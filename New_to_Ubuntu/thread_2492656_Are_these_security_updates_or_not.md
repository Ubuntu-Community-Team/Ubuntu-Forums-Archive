---
title: "Are these security updates or not ?"
date: 2023-11-19
forum: New to Ubuntu
---

### Post by maketopsite on 2023-11-19
After applying all security updates in [FONT=courier new]update-manager[/FONT]:

```
# unattended-upgrade -v
Starting unattended upgrades script
Allowed origins are: o=Ubuntu,a=jammy, o=Ubuntu,a=jammy-security, o=UbuntuESMApps,a=jammy-apps-security, o=UbuntuESM,a=jammy-infra-security
Initial blacklist: 
Initial whitelist (not strict): 
Packages that will be upgraded: ffmpeg libavcodec-dev libavcodec58 libavdevice58 libavfilter7 libavformat-dev libavformat58 libavutil-dev libavutil56 libpostproc55 libswresample-dev libswresample3 libswscale-dev libswscale5
Writing dpkg log to /var/log/unattended-upgrades/unattended-upgrades-dpkg.log
...

```

Are please these security updates or not ?
Ubuntu 22.04

---

### Post by ian-weisser on 2023-11-19
Show us your apt logs (/var/log/apt/history.log and /var/log/apt/term.log) for both the update-manager session and the unattended-upgrades session.

---

### Post by maketopsite on 2023-11-20
/var/log/apt/history.log
```

Start-Date: 2023-11-19  08:32:25
Commandline: aptdaemon role='role-commit-packages' sender=':1.74'
Upgrade: libprocps8:amd64 (2:3.3.17-6ubuntu2, 2:3.3.17-6ubuntu2.1), procps:amd64 (2:3.3.17-6ubuntu2, 2:3.3.17-6ubuntu2.1), intel-microcode:amd64 (3.20230808.0ubuntu0.22.04.1, 3.20231114.0ubuntu0.22.04.1)
End-Date: 2023-11-19  08:33:26

Start-Date: 2023-11-19  08:35:02
Commandline: aptdaemon role='role-commit-packages' sender=':1.74'
Upgrade: apt:amd64 (2.4.10, 2.4.11), libapt-pkg6.0:amd64 (2.4.10, 2.4.11), brave-browser:amd64 (1.60.114, 1.60.118), apt-utils:amd64 (2.4.10, 2.4.11)
End-Date: 2023-11-19  08:35:26

```

```

Start-Date: 2023-11-19  08:41:01
Commandline: /usr/bin/unattended-upgrade -v
Requested-By: maketopsite (1000)
Upgrade: libavdevice58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), ffmpeg:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libpostproc55:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libswscale-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libavcodec58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libavutil56:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libswscale5:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libavutil-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libswresample3:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libavformat58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libavformat-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libavcodec-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libswresample-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3), libavfilter7:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm2, 7:4.4.2-0ubuntu0.22.04.1+esm3)
End-Date: 2023-11-19  08:41:27

```




