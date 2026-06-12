---
title: "System Error Detected - Why on Ubuntu 12.04 Boot?"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by afz12 on 2012-05-20
I often get a "system error detected" error message when I boot Ubuntu 12.04. It then asks me to send info for debugging but this never works. However the message clicks off usually but it is  a nuisance. How do I either get rid of the message or find a "fix" for whatever the error is?

I made a recent fresh install of Ubuntu and have all updates installed.

---

### Post by rajivrnair on 2012-05-21
Take a look at the contents of /var/log/boot.log and /var/log/dmesg. These are where the boot logs are written. They'll tell you the real issue.

---

### Post by mlentink on 2012-05-21
Please be aware that it can take a while for apport to gather all the info it needs. You can opt to be shown the pertinent data if you wish. You can also opt not to receive messages about this issue again.
With the upgrade to Precise I got a recurring error at start-up on the bluetooth-stack, which I have now opted to ignore. But please end bug reports, as your issue might never get solved if you don't.

---

### Post by afz12 on 2012-05-21
Thanks for the suggestions. I looked at boot.log and dmesg. but didn't see anything that looked like an error. I any case script details are as good as gobbledegook to me. (Hence posting to beginners - computer syntax seems artificial compared to science/math descriptors I guess). Anyway the contents of boot.log are below if this provides any clue - also I have clicked not to receive the errors but these "opts" don't seem to be effective on 12.04. Also I've not seen this behaviour on previous Ubuntu versions.

fsck from util-linux 2.20.1
/dev/sda1: clean, 260145/30146560 files, 39867309/120575232 blocks
modem-manager[844]: <info>  ModemManager (version 0.5.2.0) starting...


modem-manager[844]: <info>  Loaded plugin Samsung


modem-manager[844]: <info>  Loaded plugin Wavecom


modem-manager[844]: <info>  Loaded plugin SimTech


modem-manager[844]: <info>  Loaded plugin X22X


modem-manager[844]: <info>  Loaded plugin Huawei


modem-manager[844]: <info>  Loaded plugin Longcheer


modem-manager[844]: <info>  Loaded plugin Option


modem-manager[844]: <info>  Loaded plugin AnyData


modem-manager[844]: <info>  Loaded plugin Novatel


modem-manager[844]: <info>  Loaded plugin ZTE


modem-manager[844]: <info>  Loaded plugin Gobi


modem-manager[844]: <info>  Loaded plugin Option High-Speed


modem-manager[844]: <info>  Loaded plugin Sierra


modem-manager[844]: <info>  Loaded plugin Linktop


modem-manager[844]: <info>  Loaded plugin Nokia


modem-manager[844]: <info>  Loaded plugin Ericsson MBM


modem-manager[844]: <info>  Loaded plugin MotoC


modem-manager[844]: <info>  Loaded plugin Generic


Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [80G 
[74G[ OK ]
 * Stopping restore software rfkill state[74G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Stopping System V initialisation compatibility[74G[ OK ]
 * Starting System V runlevel compatibility[74G[ OK ]
 * Starting automatic crash report generation[74G[ OK ]
 * Starting ACPI daemon[74G[ OK ]
 * Starting anac(h)ronistic cron[74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
 * Starting crash report submission daemon[74G[ OK ]
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting deferred execution scheduler[74G[ OK ]
 * Stopping save kernel messages[74G[ OK ]
 * Stopping anac(h)ronistic cron[74G[ OK ]
 * Starting VirtualBox kernel modules       [80G 
[74G[ OK ]
 * Starting Userspace bootsplash[74G[ OK ]
 * Starting LightDM Display Manager[74G[ OK ]
 * Stopping cold plug devices[74G[ OK ]
 * Stopping log initial device creation[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting save udev log and update rules[74G[ OK ]
 * Starting configure virtual network devices[74G[ OK ]
 * Stopping configure virtual network devices[74G[ OK ]
 * Stopping save udev log and update rules[74G[ OK ]
 * Stopping Userspace bootsplash[74G[ OK ]
 * Starting the Winbind daemon winbind       [170G 
[164G[ OK ]
saned disabled; edit /etc/default/saned

---

