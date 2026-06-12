---
title: "How to prevent program running during start up"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-14
Hello, since yesterday Pidgin, Nautilus (File browser) and FF will automatically start during booting. I already uncheck "Automatically remember running...." option in Session Preference and confirm that none of these problem appear in "Startup Programs". However, the problem still persist even after several reboots. How do I solve this problem

---

### Post by PmDematagoda on 2008-06-14
Post the output of:-
```
ls ~/.config/autostart
```

---

### Post by jspolen on 2008-06-14
You can also look if the script is still "active" in the /etc/rc3.d folder

The readme file in this folder says:

> The scripts in this directory are executed each time the system enters
this runlevel.

The scripts are all symbolic links whose targets are located in
/etc/init.d/ .

To disable a service in this runlevel, rename its script in this directory
so that the new name begins with a 'K' and a two-digit number, where the
number is the difference between the two-digit number following the 'S'
in its current name, and 100.  To re-enable the service, rename the script
back to its original name beginning with 'S'.

For a more information see /etc/init.d/README.

---

### Post by wariskampar on 2008-06-14
aznan@aznan-laptop:~$ ls ~/.config/autostart
bluetooth-applet.desktop        redhat-print-applet.desktop
evolution-alarm-notify.desktop


weird because i disable these services from "Session Preference"

---

### Post by wariskampar on 2008-06-14
depper look in rc3 file:

aznan@aznan-laptop:/etc/rc3.d$ ls
README                       S18avahi-daemon   S24dhcdbd      S98usplash
S01policykit                 S20apmd           S24hal         S99acpi-support
S05vbesave                   S20apport         S25bluetooth   S99laptop-mode
S10acpid                     S20cupsys         S25pulseaudio  S99rc.local
S10sysklogd                  S20hotkey-setup   S30gdm         S99rmnologin
S10xserver-xorg-input-wacom  S20nvidia-kernel  S89anacron
S11klogd                     S20powernowd      S89atd
S12dbus                      S20rsync          S89cron
aznan@aznan-laptop:/etc/rc3.d$ 

What should I do next

---

### Post by jspolen on 2008-06-14
Have you checked the other rc?.d folders, they may differ in according to number of files. 

It's a possibility that your scripts may be there.

---

