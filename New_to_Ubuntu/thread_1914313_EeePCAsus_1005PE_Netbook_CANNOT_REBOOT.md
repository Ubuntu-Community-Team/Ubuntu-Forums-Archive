---
title: "EeePCAsus 1005PE Netbook CANNOT REBOOT"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by ian19jam on 2012-01-24
I have an EeePC Asus Netbook using Ubuntu 11.04 and it froze up on the screen. I tried to come out of the files that I was using but the cursor would not move. S o I switched off and paused. The Tried switiching on again and the screen comes up with the following:

Target file systemdoesn't have requested/S bin/init
No init found try passing unit= bootary 

Busybox v 1. 15.3 5ubuntu 1.1.15.3-1ubuntu5) built in shell cash 
Enter 'help' for a listof built in commands

(intitramfs)-

I tried using help but it is all gobbley dook and nothing makes sense

I am very amateur with computers please can somebody advise as to how I can boot into my Netbook again in simple Computer terms please?:

Many thanks

---

### Post by evilsoup on 2012-01-24
OK, you'll need a live CD (well, a live USB stick in your case, since you are using a netbook); that is the USB (or CD) that you installed Ubuntu with in the first place. If it was installed for you by someone else and you don't have the USB stick, or you've since overwritten the USB stick, you'll first need to follow the instructions on [this page]("http://www.ubuntu.com/download/ubuntu/download") to create a new live USB.

Boot from the live USB. You do this by plugging the USB in before turning on the netbook, and then turning it on. After this, follow the instructions from [this blog post]("http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html").

For step 2, to open a teminal, you'll need to press 'ctrl+alt+t'. When you come to the final step: to boot up normally, remember to remove the USB stick before turning the computer on ;)

(NOTE: I haven't tried this fix, but it looks legit to me.)

---

