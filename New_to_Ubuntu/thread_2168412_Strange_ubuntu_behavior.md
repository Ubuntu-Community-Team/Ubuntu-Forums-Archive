---
title: "Strange ubuntu behavior"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-08-17
I have an HP 2000 Notebook PC, and I decided to install Ubuntu 13.04 on a 150 GB partition I had prepared for it, dual-booting with Windows 8 (on a 350 GB partition).

Ubuntu was fast, fluid, and very user-friendly :). No problems whatsoever. That lasted a couple of weeks.

That doomsday, when everything began, I was installing a program called gnome-system-tools, so that I could use the program (that previously came with ubuntu) called "Users and groups" (the now-standard "User accounts" doesn't have as many features). I used it to move the home folder of another user I created to another place. Thats when everything started.

[HR][/HR]
I switched to the user to test it to see if it worked. Unfortunately, I got a blank screen, then followed by the lightdm login screen :confused:. Once again, I chose the user,and it failed again, presenting me with the login screen (again). I switched back to my "real user", to check to see what was wrong. every attempt to fix it failed. So I decided to work on it again the next day...

That day I decided to revert to the previous home folder, and I got a message saying I had 0 GB of space left, which was strange because I didn't have too much software installed (except the KDE desktop package). I decided to clean up some space (only 5 GB could be cleaned). After the clean, I tried to uninstall some software, which failed because dpkg says there is no space left.

The main question is, what happened??? Will it happen again if I reinstall ubuntu???

---

### Post by Jonathan Precise on 2013-08-18
Restarting (strangely) fixed the problem:KS... The gnome-system-monitor says only 5% of the partition is used:confused:...

May this happen again??

---

### Post by Jonathan Precise on 2013-09-12
It happened again :shock:. I noticed it was a short while after compiz crashed. Rebooting strangely fixed it. Again.
Now up and running again, I see only 7% is used.

What is happening?

---

