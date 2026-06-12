---
title: "Stuck while booting"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by Singerlcd on 2011-09-09
Help please!  I have Ubuntu 10.04 Lucid Lynx. I have been using it for several months and it has worked just fine. Today I tried to boot up and I get and a message Killed and then
mount: mounting /dev on/root/dev failed: No such fine or directory
mount: mounting /sys on /roots/sys failed: No such file or directory
mount: mounting /proc on / root /proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
 
BusyBox    v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shel (ash)
Enter 'help' for a list of built-in commands.
 
I entered 'help' and it gives a list of commands and I have tried several of them and the computer doesn't recognize any of them.
 
I don't know where to go from here. It is stuck at this  point. Can anyone help?
 
Thank you 
Singerlcd

---

### Post by mmsmc on 2011-09-09
are you able to re-install at all? or is it vital that this is recovered

---

### Post by coffeecat on 2011-09-09
Boot up with a live Ubuntu CD or live USB and choose "try Ubuntu" to get you to the live desktop. Open Gparted which you will find in System > Administration if you are using the 10.04 version. Right-click on your Ubuntu partition in the Gparted window and choose "check". That will do a filesystem check and, hopefully, repair any damage if there is any.

If that doesn't solve the problem, boot up with the live CD again and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. That will give us an overview of your system and may have some helpful information.

While you are in the live session, open Disk Utility (it is somewhere in the System menu). Highlight your internal drive in the left pane and then see if SMART status is supported in the right-pane. Wait a few seconds - supported disks are sometimes reported as unsupported until Disk Utility has finished gathering information. What does it say under SMART status? Run a self-test. This is important. You need to exclude a failing hard drive when confronted by an unexpected error like this.

---

### Post by audiomick on 2011-09-09
Coffecat's advice is, as always, very good. You should follow it. As well as that, if it is a desktop, just have a look and make sure the cables  to the drive are seated properly. The error messages indicate that the computer can't find the drive at boot up. I have had seen badly seated cables as a cause for this several times. Also, it pays to exclude the simple causes as possibilities before going on to the complicated ones... ;)

---

