---
title: "Update History"
date: 2021-07-22
forum: New to Ubuntu
---

### Post by tech-jeff on 2021-07-22
Hi,

Not so good about Ubuntu so apologies if this question is easy for others. So we have an Ubuntu server 18.04 LTS and it was spun up using a container which has HUDU, it's a wiki/knowledge base program. Recently read an article about Ubuntu vulnerability, so I went ahead and enter the command:

sudo apt update

My question is, is there like a history? OS Update history and what are other available security updates I can do to patch the OS?

Thanks
tech-jeff

---

### Post by deadflowr on 2021-07-22
Update history logs are located in /var/log/apt.
If using unattended-upgrades then they also have a history in /var/log/unattended-upgrades.

Also, fwiw, sudo apt update only updates the list of available updates.
You need to run an apt upgrade or apt full-upgrade command to actually install any available updates.
Typically run
```
sudo apt update
sudo apt full-upgrade

or

sudo apt upgrade
```

The difference between  full-upgrade and upgrade is apt full-upgrade will do a complete upgrade, whereas apt upgrade might hold back updating some packages
if special circumstances require it not to do a complete upgrade.
Specifically, apt full-upgrade will remove installed packages if doing so is required to satisfy the complete upgrade.
apt upgrade will never remove packages, so it cannot satisfy the complete upgrade and will require any packages not upgradeable to be held back.
It's actually rare that an update will require the above circumstance, but it does happen.
As if any of that makes sense. I hope it does.

> what are other available security updates I can do to patch the OS?
Unless you install packages from outside of the Ubuntu ecosystem all security patches will be dealt with through apt.

---

### Post by tech-jeff on 2021-07-22
Thanks for the reply, this is what I got from the following commands:

cat /var/logs/apt/history.log



```
Start-Date: 2021-07-22  06:25:04
Commandline: /usr/bin/unattended-upgrade
Upgrade: systemd-sysv:amd64 (237-3ubuntu10.44, 237-3ubuntu10.49)
End-Date: 2021-07-22  06:25:05


Start-Date: 2021-07-22  06:25:08
Commandline: /usr/bin/unattended-upgrade
Upgrade: udev:amd64 (237-3ubuntu10.44, 237-3ubuntu10.49), libudev1:amd64 (237-3ubuntu10.44, 237-3ubuntu10.49)
End-Date: 2021-07-22  06:25:31


Start-Date: 2021-07-22  06:25:34
Commandline: /usr/bin/unattended-upgrade
Upgrade: libsystemd0:amd64 (237-3ubuntu10.44, 237-3ubuntu10.49), libpam-systemd:amd64 (237-3ubuntu10.44, 237-3ubuntu10.49), systemd:amd64 (237-3ubuntu10.44, 237-3ubuntu10.49), libnss-systemd:amd64 (237-3ubuntu10.44, 237-3ubuntu10.49)
End-Date: 2021-07-22  06:25:39


Start-Date: 2021-07-22  06:25:41
Commandline: /usr/bin/unattended-upgrade
Install: linux-headers-4.15.0-151-generic:amd64 (4.15.0-151.157, automatic), linux-modules-4.15.0-151-generic:amd64 (4.15.0-151.157, automatic), linux-image-4.15.0-151-generic:amd64 (4.15.0-151.157, automatic), linux-modules-extra-4.15.0-151-generic:amd64 (4.15.0-151.157, automatic), linux-headers-4.15.0-151:amd64 (4.15.0-151.157, automatic)
Upgrade: linux-headers-generic:amd64 (4.15.0.147.134, 4.15.0.151.139), linux-image-generic:amd64 (4.15.0.147.134, 4.15.0.151.139), linux-generic:amd64 (4.15.0.147.134, 4.15.0.151.139)
End-Date: 2021-07-22  06:26:23

```
and below are the one I got from cat /var/log/unattended-upgrades/unattended-upgrades.log

