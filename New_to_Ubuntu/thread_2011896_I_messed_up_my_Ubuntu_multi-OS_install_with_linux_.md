---
title: "I messed up my Ubuntu multi-OS install with linux mint and xp!"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by excitingsongs on 2012-06-28
My laptop came preloaded with xp and then I loaded linux mint 9 along with it. It was a dual-boot, then. But I loaded linux mint 11 before a few months as I wanted to work with my 3G USB modem (which works in the new version out of the box). But there is an issue with linux mint 11 in my system - The OS hangs and freezes frequently. 

So, even though I have three OS's now, I still proceeded to install Ubuntu (latest version, 12). I did it through a USB stick. I used the option of, 'Install alongside other OS' and the installation got complete. At the end of the installation it said something like, 'Ubuntu cannot be mounted, try manually' or something, but I ignored it and went back.  It completed the installation and asked me to restart.

I restarted, but I get the Grub loader of Linux Mint 11 only. I see xp, linux mint 9, linux mint 11 in that list, but ubuntu is not listed! I used partition manager to see if ubuntu was installed and it seems ubuntu is installed in /sda 12. But how do I boot from sda 12?  I want to use Ubuntu and Linux Mint 9 (too many installed applications, there). Other two OS are not important.

Please tell me how to boot from Ubuntu and use it. I don't know CLI, but I can learn now, if it's required.

---

### Post by Gone fishing on 2012-06-28
I think its time to make up your mind - start up on a live CD, remove any surplus partitions and install Ubuntu over the partitions of OSes you don't want. Making sure to back up data etc first.

---

### Post by Hendra Fuhrer on 2012-06-29
the / partition might have not been mounted . .
reinstall it using "Something Else" partitioning choice

---

