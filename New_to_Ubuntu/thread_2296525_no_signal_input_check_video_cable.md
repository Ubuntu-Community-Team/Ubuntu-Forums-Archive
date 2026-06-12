---
title: "no signal input check video cable"
date: 2015-09-26
forum: New to Ubuntu
---

### Post by maurizio_marrocco on 2015-09-26
Hi
I'm an ubuntu newbie
i have 14.04 lts

I wanted to speed up my old pc so I had a bit of a clean up
I would like to be specific about what I did but I didn't make a note of it.

when I now switch on my pc everything seems to be working fine except for 'no signal input check video cable' message on the screen and it just stays blank. 

I didn't do anything to the hardware but I guess I must have changed something or uninstaled something by mistake.

I would be really grateful  if someone could point me in the right direction. 

I have tried most of today searching on the internet for a solution but to no avail. 

any help appreciated.

thanks

---

### Post by tgalati4 on 2015-09-26
Welcome to the forums.  If you deleted any system software, then it's possible that you broke your video driver.

When you boot hit "esc" and get to a GRUB2 menu, then select rescue shell.  That will boot you into a root terminal for troubleshooting.

When you get to that terminal:

```
lspci | grep VGA
```

From now on, take notes about your actions so you can "unroll" them when things break.

---

### Post by grahammechanical on 2015-09-26
Run the Try Ubuntu session from the Ubuntu DVD disc or USB memory stick. Does that get you to a working desktop? If it did, then I would simply backup any data I did not want to lose and re-install.

---

### Post by maurizio_marrocco on 2015-09-26
Thank you for your help but this didn't work for me 


ubuntu version 2.02 beta2-9ubuntu1.3

Options
advanced options
memorytest (memetest86+)
memorytest (memetest86+, serial console 115200)


I selected advanced options

options
ubuntu, with linux 3.13.0-63-generic
ubuntu, with linux 3.13.0-63-generic(recovery mode)
ubuntu, with linux 3.13.0-62-generic
ubuntu, with linux 3.13.0-62-generic(recovery mode)

I selected the first recovery mode option

Options
resume normal boot
clean
dpkg
failsafex
fsck
grub
network
root
system-summary

I seleected root and entered

lspci | grep VGA

I then hit "enter"

It then shows "vga compatible controller:advanced micro devices, inc. [amd/ati] rv516 radeon x1300/x1550 series]

I am stuck at this point and can only force a reboot by switching off the computer and on again. 

It doens't solve the problem. 

Can anyone please offer another suggestion. 

thanks

---

### Post by maurizio_marrocco on 2015-09-26
I forgot to mention that the ubuntu log displays briefly before the screen goes blank

---

### Post by maurizio_marrocco on 2015-09-26
Sorry I meant to say the ubuntu Logo (not the log)

---

### Post by cariboo on 2015-09-26
There is no

> ubuntu version 2.02 beta2-9ubuntu1.3

If you can boot into recovery mode, and drop to a root prompt, then type:

```
cat /etc/lsb-release
```

it should display something similar to this:

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu Wily Werewolf (development branch)"
```

---

### Post by tgalati4 on 2015-09-26
OK, so we know you have an ATI radeon graphics card that is driven by the "radeon" module.  Perhaps you deleted your radeon module.  In a root terminal examine the following:

```
apt-cache policy xserver-xorg-video-ati
apt-cache policy xserver-xorg-video-radeon
```

It should look like:

> tgalati4@Mint17 ~ $ apt-cache policy xserver-xorg-video-ati
xserver-xorg-video-ati:
  Installed: 1:7.3.0-1ubuntu3.1
  Candidate: 1:7.3.0-1ubuntu3.1
  Version table:
 *** 1:7.3.0-1ubuntu3.1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:7.3.0-1ubuntu3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
tgalati4@Mint17 ~ $ apt-cache policy xserver-xorg-video-radeon
xserver-xorg-video-radeon:
  Installed: 1:7.3.0-1ubuntu3.1
  Candidate: 1:7.3.0-1ubuntu3.1
  Version table:
 *** 1:7.3.0-1ubuntu3.1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:7.3.0-1ubuntu3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages


If the files are in place then try to reconfigure your graphics:

```
dpkg-reconfigure xserver-xorg
```

Reboot.

```
reboot
```

---

### Post by maurizio_marrocco on 2015-09-27
thank you but it didn't work.

I typed
apt-cache policy xserver-xorg-video-ati
apt-cache policy xserver-xorg-video-radeon

everything looked ok

then when I typed this
dpkg-reconfigure xserver-xorg

I got this
failed to create symbolic link '/etc/x11/x' Read-only file system

---

### Post by tgalati4 on 2015-09-27
Well, you have a Read-Only file system.  That means you have an issue that needs to be fixed with the file system first before doing anything else.  A file system will get marked "RO" when there is a sudden shutdown (like pressing the power button), or a failing disk.  Your file system is now "unclean" and needs to be checked before write access is allowed.

Unfortunately, to check your file system, you need to be unmounted from that file system.  So, reboot, get to the recovery menu and choose "fsck".

Take note of what actions were required.  Summarize what was done.  Then reboot into the root console and try to reconfigure again.

And from now on rather than say "It didn't work", say "What is next?".  We have no idea what state your system is in.  There is no single command that will fix it.  It is a long process and it takes patience.

---

### Post by SeijiSensei on 2015-09-27
> **grahammechanical said:**
> Run the Try Ubuntu session from the Ubuntu DVD disc or USB memory stick. Does that get you to a working desktop? If it did, then I would simply backup any data I did not want to lose and re-install.
My advice as well.  You will end up spending much more time trying to fix this problem than you will just reinstalling.

Next time around, I recommend partitioning your disk drive so that /home is on a separate partition.  Then you can change the installation but not touch your personal files.

---

### Post by maurizio_marrocco on 2015-09-27
Thank you for this. 
My screen is back so I sincerely appreciate your help. 

I must have forced a shutdown at some point which rang a bell when you mentioned it in last the last post.

---

### Post by maurizio_marrocco on 2015-09-28
Thank you very much I have my screen back now.

Since you mentioned it I think I did force a shutdown (making my files read-only)

So I did as you said by going into ubuntu advanced options, choosing the recovery option and selecting 'fsck' 

Then selecting root and typing 
dpkg-reconfigure xserver-xorg

then

reboot

---

### Post by tgalati4 on 2015-09-28
Glad you got it repaired.  Now keep this procedure handy, because it is a common problem in Linux when you either have a hard-shutdown or graphics problems or both.

---

### Post by kendinh8 on 2015-09-29
i ran into the same problem here, after the foot logo , the screen just went black. i tried to follow above steps , but after typing the reconfigure command ,nothing happen. 
i also have a ati raedon hd7770 card. 
is there any way that i can try to fix this. thanks

---