/var/log/apt/term.log
```

Log started: 2023-11-19  08:32:25
(Reading the database... 
(Reading the database... 5%
(Reading the database... 10%
(Reading the database... 15%
(Reading the database... 20%
(Reading the database... 25%
(Reading the database... 30%
(Reading the database... 35%
(Reading the database... 40%
(Reading the database... 45%
(Reading the database... 50%
(Reading the database... 55%
(Reading the database... 60%
(Reading the database... 65%
(Reading the database... 70%
(Reading the database... 75%
(Reading the database... 80%
(Reading the database... 85%
(Reading the database... 90%
(Reading the database... 95%
(Reading the database... 100%
(Read database... 601029 files and directories already installed.)
Preparing to unpack .../libprocps8_2%3a3.3.17-6ubuntu2.1_amd64.deb ...
Unpacking libprocps8:amd64 (2:3.3.17-6ubuntu2.1) from (2:3.3.17-6ubuntu2) ...
Preparing to troubleshoot .../procps_2%3a3.3.17-6ubuntu2.1_amd64.deb ...
Unpacking procps (2:3.3.17-6ubuntu2.1) on (2:3.3.17-6ubuntu2) ...
Preparing to troubleshoot .../intel-microcode_3.20231114.0ubuntu0.22.04.1_amd64.deb ...
Troubleshooting intel-microcode (3.20231114.0ubuntu0.22.04.1) on (3.20230808.0ubuntu0.22.04.1) ...
Configuration of intel-microcode (3.20231114.0ubuntu0.22.04.1) ...
update-initramfs: deferring update (trigger activated)
intel-microcode: microcode will be updated at next boot
Setting libprocps8:amd64 (2:3.3.17-6ubuntu2.1) ...
Setting procps (2:3.3.17-6ubuntu2.1) ...
Processing of delayed actions («triggers») for libc-bin (2.35-0ubuntu3.4) ...
Processing of delayed actions («triggers») for man-db (2.10.2-1) ...
Processing of delayed actions («triggers») for menu (2.1.47ubuntu4) ...
Processing of delayed actions («triggers») for initramfs-tools (0.140ubuntu13.4)
update-initramfs: Generating /boot/initrd.img-5.15.0-88-generic 
Log ended: 2023-11-19  08:33:26

Log started: 2023-11-19  08:35:02
(Reading the database... 
(Reading the database... 5%
(Reading the database... 10%
(Reading the database... 15%
(Reading the database... 20%
(Reading the database... 25%
(Reading the database... 30%
(Reading the database... 35%
(Reading the database... 40%
(Reading the database... 45%
(Reading the database... 50%
(Reading the database... 55%
(Reading the database... 60%
(Reading the database... 65%
(Reading the database... 70%
(Reading the database... 75%
(Reading the database... 80%
(Reading the database... 85%
(Reading the database... 90%
(Reading the database... 95%
(Reading the database... 100%
(Read database... 601029 files and directories already installed.)
Preparing to unpack .../libapt-pkg6.0_2.4.11_amd64.deb ...
Unpacking libapt-pkg6.0:amd64 (2.4.11) on (2.4.10) ...
Setting libapt-pkg6.0:amd64 (2.4.11) ...
(Reading the database... 
(Reading the database... 5%
(Reading the database... 10%
(Reading the database... 15%
(Reading the database... 20%
(Reading the database... 25%
(Reading the database... 30%
(Reading the database... 35%
(Reading the database... 40%
(Reading the database... 45%
(Reading the database... 50%
(Reading the database... 55%
(Reading the database... 60%
(Reading the database... 65%
(Reading the database... 70%
(Reading the database... 75%
(Reading the database... 80%
(Reading the database... 85%
(Reading the database... 90%
(Reading the database... 95%
(Reading the database... 100%
(Read database... 601029 files and directories already installed.)
Preparing to unpack .../archives/apt_2.4.11_amd64.deb ...Unpacking apt (2.4.11) on (2.4.10) ... 
Setting up apt (2.4.11) ...
(Reading the database... 
(Reading the database... 5%
(Reading the database... 10%
(Reading the database... 15%
(Reading the database... 20%
(Reading the database... 25%
(Reading the database... 30%
(Reading the database... 35%
(Reading the database... 40%
(Reading the database... 45%
(Reading the database... 50%
(Reading the database... 55%
(Reading the database... 60%
(Reading the database... 65%
(Reading the database... 70%
(Reading the database... 75%
(Reading the database... 80%
(Reading the database... 85%
(Reading the database... 90%
(Reading the database... 95%
(Reading the database... 100%
(Read database... 601027 files and directories already installed.)
Preparing to unpack .../apt-utils_2.4.11_amd64.deb ...
Unpacking apt-utils (2.4.11) on (2.4.10) ...
Preparing to unpack .../brave-browser_1.60.118_amd64.deb ...
Troubleshooting brave-browser (1.60.118) on (1.60.114) ...
Setting up apt-utils (2.4.11) ...
brave-browser settings (1.60.118) ...
Processing of delayed actions («triggers») for mailcap (3.70+nmu1ubuntu1) ...
Processing of delayed actions («triggers») for desktop-file-utils (0.26-1ubuntu3) ...
Processing of delayed actions («triggers») for gnome-menus (3.36.0-1ubuntu3) ...
Processing of delayed actions («triggers») for mate-menus (1.26.0-2ubuntu2) ...
Processing of delayed actions («triggers») for libc-bin (2.35-0ubuntu3.4) ...
Processing of delayed actions («triggers») for man-db (2.10.2-1) ...
Processing of delayed actions («triggers») for menu (2.1.47ubuntu4) ...
Log ended: 2023-11-19  08:35:26

```


```

Log started: 2023-11-19  08:41:01
(Reading the database... 
(Reading the database... 5%
(Reading the database... 10%
(Reading the database... 15%
(Reading the database... 20%
(Reading the database... 25%
(Reading the database... 30%
(Reading the database... 35%
(Reading the database... 40%
(Reading the database... 45%
(Reading the database... 50%
(Reading the database... 55%
(Reading the database... 60%
(Reading the database... 65%
(Reading the database... 70%
(Reading the database... 75%
(Reading the database... 80%
(Reading the database... 85%
(Reading the database... 90%
(Reading the database... 95%
(Reading the database... 100%
(Read database... 601027 files and directories already installed.)
Preparing to unpack .../00-libavformat-dev_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libavformat-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../01-libavcodec-dev_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libavcodec-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../02-libswresample-dev_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libswresample-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to troubleshoot .../03-ffmpeg_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking ffmpeg (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../04-libavdevice58_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libavdevice58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../05-libavfilter7_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libavfilter7:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../06-libavformat58_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libavformat58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../07-libavcodec58_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libavcodec58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../08-libswresample3_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libswresample3:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../09-libpostproc55_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libpostproc55:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../10-libswscale-dev_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libswscale-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../11-libswscale5_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libswscale5:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../12-libavutil-dev_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libavutil-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Preparing to unpack .../13-libavutil56_7%3a4.4.2-0ubuntu0.22.04.1+esm3_amd64.deb ...
Unpacking libavutil56:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) on (7:4.4.2-0ubuntu0.22.04.1+esm2) ...
Setting libavutil56:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libpostproc55:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libswscale5:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libavutil-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libswresample3:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libswscale-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libavcodec58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libswresample-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libavformat58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libavcodec-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libavformat-dev:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libavfilter7:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting libavdevice58:amd64 (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Setting ffmpeg (7:4.4.2-0ubuntu0.22.04.1+esm3) ...
Processing of delayed actions («triggers») for man-db (2.10.2-1) ...
Processing of delayed actions («triggers») for libc-bin (2.35-0ubuntu3.4) ...
Log ended: 2023-11-19  08:41:27

```

---

### Post by ian-weisser on 2023-11-20
> **maketopsite said:**
> Are please these security updates or not ?

Yes, they do seem to be security updates.

---

### Post by maketopsite on 2023-11-24
> **ian-weisser said:**
> Yes, they do seem to be security updates.

Thank you.

---

