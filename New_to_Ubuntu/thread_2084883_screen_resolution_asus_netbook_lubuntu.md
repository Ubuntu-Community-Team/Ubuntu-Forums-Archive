---
title: "screen resolution asus netbook lubuntu"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by Althusian on 2012-11-16
I've installed Lubuntu on an Asus EeePC 1015CX.
I tried it first running on a 16gb peg, runs like a dream with 1024x600 resoluton.

Installed on the netbook itself, it only does 800x600.

-- I tried installing additional drivers (cedar trail I think). When I boot the blue lubuntu screen (at 1024x600) comes on for a split second.  The I get a blinking cursor.  I can get command line (again, at 1024x600) but thats all.

-- I reinstalled and xrandr gives me this:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 

Appreciate any advice.

---

### Post by NikTh on 2012-11-16
Hi , 

can you give the results of 
```
lsb_release -rcd ; uname -r
lspci -nnkv | grep -iA10 vga
```

Click on **"New Reply"** and put the results inside [CODE] tags to be easier to read. [See here how]("http://i.stack.imgur.com/zADbK.png")
Thanks

---

### Post by idoitprone on 2012-11-16
> **Althusian said:**
> I've installed Lubuntu on an Asus EeePC 1015CX.
I tried it first running on a 16gb peg, runs like a dream with 1024x600 resoluton.

Installed on the netbook itself, it only does 800x600.

-- I tried installing additional drivers (cedar trail I think). When I boot the blue lubuntu screen (at 1024x600) comes on for a split second.  The I get a blinking cursor.  I can get command line (again, at 1024x600) but thats all.

-- I reinstalled and xrandr gives me this:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 

Appreciate any advice.

it is a issue.... you are using cedar trail.....

cedar trail does not use intel graphics. They use powerVR graphics.

I dont know what to say because I do not know there is a method to install powerVR onto your netbook

---

### Post by Althusian on 2012-11-17
Here's the output:


lsb_release -rcd ; uname -r
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
3.2.0-33-generic-pae

lspci -nnkv | grep -iA10 vga:
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device [1043:84a9]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at dfc00000 (32-bit, non-prefetchable) [size=1M]
	I/O ports at f0e0 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8437]
	Flags: bus master, fast devsel, latency 0, IRQ 44

thanks,

---

### Post by idoitprone on 2012-11-17
> **Althusian said:**
> Here's the output:


lsb_release -rcd ; uname -r
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
3.2.0-33-generic-pae

lspci -nnkv | grep -iA10 vga:
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:84a9]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at dfc00000 (32-bit, non-prefetchable) [size=1M]
    I/O ports at f0e0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8437]
    Flags: bus master, fast devsel, latency 0, IRQ 44

thanks,
there is no support for linux for power VR graphics
[http://communities.intel.com/thread/29157?start=0&tstart=0](http://communities.intel.com/thread/29157?start=0&tstart=0)
[https://bbs.archlinux.org/viewtopic.php?id=145349](https://bbs.archlinux.org/viewtopic.php?id=145349)
it is useless and the community cannot do anything about it.
Go to intel site and beg them or say you suck or something


this is your only support
[http://ubuntuforums.org/showthread.php?t=1984236](http://ubuntuforums.org/showthread.php?t=1984236)

---

### Post by Althusian on 2012-11-17
Well that may be true.
But the same model can be bought off the shelf in Italy with Ubuntu installed.  
And if I run Lubuntu from a USB stick, the machine will deliver 1024x600.
So it ought to run OK installed on the machine, you'd think ...

---

### Post by NikTh on 2012-11-17
Hi , 

This is a "Cedarview Integrated Graphics Controller" . Some people say that might this PPA work. 
Check it => [https://launchpad.net/~sarvatt/+archive/cedarview](https://launchpad.net/~sarvatt/+archive/cedarview)
**Please read the description** 

As you using Lubuntu (LXDE) you only need the correct resolution. This PPA (driver included) might offer you the appropriate screen resolution.

Thanks

---

### Post by Althusian on 2012-11-17
Thanks, I'll give it a go.  Yes, it is just the resolution I need sorting out.

---

### Post by Althusian on 2012-12-28
Right then, had a bit of time over Christmas to try again and it's like this:

- tried installing cedarview drivers, and couldn't get gui, just the terminal (frustratingly, it was clearly a terminal in 1042x600...).  Tried startx and one or two other commands to get the gui going,but just got error messages back.

- tried 12.10 of Lubuntu, installing from a USB, and it wouldn't load at all

- reinstalled 12.04 from USB

- then tried updating the USB mounted version of 12.04 with cedarview drivers (worked ok a month or two back) to get higher resolution.  But that didn't work: it won't load at all now (just get a blank screen and a flashing orange "-"...)
 
To recap, all I want is 1042x600 resolution on this Asus, don't want Unity (hence using Lubuntu).

I suspect the following:
- updating the drivers would work if the d**** thing would boot ok. Maybe I ought to focus attention on booting from the cli. 
- 12.04 used to run the higher resolution off a USB stick no problem, but doesn't do so now.  The result of some 'upgrade' I guess.
- 12.10 won't boot at all.  Think I'll wait till the bugs have been ironed out before I try it again.

I think I have the following options:
- delete Lubuntu and go back to Windoze (yuck)
- accept 800x600 is the best it'll do and accept the low res and the distorted images
- install the drivers and see if I can get from the terminal to a full graphical boot
- give it to the dog and buy an ipad

Thanks to those who advised, if I do find a solution I'll try and remember to post it, ---

LATER EDIT: see my following post ([http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/](http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/)) for solution...

---

### Post by Althusian on 2012-12-28
!!! SUCCESS !!!

I'll stop winging now: the problem was - I believe - to do with the kernel.  

Followed the instructions at:
[http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/](http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/)

... and its running as sweet as... well, as a nut.  Apologies to Asus, whose netbook is now my new Best Thing...

---

