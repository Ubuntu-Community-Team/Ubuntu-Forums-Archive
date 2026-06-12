---
title: "I keep getting &quot;watchdog detected hard LOCKUP on cpu 0&quot; in lubuntu installer."
date: 2017-08-04
forum: New to Ubuntu
---

### Post by thatonecoderkid on 2017-08-04
I have an old laptop that I am trying to install lubuntu (alternate) version 16.04 to off of a live dvd. I get to the menu fine, but when I try to click "Install Lubuntu", or "Check Disk for defects", it just freezes for a few seconds, goes black, and then shows the message, "watchdog detected hard LOCKUP on cpu 0". I have restarted and retried many times but nothing is working. I already tried putting the computer in legacy mode and the installer in nomodeset. It has 444 MB RAM and 1.5 gigahertz intel celeron m cpu, and is running windows vista home edition. It is a gateway so that might explain some things.

---

### Post by RobGoss on 2017-08-05
Hello and welcome to the forum, Am I reading this right **444 MB ** Ram? this may be an issue as far as hardware is concerned. What are the specs for this machine?

---

### Post by vasa1 on 2017-08-05
See if [https://ubuntuforums.org/showthread.php?t=2342796](https://ubuntuforums.org/showthread.php?t=2342796) is related to your issue.

---

### Post by thatonecoderkid on 2017-08-05
It is a gateway model W340UI, with 70 gigabyte hard drive, 450 Megabytes of ddr2 ram, and 1.5 gigahertz Intel celeron m cpu

Vasa1 it is similar, but my bios menu is different (Pheonix Bios), and a lot more simple, and doesn't have that many options

---

### Post by thatonecoderkid on 2017-08-05
I am pretty new to linux and ubuntu, so any and all help is appreciated.

---

### Post by oldos2er on 2017-08-05
You might want to try 17.04 as suggested by this askubuntu thread: [https://askubuntu.com/questions/916195/ubuntu-16-04-xenial-multiple-cpu-hard-lockup/916196](https://askubuntu.com/questions/916195/ubuntu-16-04-xenial-multiple-cpu-hard-lockup/916196)

---

### Post by RobGoss on 2017-08-06
> It is a gateway model W340UI, with 70 gigabyte hard drive, 450 Megabytes of ddr2 ram, and 1.5 gigahertz Intel celeron m cpu

It seem to me that you might be having problems do to the limited amount of Ram that machine has, I'm almost certain the minimum Ram required for even a light weight version of Ubuntu is about 512 MB. I do know Ubuntu has minimal installation and you can read about it here, [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by thatonecoderkid on 2017-08-06
Problem solved, i just had to switch acpi=off on in the installer. I learned this in the mini install so thanks to RobGoss for the suggestion and I hope this solution will help other people!

---

### Post by wildmanne39 on 2017-08-06
Once installed did you reactivate acpi=off? it is not the option you want to use long term, it turns of to many things like it may turn off wifi, fans etc. I do not think it turns off as much as it use to but the preferred method if you must have a parameter set is nomodeset.

---

### Post by thatonecoderkid on 2017-08-06
how do you check if acpi is on or off after installation?

---

### Post by wildmanne39 on 2017-08-06
If you did not set it to off after you installed Ubuntu and rebooted it is on, you would not have had a reason to change the setting if it booted after installation and you would have had to go into the grub to make it permanent..

---

