---
title: "ubuntu 10.04 no login screen right to desktop"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by klein de usa on 2012-11-16
i'v ran across a problem i haven't seen before, i just reinstalled 10.04 64bit on an hp, and i can't get the login screen to come up it goes right to desktop. (computer is fully up dated )

i'v tried the setting not to have a login screen and rebooted, then set it back to have a login screen. and still no login screen. 

i have created a second user and still no login screen when the computer boots up.

is there something else i can try?

---

### Post by ibjsb4 on 2012-11-16
When you say that you change the settings.  Is that /etc/init/gdm.conf ?

And what happens with:
[FONT=monospace]
[/FONT]sudo dpkg-reconfigure gdm

---

### Post by klein de usa on 2012-11-16
no i was doing it through system > administration > users and groups 

since you said it i looked at /etc/init/gdm.conf but did not see any clear way to change or reference to the login screen.

i ran  sudo dpkg-reconfigure gdm from terminal and it returned my prompt without any problems but i have the same problem boots right to desktop.

---

### Post by klein de usa on 2012-11-16
one thing i forgot was there is message that flashes when it is booting 

(   13.480591)(drm:rs400_gart_adjust_size) *error* force to 32m gart size (because of asci bug ?)

i don't think when i googled it it had anything to do with the login screen

---

### Post by grandsatrap on 2013-02-12
Go to this webpage: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843)   and read comments #34 and 35.

Basically they say to do this: 


in /etc/default/grub

add radeon.modeset=0 to GRUB_CMDLINE_LINUX_DEFAULT

then sudo update-grub

---

