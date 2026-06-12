---
title: "HOWTO: Get your ps/2 mouse work on a kvm switch"
date: 2005-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by woifi on 2005-04-21
hi folks!

I read a lot about troubles with ps/2 mice on a kvm switch (there's something screwed up with the psmouse.c in the 2.6.x kernels). 

With Debian Sid (I used sid before warty) I solved this in the german [debianforum.de](http://www.debianforum.de/forum/viewtopic.php?t=26704&postdays=0&postorder=asc) by editing my grub.conf:```
kernel          /boot/vmlinuz-2.6.7-1-k7 root=/dev/hda1 "psmouse.proto=imps" ro
``` Unfortunately this works not with Ubuntu.

So I had to found another workaround for this: Just edit your /etc/modules:```
ide-cd
ide-disk
ide-generic
lp
mousedev
**psmouse proto=exps**
nvidia
```

Make sure there is **NO** "." between "psmouse" and "proto" and you have "mousedev" in your /etc/modules". Using exps instead of imps has advantages when you like to use your thumb buttons.

edit: This works with warty too.

hth

woifi

---

### Post by kelvinq on 2005-04-21
Honestly, I don't see why the particular problem for PS/2 mouse on a KVM. I mean, the computer *wouldn't* know that you are on a KVM switch, right?

I'm using a Belkin KWM for both my Linux and Windows boxes. No problem switching around whether through a keyboard or with the button on the switch itself.

---

### Post by woifi on 2005-04-21
well, a lot of people do have problems, just use the forums search function:

[http://www.ubuntuforums.org/showthread.php?t=20220&highlight=kvm+mouse](http://www.ubuntuforums.org/showthread.php?t=20220&highlight=kvm+mouse)
[http://www.ubuntuforums.org/showthread.php?t=18914&highlight=kvm+mouse](http://www.ubuntuforums.org/showthread.php?t=18914&highlight=kvm+mouse)
[http://www.ubuntuforums.org/showthread.php?t=18560&highlight=kvm+mouse](http://www.ubuntuforums.org/showthread.php?t=18560&highlight=kvm+mouse)

or:> [http://kerneltrap.org/node/view/2199](http://kerneltrap.org/node/view/2199)
I have to confirm this. The Linux 2.6.x Kernel seem to have problems receiving the RAW Wheelmouse Signals when sent through an KVM.

switching around wasn't a problem, but the mouse refused cooperation (ie fuzzy behavior, jumping around ;))

---

### Post by ignavia on 2005-04-21
I have a D-Link KVM with this problem, though I'm switching between two Linux boxes. I think I figured it out though: Mine is working flawlessly right now, switching all the time. I *think* if you keep the KVM on one machine all the way through bootup, it'll be okay. If you switch out during boot, then it'll lose the mouse when you switch back.

I've done no extensive testing or anything, this is just my hypothesis. (I'm reluctant to test since that would involve me rebooting both machines, and since they're both great, I'd hate to ruin that.)

---

### Post by mrt on 2005-04-21
[QUOTE=ignavia]I have a D-Link KVM with this problem, though I'm switching between two Linux boxes. I think I figured it out though: Mine is working flawlessly right now, switching all the time. I *think* if you keep the KVM on one machine all the way through bootup, it'll be okay. If you switch out during boot, then it'll lose the mouse when you switch back.

I've done no extensive testing or anything, this is just my hypothesis. (I'm reluctant to test since that would involve me rebooting both machines, and since they're both great, I'd hate to ruin that.)[/QUOTE]


I had a no name kvm that did exactly that.  I learned this early on - it does not surprise me that you say this.  I bought a Cybex 4port kvm to get around this problem.  I read that it has some kind of "emulation" ability that allows booting pcs to detect the ps2 connection even if you're on another pc at the time.

I haven't had a chance to test that yet, though.  It seems it will only take genuine ps2 mice!  That means no usb to ps2 converter!  That means using an ancient ball mouse because you can't find a good optical mouse with a genuine ps2 connector. ](*,) 

If anyone knows of a way around this, I'd love to hear it.

---

### Post by woifi on 2005-04-21
no problems with a usb to ps/2 converter here, I'm using a Logitech MX700

have you edited your /etc/modules?

---

### Post by mrt on 2005-04-21
[QUOTE=woifi]no problems with a usb to ps/2 converter here, I'm using a Logitech MX700

have you edited your /etc/modules?[/QUOTE]

if it affects my windows box too, wouldn't the problem lie within the kvm?
on my old no-name kvm, the ps2 converter would work, but the picture is much better on the cybex

---

### Post by crane on 2005-04-21
> **woifi]hi folks!

I read a lot about troubles with ps/2 mice on a kvm switch (there's something screwed up with the psmouse.c in the 2.6.x kernels). Well, I did have those problems too and I read the fucking manuals and searched the fucking web  said:**
> debianforum.de[/url] by editing my grub.conf:```
kernel          /boot/vmlinuz-2.6.7-1-k7 root=/dev/hda1 "psmouse.proto=imps" ro
``` Unfortunately this works not with Ubuntu.

So I had to found another workaround for this: Just edit your /etc/modules:```
ide-cd
ide-disk
ide-generic
lp
mousedev
**psmouse proto=exps**
nvidia
```

Make sure there is **NO** "." between "psmouse" and "proto" and you have "mousedev" in your /etc/modules". Using exps instead of imps has advantages when you like to use your thumb buttons.

edit: This works with warty too.

hth

woifi


I haven't had any problems myself. May it is a boot up problem but I constantly switch between computers aven during boot.


-note-
Is there really a need for the colorful language? :-|

---

### Post by woifi on 2005-04-22
I think we do not need more posts like "I have no problems with my kvm". The point is, that some people have problems with their kvm and I hope I can help others with my solution.

@mrt
k, sounds like this is not a linux problem ;)

Thanks

woifi

---

### Post by terence34 on 2005-06-10
Hi Woifi
I for one am very grateful for your tip.  My (KVM) connected mouse was jumping all over the place and your suggestion fixed the problem.
Terence

---

### Post by tdk337 on 2005-06-18
I am new to Linux and I am encountering the same problem as the rest of you. I have my Ubutu box hooked up to a Belkin KVM box. How can I edit this file using the command prompt. I am familiar with dos and am just learning linux. Can someone write me a step by step fix for this without the use of the mouse? Or do I have to disconnect my KVM to fix the issue?

---

### Post by raresp on 2005-06-18
Thanks a lot for your suggestion. 
the method of adding in grub.conf.. is working on a SuSE 9.3 Linux kernel 2.6.11.4-21.7-default

Thanks again

raresp

---

### Post by spockrock on 2005-06-20
hmmm......I tired this to see if it would fix my problem with ubuntu box, if I boot up the ubuntu box while using the mouse and keyboard on the windows box, when I go to login, my mouse would jump or simply not respond as it should.........I still have the same problem, after this, I think it maybe my kvm switch, but luckly it works fine as long as I boot up ubuntu while the kvm  is on the ubuntu box with my mx duo.......

---

### Post by optikal on 2005-06-28
/etc/modules
```
ide-cd
ide-disk
ide-generic
lp
mousedev
**psmouse proto=exps**
nvidia
```

The above, adding proto=exps after psmouse, worked great for me and my KVM!  My mouse was all over, and now its great.  Thank you!

---

### Post by blueshrike on 2005-09-13
Hi

I tried the psmouse proto=exps solution and it did not work. 

I have a logitech mx510 mouse with USB-PS2 converter connected to a D-Link DKVM-2 KVM switch.  I am running ubuntu 5.04.  

Any suggestions on how to fix this are greatly appreciated.  Also if anyone could point me in the direction of some documentation that explains what the various proto  arguments mean ... that would be cool (i.e. imps, exps, bare)

It used to work with my debian 2.4 kernel (both testing and unstable)

thanks,

-jacques.

edit: I found this in another thread.  Apparently this is a known problem and has not been fixed and does not have a workaround if none of the things suggested above work.  Please see:

[http://bugzilla.kernel.org/show_bug.cgi?id=2082](http://bugzilla.kernel.org/show_bug.cgi?id=2082)

---

### Post by TwiceOver on 2005-09-14
No go on my KVM also.  Mouse jumps all over the place, I have not been able to fix this.

---

### Post by le0buntu on 2005-10-09
Thanks woifi.
The [FONT="Courier New"]psmouse proto=exps[/FONT] line in [FONT="Courier New"]/etc/modules[/FONT] fixed things for me.
I was getting random mouse jumps and clicks after switching back to my Ubuntu 5.10 install from other machines on th 4 port Belkin KVM that I have.

Mouse control prior to switching had been fine, and it was only upon return that I was experiecing problems.
I'd never tried switching machines during the boot process so can't comment on that.

Thanks
Leo

---

### Post by kjoyce on 2005-10-15
I have a pretty cheesy solution, I plug the mouse into the *computer* when it boots up.  I then plug the mouse into the KVM switch, and viola!  Kind of a hassle if  you routinely shut your machine down, but not a big issue if you reboot rarely.  Any other solutions would be awesome, here are the details of what I tried before:

My usb mouse connected through a ps/2 converter to a Belkin 2-Port KVM switch did not respond to the following solutions:

1. changing the /etc/modules file have each of these 4 lines (seperately of course):
```

psmouse proto=raw
psmouse proto=exps
psmouse proto=imps
psmouse proto=base

```
With each of these options I did the following
2. I also let the computer boot completely with each of the options added.
3. I also manually removed the module and re-added it with the commands
```

modprobe -r psmouse
modprobe -a psmouse
Ctrl-Alt-F7 Ctrl-Alt-Backspace

```
I

---

### Post by plainsman on 2005-10-18
I have a Belkin F1DB104P.  I found two methods which worked:

1). psmouse proto=exps in /etc/modules & then after switching to Ubuntu remove and readd psmouse with modprobe like above. No need to restart X.

2). Instead of useing the physical button to switch computers, use the hot key combo <scroll lock><scrool lock><# to switch to>. With this my Ubuntu mouse worked fine.

---

### Post by rwilliam42 on 2005-11-25
I experiened the same 'crazy' mouse problems with my KVM setup.  Two laptops, one Windows XP machine (work) and one Ubuntu machine (personal).  Both on docking stations connected to a keyboard, mouse and monitor through a Belkin OmniView E series KVM.  The mouse is a cheapie GE 3-button optical (Intellimouse clone).  The following post fixed the problem for me:

[http://www.ubuntuforums.org/showthread.php?t=6550&highlight=mouse+kvm](http://www.ubuntuforums.org/showthread.php?t=6550&highlight=mouse+kvm)

---

### Post by Geekboy on 2006-01-29
I had the same problem.  I have a 8 port KVM with PS/2 inputs.  I just bought a cheap ps/2 optical mouse (no USB, straight ps/2.  The last usb/ps/2 converter didn't work).  When I booted both of my Ubuntu PC's, the cursor flipped out.

I did want was suggested in the first post, and the mouse worked fine.  I am using Breezy for both PC's.

Is it ok to move this thread to Breezy How-tos?

---

### Post by doctorstrobe on 2006-03-22
Adding the **psmouse proto=exps** line to my etc/modules file fixed a KVM problem I've been having.

I'm using a JustCom 4 port KVM which normally works fine with Windows, but in Ubuntu or Kubuntu my mouse wheel stopped working once I switched the KVM to another computer.

It's working great now.
I have no idea what** psmouse proto=exps** actually means but it works...

Thanks.

---

### Post by jpb on 2006-03-28
I had the mouse-jumping problem after switching away from my Ubuntu box and switching back. I have a no-name 2-port mouse/keyboard switch. Thanks for the tip, after changing "psmouse" to "psmouse proto=exps" in /etc/modules it works fine now.

---

### Post by bigbear on 2006-04-07
[QUOTE=woifi]hi folks!

I read a lot about troubles with ps/2 mice on a kvm switch (there's something screwed up with the psmouse.c in the 2.6.x kernels). 

With Debian Sid (I used sid before warty) I solved this in the german [debianforum.de](http://www.debianforum.de/forum/viewtopic.php?t=26704&postdays=0&postorder=asc) by editing my grub.conf:```
kernel          /boot/vmlinuz-2.6.7-1-k7 root=/dev/hda1 "psmouse.proto=imps" ro
``` Unfortunately this works not with Ubuntu.

So I had to found another workaround for this: Just edit your /etc/modules:```
ide-cd
ide-disk
ide-generic
lp
mousedev
**psmouse proto=exps**
nvidia
```

Make sure there is **NO** "." between "psmouse" and "proto" and you have "mousedev" in your /etc/modules". Using exps instead of imps has advantages when you like to use your thumb buttons.

edit: This works with warty too.

hth

woifi[/QUOTE]
I have the above problem with ubuntu, could you explain in a bit more detail how to do this, I am a complete novice with linux
Thanks for any help:confused:

---

### Post by qpieus on 2006-04-08
bigbear -

open up a terminal window.
at the prompt, type: sudo gedit /etc/modules  
a new window ( the gedit program) opens up with the "modules" file shown (it's just a text-like file)
Add the line "psmouse proto=exps" to the file and then save the file.

This fix worked for me, although my mouse problems weren't as severe as yours.

Here's what my modules file looks like:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
psmouse proto=exps

---

### Post by tmarthal on 2006-06-21
I also had the same problem with my PS2 mouse and a linkskey LKV-S02 KVM (same as LKV-S04). I only have the keyboard/mouse plugged in to the KVM (I use the DVI and analog display switch on my DELL 2001FP) and the original post solved the jumping for me as well. This is with 6.06.

I searched for \ubutnu mouse problem\ and \ubutnu mouse kvm jump\ on google, so hopefully adding those terms here will help the indexing!

ubutnu ps2 mouse problem kvm !

---

### Post by bmeuwis on 2006-07-01
I also have the same problem and tried to use the fix as suggested in the first post, but I don't seem to have mousedev on my system (6.0.6). How do I get/install it ?

---

### Post by driedfruit on 2007-04-26
I know this is an old topic, but I read it while trying to solve my own problem, so I have a feeling a had to contribute...

Simple addition of proto=imps or proto=exps didn't fixed it for me, but adding resync_time like this:

> psmouse proto=imps resync_time=10

solved my problem! Hope that'll be to some use for someone :)

---

### Post by IddyBittyBugs on 2008-04-24
> **driedfruit said:**
> I know this is an old topic, but I read it while trying to solve my own problem, so I have a feeling a had to contribute...

Simple addition of proto=imps or proto=exps didn't fixed it for me, but adding resync_time like this:



solved my problem! Hope that'll be to some use for someone :)



I'm also reading this thread for the 1st time trying to fix my own problem.  I have an old Blekin OmniCube 4-port KVM connecting an Ubuntu 7.10, a Kubuntu 7.10, and a Windows 2000 machine, and the mouse works fine for each until I switch to another PC.  When I come back to either my Ubuntu or Kubuntu machine, the scroll stops working.  I have had the mouse-jumping problem as well as video sync problems with older kernels, but now only the scroll function is missing.

Switching back to the Windows machine the scroll works fine every time, so it is not the hardware, and I don't have this problem with Slackware 9.0.  I believe this is most certainly an Ubuntu (or Debian) problem.  Anyone know of a solution?

---

### Post by etc12483 on 2008-04-25
> **driedfruit said:**
> I know this is an old topic, but I read it while trying to solve my own problem, so I have a feeling a had to contribute...

Simple addition of proto=imps or proto=exps didn't fixed it for me, but adding resync_time like this:



solved my problem! Hope that'll be to some use for someone :)

Ditto for me.

I have been trying to install Hardy on a Dell Precision 670 using a Belkin 2-port KVM switch. I have a Microsoft Wireless Optical Desktop hooked up to the KVM switch.  The KVM switch is PS/2 only, no USB ports.  The Wireless desktop has a PS/2 keyboard port and a USB mouse port.  I am using a USB to PS/2 connector for the mouse.  This setup has worked for me on Windows XP as well as Ubuntu Dapper, Edgy and Feisty.  I currently have Feisty on another computer and I am trying to install Hardy on the Precision 670.

I am able to use the mouse without any problems when booting off of the 8.04 Live CD, but as soon as I reboot, I loose all mouse functionality, the cursor wouldn't move, none of the buttons would respond.  I tried adding ```
psmouse proto=exps
``` to /etc/modules and that didn't work.  I replaced that line with ```
psmouse proto=imps resync_time=10
``` and that worked beautifully.  This is an interesting issue because I had been running 7.10 on this computer previously without any mouse problems at all.  I had the same problem on a couple of the beta / pre-release versions of 8.04 as well.

---

### Post by Pie` on 2008-09-24
I recently bought a DKVM-2K switch and it all works fine, except the only resolution I can get under ubuntu is 800x600. It works fine under XP, the mouse and keyboard work fine its just the screen.

---

