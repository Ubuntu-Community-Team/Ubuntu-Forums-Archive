---
title: "Ubuntu 16.04 freezing again!"
date: 2017-05-17
forum: New to Ubuntu
---

### Post by clive12 on 2017-05-17
Apologies for posting on familiar topic but I have looked for solutions on Ubuntu freezing but none seemed to help.

I have installed Ubuntu 16.04 64 bit desktop version on an HP laptop where it runs with no problems. As it worked so well I installed it on my desktop. The two PCs have similar specification 1.9GB memory, Intel two core processor running at about 2.5GHz, installation was to a complete disk ie not dual boot, with adequate size. The laptop had about 1.9GB swap memory which usually seemed about 60% full. The HP laptop uses its own graphics driver with GM45 express graphics chipset while the desktop uses the Ubuntu default drivers.

The desktop installation gave problems from the start with frequent lockups with no mouse and limited KB access and the need for hard reboot. I did memory checks from the Ubuntu boot screen, tested the disk drives which were initially a 120GB SSD but then a 500GB HDD, did a fresh download of 16.04 and then updated to 16.09. Also tried different drivers from Software & Updates - Additional Drivers, results were bad. Overall the the fault remained the same.

I was able to load various applications perhaps 10 - 12 times before the lockup happened. On reboot there were always a number of orphaned inodes reported and cleared. I captured some output from the syslog as below:

13:28:45 clive-GA-73PVM-S2H org.freedesktop.fwupd[809]: (fwupd:1628): Fu-WARNING **: Failed to coldplug: UEFI firmware updating not supported

May 15 13:28:45 clive-GA-73PVM-S2H dbus[809]: [system] Successfully activated service 'org.freedesktop.fwupd'

May 15 13:28:45 clive-GA-73PVM-S2H colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1

May 15 13:28:48 clive-GA-73PVM-S2H systemd-timesyncd[366]: Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com).

May 15 13:29:01 clive-GA-73PVM-S2H gnome-session[1353]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

May 15 13:29:03 clive-GA-73PVM-S2H org.gnome.zeitgeist.Engine[1216]: ** (zeitgeist-datahub:1733): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

May 15 13:29:04 clive-GA-73PVM-S2H pulseaudio[1426]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: 
org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out

May 15 13:29:15 clive-GA-73PVM-S2H systemd[1]: Starting Stop ureadahead data collection...

May 15 13:29:15 clive-GA-73PVM-S2H systemd[1]: Stopped Read required files in advance.

May 15 13:29:15 clive-GA-73PVM-S2H systemd[1]: Started Stop ureadahead data collection.

May 15 13:30:36 clive-GA-73PVM-S2H kernel: [  154.392240] nouveau 0000:00:10.0: bus: MMIO write of 07af0001 FAULT at 00b020

May 15 13:30:36 clive-GA-73PVM-S2H kernel: [  154.432311] nouveau 0000:00:10.0: bus: MMIO write of 00000000 FAULT at 00b020

There was no more output as the system locked. The MMIO write of xxx FAULT at 00b020 often occurred when opening an application.

What is going wrong?

---

### Post by ajgreeny on 2017-05-17
> The HP laptop uses its own graphics driver with GM45 express graphics chipset while the desktop uses the Ubuntu default drivers.
This quote does not really help us much as you do not say what graphics hardware the desktop machine has.
> The desktop installation gave problems from the start with frequent lockups with no mouse and limited KB access and the need for hard reboot. I did memory checks from the Ubuntu boot screen, tested the disk drives which were initially a 120GB SSD but then a 500GB HDD, did a fresh download of 16.04 and then updated to 16.09. Also tried different drivers from Software & Updates - Additional Drivers, results were bad. Overall the the fault remained the same.
Tell us a lot more about the bad results from Additional Drivers please; which versions did you try? this along with the graphics hardware may help us to help you.

---

### Post by Geoffrey_Arndt on 2017-05-17
Please also submit a link to a screenshot of your hard disk(s) layout using gparted.   (imgur is an easy repo for such graphics).

Also, a report from a hardware capture app such as "neofetch" or "inxi".     Need to install both.    For the inxi report - - open a Terminal window (ctrl+alt+t) and input "inxi -Fx" (without the quotes).

---

### Post by clive12 on 2017-05-19
Thanks for suggestions. I have attached screen shots as suggested from Gparted, inxi -Fi and neofetch.

I am using X. Org X Server Nouveau driver, I tried NVIDIA 304 legacy driver 304.135 which resulted in almost totally black screen and so I then did a reload of 16.04. I tried Processor microcode firmware for Intel but this did not appear to affect the freezing problem. I updated to 16.09 but then incorrectly loaded updates listed in Software & Updates this resulted in not being able to boot system!

---

### Post by Geoffrey_Arndt on 2017-05-20
Might want to read this from "AskUbuntu" and give it a try:

[https://askubuntu.com/questions/736854/nvidia-geforce-7100-gs-drivers-on-ubuntu-14-04](https://askubuntu.com/questions/736854/nvidia-geforce-7100-gs-drivers-on-ubuntu-14-04)

---