```
2021-07-01 12:39:57,605 INFO Initial blacklisted packages:
2021-07-01 12:39:57,606 INFO Initial whitelisted packages:
2021-07-01 12:39:57,606 INFO Starting unattended upgrades script
2021-07-01 12:39:57,606 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-02 06:08:15,745 INFO Initial blacklisted packages:
2021-07-02 06:08:15,746 INFO Initial whitelisted packages:
2021-07-02 06:08:15,746 INFO Starting unattended upgrades script
2021-07-02 06:08:15,747 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-02 06:08:18,974 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-02 10:26:50,112 INFO Initial blacklisted packages:
2021-07-02 10:26:50,114 INFO Initial whitelisted packages:
2021-07-02 10:26:50,114 INFO Starting unattended upgrades script
2021-07-02 10:26:50,114 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-03 06:14:10,700 INFO Initial blacklisted packages:
2021-07-03 06:14:10,703 INFO Initial whitelisted packages:
2021-07-03 06:14:10,703 INFO Starting unattended upgrades script
2021-07-03 06:14:10,704 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-03 06:14:14,921 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-03 08:33:01,197 INFO Initial blacklisted packages:
2021-07-03 08:33:01,199 INFO Initial whitelisted packages:
2021-07-03 08:33:01,199 INFO Starting unattended upgrades script
2021-07-03 08:33:01,199 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-04 06:40:52,534 INFO Initial blacklisted packages:
2021-07-04 06:40:52,534 INFO Initial whitelisted packages:
2021-07-04 06:40:52,535 INFO Starting unattended upgrades script
2021-07-04 06:40:52,535 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-04 06:40:54,950 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-04 13:20:59,542 INFO Initial blacklisted packages:
2021-07-04 13:20:59,543 INFO Initial whitelisted packages:
2021-07-04 13:20:59,543 INFO Starting unattended upgrades script
2021-07-04 13:20:59,543 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-05 00:27:58,883 INFO Initial blacklisted packages:
2021-07-05 00:27:58,884 INFO Initial whitelisted packages:
2021-07-05 00:27:58,884 INFO Starting unattended upgrades script
2021-07-05 00:27:58,884 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-05 06:20:52,631 INFO Initial blacklisted packages:
2021-07-05 06:20:52,632 INFO Initial whitelisted packages:
2021-07-05 06:20:52,632 INFO Starting unattended upgrades script
2021-07-05 06:20:52,632 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-05 06:20:55,196 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-06 04:45:59,678 INFO Initial blacklisted packages:
2021-07-06 04:45:59,679 INFO Initial whitelisted packages:
2021-07-06 04:45:59,679 INFO Starting unattended upgrades script
2021-07-06 04:45:59,679 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-06 06:36:52,638 INFO Initial blacklisted packages:
2021-07-06 06:36:52,639 INFO Initial whitelisted packages:
2021-07-06 06:36:52,639 INFO Starting unattended upgrades script
2021-07-06 06:36:52,639 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-06 06:36:55,467 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-07 04:48:23,177 INFO Initial blacklisted packages:
2021-07-07 04:48:23,183 INFO Initial whitelisted packages:
2021-07-07 04:48:23,184 INFO Starting unattended upgrades script
2021-07-07 04:48:23,185 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-07 06:42:52,601 INFO Initial blacklisted packages:
2021-07-07 06:42:52,602 INFO Initial whitelisted packages:
2021-07-07 06:42:52,602 INFO Starting unattended upgrades script
2021-07-07 06:42:52,602 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-07 06:42:55,654 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-08 04:08:00,799 INFO Initial blacklisted packages:
2021-07-08 04:08:00,800 INFO Initial whitelisted packages:
2021-07-08 04:08:00,800 INFO Starting unattended upgrades script
2021-07-08 04:08:00,800 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-08 06:55:52,668 INFO Initial blacklisted packages:
2021-07-08 06:55:52,669 INFO Initial whitelisted packages:
2021-07-08 06:55:52,669 INFO Starting unattended upgrades script
2021-07-08 06:55:52,669 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-08 06:55:55,691 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-09 06:43:52,657 INFO Initial blacklisted packages:
2021-07-09 06:43:52,658 INFO Initial whitelisted packages:
2021-07-09 06:43:52,658 INFO Starting unattended upgrades script
2021-07-09 06:43:52,659 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-09 06:43:55,650 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-09 10:00:59,454 INFO Initial blacklisted packages:
2021-07-09 10:00:59,454 INFO Initial whitelisted packages:
2021-07-09 10:00:59,455 INFO Starting unattended upgrades script
2021-07-09 10:00:59,455 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-10 01:58:59,232 INFO Initial blacklisted packages:
2021-07-10 01:58:59,233 INFO Initial whitelisted packages:
2021-07-10 01:58:59,233 INFO Starting unattended upgrades script
2021-07-10 01:58:59,233 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-10 06:41:26,390 INFO Initial blacklisted packages:
2021-07-10 06:41:26,392 INFO Initial whitelisted packages:
2021-07-10 06:41:26,392 INFO Starting unattended upgrades script
2021-07-10 06:41:26,392 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-10 06:41:29,185 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-11 06:40:52,683 INFO Initial blacklisted packages:
2021-07-11 06:40:52,684 INFO Initial whitelisted packages:
2021-07-11 06:40:52,684 INFO Starting unattended upgrades script
2021-07-11 06:40:52,685 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-11 06:40:55,558 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-11 12:10:59,166 INFO Initial blacklisted packages:
2021-07-11 12:10:59,167 INFO Initial whitelisted packages:
2021-07-11 12:10:59,167 INFO Starting unattended upgrades script
2021-07-11 12:10:59,167 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-12 03:42:58,461 INFO Initial blacklisted packages:
2021-07-12 03:42:58,463 INFO Initial whitelisted packages:
2021-07-12 03:42:58,463 INFO Starting unattended upgrades script
2021-07-12 03:42:58,463 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-12 06:48:21,144 INFO Initial blacklisted packages:
2021-07-12 06:48:21,145 INFO Initial whitelisted packages:
2021-07-12 06:48:21,145 INFO Starting unattended upgrades script
2021-07-12 06:48:21,145 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-12 06:48:23,997 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-13 01:55:58,360 INFO Initial blacklisted packages:
2021-07-13 01:55:58,361 INFO Initial whitelisted packages:
2021-07-13 01:55:58,362 INFO Starting unattended upgrades script
2021-07-13 01:55:58,362 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-13 06:58:52,634 INFO Initial blacklisted packages:
2021-07-13 06:58:52,635 INFO Initial whitelisted packages:
2021-07-13 06:58:52,635 INFO Starting unattended upgrades script
2021-07-13 06:58:52,635 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-13 06:58:55,545 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-14 04:57:58,093 INFO Initial blacklisted packages:
2021-07-14 04:57:58,094 INFO Initial whitelisted packages:
2021-07-14 04:57:58,094 INFO Starting unattended upgrades script
2021-07-14 04:57:58,095 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-14 06:04:52,892 INFO Initial blacklisted packages:
2021-07-14 06:04:52,895 INFO Initial whitelisted packages:
2021-07-14 06:04:52,895 INFO Starting unattended upgrades script
2021-07-14 06:04:52,895 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-14 06:04:56,868 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-15 06:08:26,177 INFO Initial blacklisted packages:
2021-07-15 06:08:26,183 INFO Initial whitelisted packages:
2021-07-15 06:08:26,183 INFO Starting unattended upgrades script
2021-07-15 06:08:26,183 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-15 06:20:42,312 INFO Initial blacklisted packages:
2021-07-15 06:20:42,313 INFO Initial whitelisted packages:
2021-07-15 06:20:42,314 INFO Starting unattended upgrades script
2021-07-15 06:20:42,314 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-15 06:20:45,013 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-16 06:20:42,278 INFO Initial blacklisted packages:
2021-07-16 06:20:42,279 INFO Initial whitelisted packages:
2021-07-16 06:20:42,280 INFO Starting unattended upgrades script
2021-07-16 06:20:42,280 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-16 06:20:44,978 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-16 07:29:23,984 INFO Initial blacklisted packages:
2021-07-16 07:29:23,985 INFO Initial whitelisted packages:
2021-07-16 07:29:23,985 INFO Starting unattended upgrades script
2021-07-16 07:29:23,985 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-17 06:10:54,561 INFO Initial blacklisted packages:
2021-07-17 06:10:54,562 INFO Initial whitelisted packages:
2021-07-17 06:10:54,562 INFO Starting unattended upgrades script
2021-07-17 06:10:54,562 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-17 06:10:57,766 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-17 14:07:49,235 INFO Initial blacklisted packages:
2021-07-17 14:07:49,236 INFO Initial whitelisted packages:
2021-07-17 14:07:49,236 INFO Starting unattended upgrades script
2021-07-17 14:07:49,236 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-18 06:05:27,286 INFO Initial blacklisted packages:
2021-07-18 06:05:27,287 INFO Initial whitelisted packages:
2021-07-18 06:05:27,287 INFO Starting unattended upgrades script
2021-07-18 06:05:27,287 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-18 06:05:30,714 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-18 17:52:20,218 INFO Initial blacklisted packages:
2021-07-18 17:52:20,220 INFO Initial whitelisted packages:
2021-07-18 17:52:20,221 INFO Starting unattended upgrades script
2021-07-18 17:52:20,221 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-19 06:04:13,642 INFO Initial blacklisted packages:
2021-07-19 06:04:13,643 INFO Initial whitelisted packages:
2021-07-19 06:04:13,643 INFO Starting unattended upgrades script
2021-07-19 06:04:13,644 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-19 06:04:17,330 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-19 12:14:18,907 INFO Initial blacklisted packages:
2021-07-19 12:14:18,908 INFO Initial whitelisted packages:
2021-07-19 12:14:18,908 INFO Starting unattended upgrades script
2021-07-19 12:14:18,908 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-20 01:33:19,242 INFO Initial blacklisted packages:
2021-07-20 01:33:19,244 INFO Initial whitelisted packages:
2021-07-20 01:33:19,244 INFO Starting unattended upgrades script
2021-07-20 01:33:19,244 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-20 06:44:13,532 INFO Initial blacklisted packages:
2021-07-20 06:44:13,534 INFO Initial whitelisted packages:
2021-07-20 06:44:13,534 INFO Starting unattended upgrades script
2021-07-20 06:44:13,534 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-20 06:44:16,356 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-21 06:15:13,542 INFO Initial blacklisted packages:
2021-07-21 06:15:13,543 INFO Initial whitelisted packages:
2021-07-21 06:15:13,543 INFO Starting unattended upgrades script
2021-07-21 06:15:13,543 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-21 06:15:16,358 INFO No packages found that can be upgraded unattended and no pending auto-removals
2021-07-21 08:08:21,339 INFO Initial blacklisted packages:
2021-07-21 08:08:21,340 INFO Initial whitelisted packages:
2021-07-21 08:08:21,340 INFO Starting unattended upgrades script
2021-07-21 08:08:21,340 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-22 06:24:54,385 INFO Initial blacklisted packages:
2021-07-22 06:24:54,386 INFO Initial whitelisted packages:
2021-07-22 06:24:54,386 INFO Starting unattended upgrades script
2021-07-22 06:24:54,386 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
2021-07-22 06:24:59,763 INFO Packages that will be upgraded: libnss-systemd libpam-systemd libsystemd0 libudev1 linux-generic linux-headers-generic linux-image-generic systemd systemd-sysv udev
2021-07-22 06:24:59,763 INFO Writing dpkg log to /var/log/unattended-upgrades/unattended-upgrades-dpkg.log
2021-07-22 06:26:25,144 INFO All upgrades installed
2021-07-22 08:50:37,742 INFO Initial blacklisted packages:
2021-07-22 08:50:37,743 INFO Initial whitelisted packages:
2021-07-22 08:50:37,743 INFO Starting unattended upgrades script
2021-07-22 08:50:37,744 INFO Allowed origins are: o=Ubuntu,a=bionic, o=Ubuntu,a=bionic-security, o=UbuntuESMApps,a=bionic-apps-security, o=UbuntuESM,a=bionic-infra-security
```

