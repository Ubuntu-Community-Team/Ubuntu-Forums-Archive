---
title: "Monitor screens won't wake up after inactivity"
date: 2018-05-04
forum: New to Ubuntu
---

### Post by alecs55 on 2018-05-04
I am using Ubuntu 18.04 LTS on my desktop. When I lock the computer, or when the screens go black after inactivity, I can't wake up Ubuntu. I upgraded the graphics driver to open source, and updated the ppa, but problem persists. I have an Radeon R9 380 series. Thanks for your help!

---

### Post by ank2 on 2018-05-04
Like it's locked up and you have to reboot?

First try **CTRL-ALT-F3** to get a console (no mouse support here!) and log in as root (or user and become root then with su). Type **ls -rtl /var/log** which lists the lastest modified files and directory on the bottom. See if any looks like it has to do with X. Use a viewer like *less *to open that file and see if it tells you what's wrong.

It's also possible there are log files in your user directory. So after getting a console log in as user this time. Then **ls -rtla**&#8203; to get a list with the lastest modified file or directory on the bottom. May be there is a log file telling you what is wrong.

---

### Post by alecs55 on 2018-05-04
Thanks for the reply. I tried the ls command, but didn't see anything with X, any others that I need to look at? Now when I reboot, the screen looks scrabbled on one of my monitors. When I type my password, then both screens lose signal, and everything goes dark. I'm stumped.

---

### Post by ank2 on 2018-05-05
> **alecs55 said:**
> Thanks for the reply. I tried the ls command, but didn't see anything with X, any others that I need to look at? Now when I reboot, the screen looks scrabbled on one of my monitors. When I type my password, then both screens lose signal, and everything goes dark. I'm stumped.
I remember I looked into /var/log/Xorg. But since I didn't had any problems for years I never looked there again to realize it is gone. Might have been moved to another log on a Xorg update?

Anyway I have an ~/.xsession-errors file which looks promising.

Can you still press **CTRL-ALT-F3**? If not you could try to boot it into Single User Mode. You need to interrupt the GRUB loader (hit any key before it starts booting). Press "e" to get some boot instructions. Find the line starting with "kernel". Go to the end, hit " " (space) and an "S" (without quoting marks), the F10 to boot. It will drop you into a shell after asking you for the root password. You will have no mouse and probably also no network. But you can look into log files to see what might be wrong. Suppose you have a second machine with internet access to do a web search for errors shown there and how to fix them.

My gut feeling tels me your monitor cannot cope with the resolution your graphic card provides. Or that you are missing firmware for the graphics card. If latter and you get a shell **a** have internet access start a non-graphical package manager like aptitude and search all packages for firmware, until you found a page with the name of your graphic card (often Intel, Nvidia or AMD these days) and install it. Then reboot.

---

