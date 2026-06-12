---
title: "Ubuntu 16.04 LTS update problem; can't reach login screen after reboot"
date: 2016-08-08
forum: New to Ubuntu
---

### Post by degabged on 2016-08-08
I've been using a dual-boot system with Windows 10 and Ubuntu 14.04, and decided to upgrade Ubuntu to 16.04. After the upgrade process and reboot, I get stuck in a black screen. Pressing CTRL-ALT-F1 brings me to an Ubuntu loading screen, and pressing ESC brings me to the console screen, showing a bunch on information, some of which is shown here:

```

...
[  OK  ] Started LSB: Record successful boot for GRUB.
[  OK  ] Started LSB: automatic crash report generation.
[  OK  ] Started LSB: daemon to balance interrupts for SMP systems.
[FAILED] Failed to start Login Service.
See 'systemctl status systemd-logind.service' for details.
[FAILED] Failed to start Accounts Service.
See 'systemctl status accounts-daemon.service' for details.
[FAILED] Failed to start Modem Manager.
See 'systemctl status ModemManager.service' for details.
[FAILED] Failed to start Thermal Daemon Service.
See 'systemctl status thermald.service' for details.
[FAILED] Failed to start Bluetooth Service.
See 'systemctl status bluetooth.service' for details.
[FAILED] Failed to start Avahi mDNS/DNS-SD Stack.
See 'systemctl status avahi-daemon.service' for details.
[FAILED] Failed to start Network Manager.
See 'systemctl status NetworkManager.service' for details.
[ ***  ] A start job is running for Enable support for additional executable binary formats (49min 50s / no limit)

```

Then, the console gets stuck on that screen, just updating the time elapsed in the last line, so I can't enter the 'systemctl' commands here. I tried entering them in recovery mode's root prompt, and it just says that the services are inactive / dead. Is there anything I've missed or overlooked?
For reference, here are the specs of my computer:
i7-4790 @ 3.60 GHz
8.00 GB RAM
64-bit
NVIDIA GeForce GTX 745

While I am okay with reformatting the partition and reinstalling Ubuntu, I'd prefer a solution which doesn't require a reformat.
Thanks in advance.

---

### Post by ege-e on 2016-08-10
I already installed 16.04 but I had similar problem on my MacBook 12,1 yesterday.

I boot up in my external disk. I am on Ubuntu 16.04.1

```
[FAILED] Failed to start Login Service.
See 'systemctl status systemd-logind-service' for details.
[  OK  ] Started LSB: Record successful boot for GRUB.
[  OK  ] Started Daily apt activites.
[  OK  ] Started dnsmasq = A lightweight DHCP and caching DNS server.
[FAILED] Failed to start Accounts Service.
See 'systemctl status accounts-daemon.service' for details.
[FAILED] Failed to start Thermal Daemon Service.
See 'systemctl status thermald.service' for details.
[FAILED] Failed to start Modem Manager.
See 'systemctl status ModemManager.service' for details.
[FAILED] Failed to start IIO Sensor Proxy service.
See 'systemctl status iio-sensor-proxy.service' for details.
[FAILED] Failed to start Bluetooth service.
See 'systemctl status bluetooth.service' for details.
[FAILED] Failed to start Avahi mDNS/DNS-SD Stack.
See 'systemctl status avahi-daemon.service' for details.
[FAILED] Failed to start Network Manager.
See 'systemctl status NetworkManager.service' for details.
[DEPEND] Dependency failed for Network Manager Wait Online.
```

Then nothing happens.

---

### Post by th-heuer on 2016-09-09
sudo apt-get install systemd-sysv

# fixed the problem for me on Ubuntu 16.04.1
# I know this may be a hack but it works.

---

