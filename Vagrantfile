Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.provision "file", source: "./problem_payload.tgz", destination: "/tmp/problem_payload.tgz"

  $script = <<-SCRIPT
  tar -xzf /tmp/problem_payload.tgz -C /
  systemctl stop rsyslog
  pkill -9 rsyslogd
  echo "Running rsyslogd..."
  rsyslogd -n $SYLOGD_OPTIONS
  echo "FINISHED"
  SCRIPT

  config.vm.provision "shell",
    inline: $script
end