---

### Post by ajgreeny on 2021-07-22
I use ***alias upgrade='grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log'*** in my long list of aliases which shows the most recent packages that have been upgraded and are showing in those two log files, **dpkg.log.1** and **dpkg.log**.

You can, if you wish, look even further back by using **zgrep** on all the compressed dpkg logs as well with command ***zgrep -i upgrade /var/log/dpkg.log****

---

### Post by deadflowr on 2021-07-22
You have unattended-upgrades enabled and the default settings for it is to install security updates.
So you have all available security patches by Ubuntu for your system already installed.
Also, because the security updates have installed a new linux kernel, you need to reboot in order for the new updates to be [s]used[/s] fully applied.

---

### Post by tech-jeff on 2021-07-22
Thanks and really appreciate the help. You guys respond faster than the HUDU vendor, lol

Ok, I guess I just need a reboot tonight for those patches to take effect. 

Have a good one for all members and needs more time to study Ubuntu

---

### Post by grahammechanical on 2021-07-22
You might be interested in the Ubuntu Livepatch service.

[https://ubuntu.com/security/livepatch](https://ubuntu.com/security/livepatch)

It is free for personal use on 3 machines. Linux kernel fixes are applied automatically without restarting your system. 

Regards

---

### Post by tech-jeff on 2021-07-22
Thanks for the info

---

