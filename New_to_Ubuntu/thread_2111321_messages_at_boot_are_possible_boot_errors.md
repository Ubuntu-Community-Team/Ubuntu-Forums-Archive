---
title: "messages at boot are possible boot errors?"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by makeparts on 2013-02-01
I recently ran an update on my v12.04 release, and at boot it is flashing messages (seems like some might be errors), but it is happening so fast I cannot be sure if it is anything I need to address

I looked at /var/log/boot.log, but I'm not sure what it is telling me (boot.log pasted below)...is there anything else I should do to check the system?

I figure its worth exploring as I want to learn how things work...

here's the boot log:

fsck from util-linux 2.20.1
/dev/sda5: clean, 273058/14458880 files, 2550529/57818368 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting mDNS/DNS-SD daemonESC[74G[ OK ]
 * Starting AppArmor profiles       ESC[80G ^MESC[74G[ OK ]
 * Starting Userspace bootsplashESC[74G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned
 * Stopping System V initialisation compatibilityESC[74G[ OK ]
 * Starting System V runlevel compatibilityESC[74G[ OK ]
 * Starting automatic crash report generationESC[74G[ OK ]
 * Starting LightDM Display ManagerESC[74G[ OK ]
 * Starting save kernel messagesESC[74G[ OK ]
 * Starting anac(h)ronistic cronESC[74G[ OK ]
 * Starting ACPI daemonESC[74G[ OK ]
 * Starting CPU interrupts balancing daemonESC[74G[ OK ]
 * Starting crash report submission daemonESC[74G[ OK ]
 * Starting regular background program processing daemonESC[74G[ OK ]
 * Starting deferred execution schedulerESC[74G[ OK ]
 * Stopping Userspace bootsplashESC[74G[ OK ]
 * Stopping save kernel messagesESC[74G[ OK ]
 * Stopping cold plug devicesESC[74G[ OK ]
 * Stopping log initial device creationESC[74G[ OK ]
 * Starting configure network device securityESC[74G[ OK ]
 * Starting save udev log and update rulesESC[74G[ OK ]
 * Starting configure virtual network devicesESC[74G[ OK ]
 * Stopping save udev log and update rulesESC[74G[ OK ]
 * Stopping configure virtual network devicesESC[74G[ OK ]
(END)

thanks in advance folks

---

### Post by CharlesA on 2013-02-01
Looks fine to me.

---

