---
title: "Automatic Conditional File Transfers"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by wakeboardsam on 2012-10-14
My first post, hope my question comes across clear... thanks in advance... 

I want to minimize the use of my usb external hdd by only using/transferring files to it when my internal hdd hits a predetermined free space size. The question: is there a program that will monitor 24/7 and move files/folders based on preset conditions?

---

### Post by MG&amp;TL on 2012-10-14
Sure. *nix is good at this. Problem is, you'll need to do some research and figure out how to write a bash script and add it as a [Cron Job.]("https://help.ubuntu.com/community/CronHowto")

Now, I can't write this script for you (I don't know your exact configuration), but the following commands may be helpful:

*df *- Gives the amount of free space available. See *man df*
Bash's if-statement. See [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

*cp -*Copy files and folders.
[]("https://help.ubuntu.com/community/CronHowto")

---

