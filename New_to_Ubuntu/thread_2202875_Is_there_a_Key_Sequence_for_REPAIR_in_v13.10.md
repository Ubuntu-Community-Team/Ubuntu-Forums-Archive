---
title: "Is there a Key Sequence for REPAIR in v13.10"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by Rick St. George on 2014-01-31
How Do I Recover from Bad Video Driver installed in v13.10

After download and install of FGLRX for my dual monitor Card (Radeon 7000) upon reboot my screen comes up with blue lines and NO Login. Is there a key sequence to bring up a previous OS install, or Repair, etc.?

I tried to use my Xubuntu CD to Re-install the entire OS ... But No Luck. It may be my DVD drive as it seems to wobble, and all I see is a rotating "worm" under XUBUNTU.

Any suggestions?
Thanks!
RSG

---

### Post by deadflowr on 2014-01-31
You should be able to get a console prompt by running
ctrl+alt+F1(or F2,F3)
when you do, login as usual and try this
```
sudo apt-get remove --purge fglrx fglrx-amdcccle
```
this should remove the driver and reset the old one(I think)
look here for more, and probably better advice.
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by Rick St. George on 2014-01-31
No Go ...  All I see is a Black Screen with Blue vertical lines and a blinking cursor near the upper left part of the screen. The blinking cursor has nothing in front of it. I do notice before this screen comes up, one line of text, at the top on a black screen, but it is so quick I can't read it.

The only thing the computer responds to is Ctrl-Alt-Del and reboots.

Puzzling Indeed ! ! !

Would the commands you mention in your post work in a terminal window while I'm running BOOT REPAIR? Tried Boot Repair but get the same thing on Reboot. But I can get a terminal window, and see the contents of the HD while running the Boot Repair CD.  Hmmmm ? ? ?

---

### Post by deadflowr on 2014-01-31
> [COLOR=#000000]Would the commands you mention in your post work in a terminal window while I'm running BOOT REPAIR?[/COLOR]

Do you mean a livecd?

You'd have to mount the partition and then chroot into it.
This will give you some idea of what I mean
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

But, it should work to run the commands.
Though, if you're having problems accessing the system with 
ctrl-alt=F#
then something else might be troubling.

---

### Post by Rick St. George on 2014-01-31
Was able to chroot over to Root, but Errors were encountered while processing: fglrx
E: sub-process /usr/bin/dpkg returned an error code (1)

And I saw a lot of permission denied !!!

Here is the Boot Summary Report from BOOT REPAIR Disk. Posted at;
[http://paste.ubuntu.com/6852700/](http://paste.ubuntu.com/6852700/)

If that helps!
I'm at a loss. Thanks for any help ! ! !

---

### Post by deadflowr on 2014-01-31
Can you access the grub menu when you boot up?
If you can try entering recovery mode
This is about resetting a password, but the pictures explain what I mean well enough
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Rick St. George on 2014-01-31
No - thats the problem, it just goes to the Black Screen with Blue vertical lines.

Guess I will replace my DVD drive and try Re-installing. Funny, the Boot Repair Disk boots up, but the Xubuntu Install Disk does not. Thanks for your Help.

---

### Post by Rick St. George on 2014-02-03
Unbelievable - I replaced the DVD drive with another DVD drive and ....
Same thing. Boot Repair CD would run even though boot repair failed to solve the problem.
Xubuntu v13.10 i386 would not install. Tried downloading onto a +R DVD as the other one was -R.
No difference, the screen on both disks would display,

Boot from CD:
Missing Operating System
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER.

And no it is not a 64bit machine. Its an older one but has about 2.5 Ghz CPU, 1 GB Ram.

Any suggestions?
Thanks!

---

### Post by Bashing-om on 2014-02-03
Rick St. George; Hi !

Maybe try booting with "nomodeset" option as that disables Kernel Mode Setting ??
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by Rick St. George on 2014-02-11
Solved - ONLY due to the Fact I had to Wipe the HD and Re-Install an older version of Xubuntu.
I had 3 different disks with v13.10, and NONE of them would Boot. It wasn't until I went back
and found an older version, v12.04 that booted up and allowed me to install. Then it was just
a matter of upgrading online.

Don't know why the Xubuntu v13.10 disks would not boot. Anyone else experienced that?
Downloaded them from [www.Xubuntu.org](www.Xubuntu.org) 

Thanks for your help!
Rick

---

