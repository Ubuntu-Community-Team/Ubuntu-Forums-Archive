---
title: "How To Compile the new 2.6.16 kernel from kernel.org"
date: 2006-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by xXx 0wn3d xXx on 2006-04-09
I just finished compiling the newest 2.6.16 kernel from kernel.org and I am getting much better performance. In what follows, I will show you how to compile and configure the latest kernel. You do not need to use the 2.6.16 kernel but it is the first kernel of the release kernel and performance patches are only made for these releases. (**ex**: 2.6.16, 2.6.17 _NOT_ 2.6.16.20) Feel free to compile a kernel besides the first release cycle kernel. You do _not_ need the patch and you can configure the kernel for maxium speed in xconfig. A tutorial to optimize the kernel you are building can be found [ **here**. ](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507)
 
Before you begin, you will need to get a kernel
Download the 2.6.16 kernel and it's performance patch:[ The 2.6.16 kernel ](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.tar.bz2)
[ Latest Kernel Patch ](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/2.6.16-ck12/patch-2.6.16-ck12.bz2) Don't apply the patch if you are compiling a kernel other then 2.6.16 otherwise the kernel will _not_ compile.

Check out kernel.org for the latest stable/release canidate kernel.

**1.** [COLOR="Blue"] Install needed utilities to configure the kernel[/COLOR]

> sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev

**2.**[COLOR="BLUE"] Now we are going to move the kernel and unpack it.[/COLOR]

> sudo cp linux-2.6.16.tar.bz2 /usr/src

**3.**[COLOR="Blue"] Now we are going to move to /usr/src[/COLOR]

> cd /usr/src

**4.**[COLOR="Blue"] Now unpack it:[/COLOR]

> sudo tar -xvjf linux-2.6.16.tar.bz2

**5.**[COLOR="Blue"] Rename the folder:[/COLOR] ONLY needed for 2.6.16 kernel ! You don't need to do this.

> sudo mv linux-2.6.16/ linux-2.6.16ck12

**6.**[COLOR="Blue"] Now we are going to remove the link to the linux directory:[/COLOR]

> sudo rm -rf linux

**7.**[COLOR="Blue"] Make a new link to the new kernel:[/COLOR]

> sudo ln -s /usr/src/linux-2.6.16ck12 linux

**8.**[COLOR="Blue"] Move to the Linux directory:[/COLOR]

> cd /usr/src/linux

**9.**[COLOR="Blue"] Make yourself root:[/COLOR]

> sudo -s -H

**10.**[COLOR="Blue"] Apply the performance patch: [/COLOR] **Don't use if you are not patching the 2.6.16 kernel !**

> bzcat /home/$USER/patch-2.6.16-ck12.bz2| patch -p1

**11.**[COLOR="Blue"] Now we are going to import your current kernel configuration:[/COLOR]

> uname -r

**12.**[COLOR="Blue"] Now import it: Make sure to replace the kernel version in this following command from the one from uname -r.[/COLOR]

> sudo cp /boot/config-2.6.14-ck1 .config

**13.**[COLOR="Blue"]Configure the kernel:[/COLOR]

> make xconfig

Here are some performance tips from [ this thread. ](http://ubuntuforums.org/showthread.php?t=84174&highlight=compile+kernels)

> In "General Setup" activate:

-Support for paging of anonymous memory (swap)
--Support for prefetching swapped memory

In "Processor type and features":

-Processor family Choose the model of your processor.

Activate:

-Preemption Model
--Voluntary Kernel Preemption (Desktop)

-High Memory Support
--off -if you have less than 1 GB of RAM
--1GB Low Memory Support -if you have 1GB of RAM
--4GB -if you have more than 1GB of RAM

-Timer frequency
--1000 Hz

In "Device drivers" go to "Block devices" and in "IO Schedulers" leave only the "CFQ I/O scheduler" activated, which provides the best performance.

In "Kernel hacking" uncheck "Kernel debugging".

Ctrl+S to save the kernel configuration and then close the window.

**Note**: Not all the options will be the same in newer kernels.

**14.**[COLOR="Blue"] Let's build the kernel: Make sure that you are in /usr/src/linux with full root access. Make sure that you are. This will build a debian file that you can install.[/COLOR]

Now, in terminal do the following:

> make-kpkg clean

make-kpkg -initrd --revision=ck12 kernel_image kernel_headers modules_image
**Note:** You can replace "ck12" with anything you want. Like "k7" or "686."
**15.**[COLOR="Blue"] Install the .deb fine in /usr/src. In terminal do[/COLOR] 

> sudo dpkg -i <name of the file>

[COLOR="Blue"] Now reboot and you will have a much faster system ![/COLOR]
-------------------------------------------------------------------------

How I learned to do this:
[ 2.6.14 Vanilla Kernel ](http://ubuntuforums.org/showthread.php?t=84174&highlight=compile+kernels) I based my tutorial on this thread. Thank you for writing this tutorial RubenGonc !

And I also learned some stuff from [ this thread ](http://ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel)
-------------------------------------------------------------------------
[COLOR="Red"]_**Troubleshooting:**_[/COLOR]

**Q**: My Wifi Doesn't work !

**A**:To get wifi working, compile the new ndiswrapper from source. Follow the [ tutorial. ](http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source)

**Q**: When I reboot I get Grub Error 22 ! WTF ???

**A**: You may have missed a step or messed something up. When it says Grub Loading..... press esc and you will be able to boot  with another kernel. Then you should go into synaptic and uninstall the broken kernel and then reompile it.
**--------------------------------------------------------------------------------**
**Q**: How can I get fglrx and DRI working on my new kernel ? 

**A**: Type this in terminal:

> sudo apt-get install fglrx-kernel-source

Reboot and if that does not work, make sure fglrx is in the Driver section.
**---------------------------------------------------------------------------------**
**Q**: I need kernel headers for my custom kernel.

**A**: I updated the howto and edited the last step to build a kernel image, kernel module image, and kernel headers. Thank you to tseliot for his kernel thread because I found the command there. You can view the thread [ here. ](http://ubuntuforums.org/showthread.php?t=85064&highlight=custom+compile)
**------------------------------------------------------------------------------------**
**Q**: I want to optimize my kernel ! What do I select ???

**A**: I just wrote [ this tutorial ](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507) on how to configure your kernel for enhanced performance. I hope [ it ](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507) helps.
**----------------------------------------------------------------------------------------**
**Q**: Why did you write this tutorial ?
**A**: I wrote this tutorial to help give back to the Ubuntu community. I've had such a good expericence with ubuntu that I want to help others. This community is great :)

---

### Post by dicecca112 on 2006-04-09
should be name of file for 16th step

also didn't work for me, there is no option to boot the 2.6.16 kernel in my grub

---

### Post by Juanito on 2006-04-09
Did you try manually adding the parameters to /boot/grub/menu.lst?

---

### Post by xXx 0wn3d xXx on 2006-04-09
[QUOTE=Juanito]Did you try manually adding the parameters to /boot/grub/menu.lst?[/QUOTE]
or sudo update-grub. I just ran through the tutorial again and I compilied the kernel and the set it up and it worked.

---

### Post by dicecca112 on 2006-04-09
weird, it shows in the menu.lst. but not in my grub.  ran update-grub too and it shows up there, but not on boot

---

### Post by xXx 0wn3d xXx on 2006-04-09
[QUOTE=dicecca112]weird, it shows in the menu.lst. but not in my grub.  ran update-grub too and it shows up there, but not on boot[/QUOTE]
That's weird...check if it's hidden. Also, after upgrading up to this kernel, my sound works and it never did before !

---

### Post by dicecca112 on 2006-04-09
how come the path reads number-cks3 and on step  			 				8 it says sudo ln -s /usr/src/linux-2.6.16ck3 linux

---

### Post by Juanito on 2006-04-09
I copied and pasted everything and succeeded! now I can suspend and resume!!!!! but I still don't have wifi.

---

### Post by dpicker on 2006-04-09
To get usplash you need to make sure you enable this in the config:

Graphics support:
-VGA 16-color graphics support - module (m)
-VESA VGA graphics support - build in kernel (y)

Console display driver support:
-VGA text console and Video mode selection support- build in kernel (y)
-MDA text console-module (m)
-Framebuffer Console and Framebuffer Console Rotation support-build in kernel (y)

Not sure how to change from "m" to "y" and vice versa in xconfig so I opened the .config file in gedit and checked it manually.

Archck patch includes the Con Kolivas patch but with lots of other cool things too like acpi updates and suspend2 but I had trouble compiling it.

It's here if you wanna hava a go: [http://iphitus.loudas.com/archck.php](http://iphitus.loudas.com/archck.php)

---

### Post by berserker on 2006-04-09
EDIT:  Code corrected.

---

### Post by Thios on 2006-04-09
Hi... Would anyone happen to know how to enable iptables support for the 2.6.16-ck3 kernel? Firestarter won't start without it...

---

### Post by R3linquish3r on 2006-04-09
Thats not a link to the patchset thats a link to the folder that the kernel is in before you compile it.

---

### Post by dicecca112 on 2006-04-09
> That's weird...check if it's hidden. Also, after upgrading up to this kernel, my sound works and it never did before !

how do I do that?

---

### Post by xXx 0wn3d xXx on 2006-04-09
[QUOTE=Thios]Hi... Would anyone happen to know how to enable iptables support for the 2.6.16-ck3 kernel? Firestarter won't start without it...[/QUOTE]
Iptables starts but firestarter doesn't reconize it. Youb don't need firestarter anyway.

---

### Post by R3linquish3r on 2006-04-09
K well that completely drove me away from kernal compilation....

I dont know what I messed up but when I booted into the kernel it started in Failsafe. I logged in and when I went to start X it panicked. I booted my old kernel (2.6.12 ancient!) and THAT started in failsafe but X started at least. I uninstalled the package and now everything is back to normal. Think I'll wait till Dapper is released then do a fresh install of that so I have the latest kernel.

---

### Post by xXx 0wn3d xXx on 2006-04-09
[QUOTE=R3linquish3r]K well that completely drove me away from kernal compilation....

I dont know what I messed up but when I booted into the kernel it started in Failsafe. I logged in and when I went to start X it panicked. I booted my old kernel (2.6.12 ancient!) and THAT started in failsafe but X started at least. I uninstalled the package and now everything is back to normal. Think I'll wait till Dapper is released then do a fresh install of that so I have the latest kernel.[/QUOTE]
Very well, I would try and get comfortable with compiling kernels, once you compile your first one, the rest are simple. I origionally broke my system when I tried to install the 2.14.2 kernel but I got it the second time. I also tried to compile this kernel but it didn't work. I then compiled it again and it works great.

---

### Post by dxdemetriou on 2006-04-09
It's time to start my first community :)
I have followed all steps and the Kernel is building..
If something goes wrong, what must I do to rebuild the deb package?
What must I do for "make clean"?
I have build the Kernel in the past but not on the Debian based system, and I haven't try to rebuild the same kernel.

---

### Post by shorty0927 on 2006-04-09
*new to linux*
Well, things were going along smoothly until step 11.  Since I downloaded the kernel and patch to my desktop, I had to put that into the path.  Apparently, I must have forgotten to type in the pipe and everything after, because nothing happened.  Then when I got to step 15, I got an error (but I don't know what it was, because it scrolled off the terminal).  So after realizing I missed some things after the pipe, I tried re-typing it and I got launched into some program that wanted me to verify every little element of the patch (I think).  This wasn't in your instructions, so I'm panicking.  A snippet from the program that started up is below.  If anyone can get me out of whatever hole I've dug myself into. 

can't find file to patch at input line 7819
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: linux-2.6.16-ck3/arch/x86_64/Makefile
|===================================================================
|--- linux-2.6.16-ck3.orig/arch/x86_64/Makefile 2006-04-02 13:04:38.000000000 +1000
|+++ linux-2.6.16-ck3/arch/x86_64/Makefile      2006-04-02 13:05:11.000000000 +1000
--------------------------
File to patch:
Skip this patch? [y]
Skipping patch.
1 out of 1 hunk ignored
can't find file to patch at input line 7834
Perhaps you used the wrong -p or --strip option?

etc, etc, etc....

---

### Post by Juanito on 2006-04-09
For future reference, you can copy and paste things into Konsole or Yakuake ;) 

shit+ins

---

### Post by dxdemetriou on 2006-04-09
The new kernel works fine
The problem I have is with the motherboard
I don't know why, but it can't show the name of cards, or show other names
I have tested my tvcard on Athlon PC, and it works, but no on Intel PC the same tvcard.
I have upgraded my kernel beliving that it can recognize my motherboard
I don't know what goes wrong (and sorry if this is not the thread for that :)), but if somebody had the same problem and can help...
I have seen the names from lspci
-----------------------------------------------
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0259
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1259
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2259
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3259
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4259
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7259
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78 )
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3118 (rev 02)
-----------------------------------------
Thanks

---

### Post by Dropknee on 2006-04-10
> In "Device drivers" go to "Block devices" and in "IO Schedulers" leave only the "CFQ I/O scheduler" activated, which provides the best performance.

Dont know why I dont have in "Device drivers" the opcion IO Schedulers.

anyone have this same prob??

---

### Post by dxdemetriou on 2006-04-10
Another problem.. ;)
--------------------------------
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The kernel defined by this directory of header files does not have the same
address space size as your running kernel.
----------------------------------
I have checked all kernel directories in /usr/src/linux(version)/include, but nothing

---

### Post by Dropknee on 2006-04-10
Well new kernel up and running but need the splash screen :( Im goint to work with my wireless now, the strage thing is the default Ubuntu kernel have my Wireless drivers, and only with sudo ifconfig wlan up make my wireless appear, but now this dont work, I still have the drivers, but need to enable.....

Time to work lol

---

### Post by Rizado on 2006-04-10
[QUOTE=dpicker]To get usplash you need to make sure you enable this in the config:

Graphics support:
-VGA 16-color graphics support - module (m)
-VESA VGA graphics support - build in kernel (y)

Console display driver support:
-VGA text console and Video mode selection support- build in kernel (y)
-MDA text console-module (m)
-Framebuffer Console and Framebuffer Console Rotation support-build in kernel (y)

Not sure how to change from "m" to "y" and vice versa in xconfig so I opened the .config file in gedit and checked it manually.

Archck patch includes the Con Kolivas patch but with lots of other cool things too like acpi updates and suspend2 but I had trouble compiling it.

It's here if you wanna hava a go: [http://iphitus.loudas.com/archck.php](http://iphitus.loudas.com/archck.php)[/QUOTE]Could [this](http://dev.gentoo.org/~spock/projects/vesafb-tng/) work with usplash? I've tried it but I never got the usplash picture but I don't think I enabled the other stuff. Regular vesa doesn't work at all.
I see you recommend archck and vesafb-tng is included in that.

There's nothing called MDA text console-module in this kernel...

---

### Post by atlas95 on 2006-04-10
I have the spalsh but my ethernet doesn't work and my FAT32 partitions doesn't work too :/
Do you know how to resolve this ?
Thanks

---

### Post by Thios on 2006-04-10
> Iptables starts but firestarter doesn't reconize it. Youb don't need firestarter anyway.

Thanks for the reply.

After running xconfing I can see the option *networking support/networking options/TCPIP networking/network paket filtering/core netfilter configuration/netfilter xtables support*, which is unchecked. Its description says "This is required if you intend to use any of ip_tables,
ip6_tables or arp_tables."

It seems to me that my make oldconfig misses it...

So, my question is: how can I tell if iptables does actually work? And if it doesn't, how can I make it work?

---

### Post by Eazy© on 2006-04-10
[QUOTE=atlas95]I have the spalsh but my ethernet doesn't work and my FAT32 partitions doesn't work too :/
Do you know how to resolve this ?
Thanks[/QUOTE]

Think you need to do this: [http://doc.gwos.org/index.php/Mount_filesystem_new_kernel](http://doc.gwos.org/index.php/Mount_filesystem_new_kernel)
in order to mount your local filesystem. When I compiled kernel 2.6.15 this worked anyway. Haven't tested with the latest kernel. So I'm afraid you have to compile again.

---

### Post by IsSuE on 2006-04-10
i tried compiling the source, but i always get an error when i try to install the created .deb package:
```

Richte kernel-image-2.6.16-cks3 ein (kiwiv1) ...
Cannot find /lib/modules/2.6.16-cks3
Failed to create initrd image.
dpkg: Fehler beim Bearbeiten von kernel-image-2.6.16-cks3 (--install):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 kernel-image-2.6.16-cks3

```
sorry that it is in german, but the main error is in english

---

### Post by magnusbb on 2006-04-10
Have the pmount issues from earlier kernel compilations been fixed?

---

### Post by sYs^ on 2006-04-10
Hi!

Is this patch working with the latest  version kernel? (2.6.16.2)?
When I tried to apply the patch I got these lines:

```
sudo bzcat /home/dani/patch-2.6.16-cks3.bz2| patch -p1
patching file include/linux/sched.h
patching file kernel/sched.c
Hunk #6 FAILED at 153.
Hunk #7 succeeded at 203 (offset 1 line).
Hunk #8 succeeded at 212 (offset 1 line).
Hunk #9 succeeded at 222 (offset 1 line).
Hunk #10 succeeded at 248 (offset 1 line).
Hunk #11 succeeded at 270 (offset 1 line).
Hunk #12 succeeded at 407 (offset 1 line).
Hunk #13 succeeded at 445 (offset 1 line).
Hunk #14 succeeded at 504 (offset 1 line).
Hunk #15 succeeded at 638 (offset 1 line).
Hunk #16 succeeded at 647 (offset 1 line).
Hunk #17 succeeded at 831 (offset 1 line).
Hunk #18 succeeded at 844 (offset 1 line).
Hunk #19 succeeded at 873 (offset 1 line).
Hunk #20 succeeded at 910 (offset 1 line).
Hunk #21 succeeded at 930 (offset 1 line).
Hunk #22 succeeded at 938 (offset 1 line).
Hunk #23 succeeded at 968 (offset 1 line).
Hunk #24 succeeded at 993 (offset 1 line).
Hunk #25 succeeded at 1005 (offset 1 line).
Hunk #26 succeeded at 1014 (offset 1 line).
Hunk #27 succeeded at 1051 (offset 1 line).
Hunk #28 succeeded at 1105 (offset 1 line).
Hunk #29 succeeded at 1116 (offset 1 line).
Hunk #30 succeeded at 1138 (offset 1 line).
Hunk #31 succeeded at 1190 (offset 1 line).
Hunk #32 succeeded at 1213 (offset 1 line).
Hunk #33 succeeded at 1257 (offset 1 line).
Hunk #34 succeeded at 1274 (offset 1 line).
Hunk #35 succeeded at 1319 (offset 1 line).
Hunk #36 succeeded at 1365 (offset 1 line).
Hunk #37 succeeded at 1374 (offset 1 line).
Hunk #38 succeeded at 1385 (offset 1 line).
Hunk #39 succeeded at 1415 (offset 1 line).
Hunk #40 succeeded at 1432 (offset 1 line).
Hunk #41 succeeded at 1442 (offset 1 line).
Hunk #42 succeeded at 1452 (offset 1 line).
Hunk #43 succeeded at 1463 (offset 1 line).
Hunk #44 succeeded at 1493 (offset 1 line).
Hunk #45 succeeded at 1675 with fuzz 2 (offset 4 lines).
Hunk #46 FAILED at 1689.
Hunk #47 FAILED at 1725.
Hunk #48 succeeded at 1740 (offset 4 lines).
Hunk #49 succeeded at 1783 (offset 4 lines).
Hunk #50 succeeded at 1834 (offset 4 lines).
Hunk #51 succeeded at 1886 (offset 4 lines).
Hunk #52 succeeded at 1915 (offset 4 lines).
Hunk #53 succeeded at 1943 (offset 4 lines).
Hunk #54 succeeded at 1963 (offset 4 lines).
Hunk #55 succeeded at 1976 (offset 4 lines).
Hunk #56 succeeded at 1996 (offset 4 lines).
Hunk #57 succeeded at 2010 (offset 4 lines).
Hunk #58 succeeded at 2038 (offset 4 lines).
Hunk #59 succeeded at 2085 (offset 4 lines).
Hunk #60 succeeded at 2109 (offset 4 lines).
Hunk #61 succeeded at 2157 (offset 4 lines).
Hunk #62 succeeded at 2242 (offset 4 lines).
Hunk #63 succeeded at 2276 (offset 4 lines).
Hunk #64 succeeded at 2302 (offset 4 lines).
Hunk #65 succeeded at 2324 (offset 4 lines).
Hunk #66 succeeded at 2357 (offset 4 lines).
Hunk #67 succeeded at 2378 (offset 4 lines).
Hunk #68 succeeded at 2409 (offset 4 lines).
Hunk #69 succeeded at 2466 (offset 4 lines).
Hunk #70 succeeded at 2489 (offset 4 lines).
Hunk #71 succeeded at 2503 (offset 4 lines).
Hunk #72 succeeded at 2536 (offset 4 lines).
Hunk #73 succeeded at 2563 (offset 4 lines).
Hunk #74 succeeded at 2610 (offset 4 lines).
Hunk #75 succeeded at 2684 (offset 4 lines).
Hunk #76 succeeded at 2730 (offset 4 lines).
Hunk #77 succeeded at 2769 (offset 4 lines).
Hunk #78 succeeded at 2778 (offset 4 lines).
Hunk #79 succeeded at 2797 (offset 4 lines).
Hunk #80 succeeded at 2832 (offset 4 lines).
Hunk #81 succeeded at 2863 (offset 4 lines).
Hunk #82 succeeded at 2877 (offset 4 lines).
Hunk #83 succeeded at 2901 (offset 4 lines).
Hunk #84 succeeded at 2939 (offset 4 lines).
Hunk #85 succeeded at 2970 (offset 4 lines).
Hunk #86 succeeded at 2993 (offset 4 lines).
Hunk #87 succeeded at 3009 (offset 4 lines).
Hunk #88 succeeded at 3146 (offset 4 lines).
Hunk #89 succeeded at 3438 (offset 4 lines).
Hunk #90 succeeded at 3461 (offset 4 lines).
Hunk #91 succeeded at 3575 (offset 4 lines).
Hunk #92 succeeded at 3584 (offset 4 lines).
Hunk #93 succeeded at 3593 (offset 4 lines).
Hunk #94 succeeded at 3622 (offset 4 lines).
Hunk #95 succeeded at 3651 (offset 4 lines).
Hunk #96 succeeded at 3662 (offset 4 lines).
Hunk #97 succeeded at 3677 (offset 4 lines).
Hunk #98 succeeded at 3697 (offset 4 lines).
Hunk #99 succeeded at 3711 (offset 4 lines).
Hunk #100 succeeded at 3720 (offset 4 lines).
Hunk #101 succeeded at 3748 (offset 4 lines).
Hunk #102 succeeded at 3763 (offset 4 lines).
Hunk #103 succeeded at 3773 (offset 4 lines).
Hunk #104 succeeded at 3800 (offset 4 lines).
Hunk #105 succeeded at 3836 (offset 4 lines).
Hunk #106 succeeded at 3892 (offset 4 lines).
Hunk #107 succeeded at 3920 (offset 4 lines).
Hunk #108 succeeded at 3951 (offset 4 lines).
Hunk #109 succeeded at 3972 (offset 4 lines).
Hunk #110 succeeded at 4127 (offset 4 lines).
Hunk #111 succeeded at 4138 (offset 4 lines).
Hunk #112 succeeded at 4153 (offset 4 lines).
Hunk #113 succeeded at 4164 (offset 4 lines).
Hunk #114 succeeded at 4180 (offset 4 lines).
Hunk #115 succeeded at 4201 (offset 4 lines).
Hunk #116 succeeded at 4318 (offset 4 lines).
Hunk #117 succeeded at 4421 (offset 4 lines).
Hunk #118 succeeded at 4440 (offset 4 lines).
Hunk #119 succeeded at 4451 (offset 4 lines).
Hunk #120 succeeded at 4665 (offset 4 lines).
Hunk #121 succeeded at 6007 (offset 4 lines).
Hunk #122 FAILED at 6024.
Hunk #123 succeeded at 6079 (offset 5 lines).
Hunk #124 succeeded at 6090 (offset 5 lines).
4 out of 124 hunks FAILED -- saving rejects to file kernel/sched.c.rej
patching file fs/proc/array.c
patching file include/linux/sysctl.h
patching file kernel/exit.c
patching file kernel/sysctl.c
patching file include/linux/init_task.h
patching file block/Kconfig.iosched
patching file include/linux/ioprio.h
patching file mm/page-writeback.c
patching file arch/ia64/configs/tiger_defconfig
patching file arch/ia64/configs/zx1_defconfig
patching file arch/ppc/configs/common_defconfig
patching file arch/ppc/configs/pmac_defconfig
patching file kernel/Kconfig.hz
patching file Documentation/sysctl/vm.txt
patching file include/linux/swap.h
patching file init/Kconfig
patching file mm/Makefile
patching file mm/swap.c
patching file mm/swap_prefetch.c
patching file mm/swap_state.c
patching file mm/vmscan.c
patching file include/linux/mm_inline.h
patching file include/linux/swap-prefetch.h
patching file include/linux/mmzone.h
patching file mm/page_alloc.c
patching file fs/buffer.c
patching file kernel/power/disk.c
patching file drivers/block/loop.c
patching file fs/mpage.c
patching file fs/nfsd/vfs.c
patching file include/linux/fs.h
patching file include/linux/mm.h
patching file include/linux/page-flags.h
patching file include/linux/radix-tree.h
patching file include/linux/writeback.h
patching file lib/radix-tree.c
patching file mm/Kconfig
patching file mm/filemap.c
patching file mm/memory.c
patching file mm/readahead.c
patching file Documentation/DocBook/Makefile
patching file Makefile
Hunk #1 FAILED at 1.
1 out of 20 hunks FAILED -- saving rejects to file Makefile.rej
patching file arch/arm/Makefile
patching file arch/arm/boot/Makefile
patching file arch/arm/boot/bootp/Makefile
patching file arch/arm26/Makefile
patching file arch/arm26/boot/Makefile
patching file arch/i386/Makefile
patching file arch/ia64/Makefile
patching file arch/m32r/Makefile
patching file arch/powerpc/Makefile
patching file arch/ppc/Makefile
patching file arch/ppc/boot/Makefile
patching file arch/ppc/boot/openfirmware/Makefile
patching file arch/sh/Makefile
patching file arch/um/Makefile
patching file arch/x86_64/Makefile
patching file scripts/Kbuild.include
patching file scripts/Makefile.build
patching file scripts/Makefile.clean
patching file scripts/Makefile.modinst
patching file scripts/Makefile.modpost
patching file scripts/kconfig/Makefile
patching file scripts/kconfig/lxdialog/Makefile
patching file scripts/package/Makefile
patching file arch/i386/kernel/cpu/cpufreq/speedstep-smi.c
Reversed (or previously applied) patch detected!  Assume -R? [n]

```

What should I do? Thanks!

---

### Post by oxEz on 2006-04-10
[QUOTE=Dropknee]Dont know why I dont have in "Device drivers" the opcion IO Schedulers.

anyone have this same prob??[/QUOTE]

Don't go in Devices Drivers first, go in "Block layers". I looked in the .config file, and it's where I learned where IO schedulers were hidden.

---

### Post by sYs^ on 2006-04-10
[QUOTE=IsSuE]i tried compiling the source, but i always get an error when i try to install the created .deb package:
```

Richte kernel-image-2.6.16-cks3 ein (kiwiv1) ...
Cannot find /lib/modules/2.6.16-cks3
Failed to create initrd image.
dpkg: Fehler beim Bearbeiten von kernel-image-2.6.16-cks3 (--install):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 kernel-image-2.6.16-cks3

```
sorry that it is in german, but the main error is in english[/QUOTE]

Is that directory exists? /lib/modules/2.6.16-cks3

---

### Post by IsSuE on 2006-04-10
the .deb file creates a dir called 2.6.16-cks3kiwiv1. i tried removing the kiwiv1 and reinstalling the .deb, that works, but if i reboot, modprobe complains about not finding the modules...
strange thing

---

### Post by sYs^ on 2006-04-10
try something like this:

```
cd /boot/
sudo mkinitrd -o /boot/initrd.img-2.6.16-cks3 2.6.16-cks3kiwiv1
```

Do not rename the module directory after compiling the kernel.
I'm not sure it'll help but it worth a try.

---

### Post by mechatronic on 2006-04-10
This is my problem when I build 2.6.16.2:
> 
make-kpkg -initrd --revision=2 kernel_image
.......<some things>.....
kernel/sched.c: In function â€˜sched_initâ€™:
kernel/sched.c:6031: error: â€˜arrayâ€™ undeclared (first use in this function)
kernel/sched.c:6031: error: (Each undeclared identifier is reported only once
kernel/sched.c:6031: error: for each function it appears in.)
kernel/sched.c:6031: error: â€˜struct runqueueâ€™ has no member named â€˜arraysâ€™
kernel/sched.c:6032: error: â€˜kâ€™ undeclared (first use in this function)
make[2]: *** [kernel/sched.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16.2'
make: *** [stamp-build] Error 2

I'm newbie:confused:  and I see number 6031](*,) ... How can I solve them? Thanks.

---

### Post by R3linquish3r on 2006-04-10
Well I managed to get it running this time but I dont have splash (didnt read the post later about how to get it) and my wireless doesnt work. Is there a way I can get splash working without re-compiling?

---

### Post by xXx 0wn3d xXx on 2006-04-10
[QUOTE=R3linquish3r]Well I managed to get it running this time but I dont have splash (didnt read the post later about how to get it) and my wireless doesnt work. Is there a way I can get splash working without re-compiling?[/QUOTE]
Do you really need the usplash ? Anyway look under troubleshooting for a way to get the wifi to work.

---

### Post by R3linquish3r on 2006-04-10
i like usplash :P wanna know when something fails to load personally.

---

### Post by R3linquish3r on 2006-04-10
i dont think that way wil help me because u still need to download the headers for that kernel in uname -r. im not on the net on that kernel.....

---

### Post by atlas95 on 2006-04-10
[QUOTE=Eazy©]Think you need to do this: [http://doc.gwos.org/index.php/Mount_filesystem_new_kernel](http://doc.gwos.org/index.php/Mount_filesystem_new_kernel)
in order to mount your local filesystem. When I compiled kernel 2.6.15 this worked anyway. Haven't tested with the latest kernel. So I'm afraid you have to compile again.[/QUOTE]
Yes I thinks It is that !
Thanks you, I will retry ;) !

---

### Post by R3linquish3r on 2006-04-10
I just instaled ndiswrapper (went downstairs and plugged in) and i rebooted after isntall and my wireless card still isnt showing up.... incase its needed it is a linksys wireless g card.

---

### Post by xXx 0wn3d xXx on 2006-04-10
[QUOTE=mechatronic]This is my problem when I build 2.6.16.2:

I'm newbie:confused:  and I see number 6031](*,) ... How can I solve them? Thanks.[/QUOTE]
Try redownloading the kernel and patch. I had that error the first time I tried to compile it but I just redownloaded the patch and the kernel and the install returned no errors. The kernel works great.

---

### Post by rajesh on 2006-04-10
[QUOTE=mechatronic]This is my problem when I build 2.6.16.2:

I'm newbie:confused:  and I see number 6031](*,) ... How can I solve them? Thanks.[/QUOTE]

I am getting compilation errors in sched.h also. My error is 

  /include/linux/sched.h:483: error: "SCHED_LOAD_SCALE" undeclared (first use in this function). 

Any pointers on how to solve this ?
Thanks

---

### Post by R3linquish3r on 2006-04-10
Quote:
Originally Posted by Thios
Hi... Would anyone happen to know how to enable iptables support for the 2.6.16-ck3 kernel? Firestarter won't start without it...


Iptables starts but firestarter doesn't reconize it. Youb don't need firestarter anyway.


If you can find a fix for that it would be cool :) i like having firestarter just so i no whats going on :)

---

### Post by dcstar on 2006-04-10
> **MasterChief1234]I just finished compiling the newest 2.6.16 kernel from kernel.org and I am getting much better performance. In what follows, I will show you how to compile and configure the latest kernel. I don't have a splash screen at start up but the kernel works great. It is much faster.  said:**
> 12. Now we are going to import your current kernel configuration:[/COLOR]

[COLOR="Blue"]13. Now import it: Make sure to replace the kernel version in this following command from the one from uname -r.[/COLOR]

[COLOR="Blue"]14. Configure the kernel:[/COLOR]
......
And a little tip for anyone who makes a few too many modifications and ends up with a compiled kernel that won't boot:

Delete the .configure file created by **make xconfig**, and run this again to start afresh (don't ask me how I know to do this.....   :oops:  )

---

### Post by Skarjoko on 2006-04-10
Ok i'm not sure whats wrong, but this happened with both 2.6.14 and 2.6.16 kernels, when i'm packaging them.

My laptop just shuts down. I'm guessing its near the end, and it suddenly just turns off, and its completely gone. This happened with both kernels, trying to make them into a .deb package. Whats wrong?

Thanks in advance.

---

### Post by benplaut on 2006-04-10
i tried this (before the howto, but i did the same basic thing) with dapper and MadWifi, but madwifi module makes the boot hang on 'loading hardware drivers'. Ctrl+C'ing it makes everything work just fine.

I'm using the 2.6.15-686 right now

---

### Post by towsonu2003 on 2006-04-11
I got this a little while after make-kpkg -initrd --revision=ck3 kernel_image

```
kernel/sched.c: In function &#8216;sched_init&#8217;:
kernel/sched.c:6031: error: &#8216;array&#8217; undeclared (first use in this function)
kernel/sched.c:6031: error: (Each undeclared identifier is reported only once
kernel/sched.c:6031: error: for each function it appears in.)
kernel/sched.c:6031: error: &#8216;struct runqueue&#8217; has no member named &#8216;arrays&#8217;
kernel/sched.c:6032: error: &#8216;k&#8217; undeclared (first use in this function)
make[2]: *** [kernel/sched.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16.2ck3'
make: *** [stamp-build] Error 2
root@bla:/usr/src/linux#

```
any idea why this might be?

---

### Post by mechatronic on 2006-04-11
Ok! I have compiled kernel 2.6.16.3 from kernel.org. It's cool, as fast as a rabbit, but no splash screen. I hope to found the way to solve soon...

---

### Post by xXx 0wn3d xXx on 2006-04-11
[QUOTE=mechatronic]Ok! I have compiled kernel 2.6.16.3 from kernel.org. It's cool, as fast as a rabbit, but no splash screen. I hope to found the way to solve soon...[/QUOTE]
I'm glad it worked for someone :) Is your internet any faster to ? It seems alot faster to me.

---

### Post by towsonu2003 on 2006-04-11
For people having troubles compiling the kernel:
The ck patch website says you are supposed to use 2.6.16 as base. I just found out that this means you are supposed to download **2.6.16**, not 2.6.16.x and patch ckx (x-> **4** as of today, because the latest stable kernel is 2.6.16.**4**) that. 
The OP might wanna specify that in the original howto ;)

the append -R and sched error seem to occur because we (I) were applying the patch (which adds features of 2.6.16.x + ck features **to** 2.6.16) to 2.6.16.x (double patching and thus breaking things)... 

Sorry for the bold stuff. It took me a day to understand this.

---

### Post by Harold P on 2006-04-11
I keep on getting things like this, and it's been going for about a two hours.

et/ipv4/ipvs/ip_vs_lblcr.o
  CC [M]  net/ipv4/ipvs/ip_vs_dh.o
  CC [M]  net/ipv4/ipvs/ip_vs_sh.o
  CC [M]  net/ipv4/ipvs/ip_vs_sed.o
  CC [M]  net/ipv4/ipvs/ip_vs_nq.o
  CC [M]  net/ipv4/ipvs/ip_vs_ftp.o
  CC [M]  net/ipv4/netfilter/ip_conntrack_standalone.o
  CC [M]  net/ipv4/netfilter/ip_conntrack_core.o
  CC [M]  net/ipv4/netfilter/ip_conntrack_proto_generic.o
  CC [M]  net/ipv4/netfilter/ip_conntrack_proto_tcp.o
  CC [M]  net/ipv4/netfilter/ip_conntrack_proto_udp.o
  CC [M]  net/ipv4/netfilter/ip_conntrack_proto_icmp.o
  LD [M]  net/ipv4/netfilter/ip_conntrack.o
  CC [M]  net/ipv4/netfilter/ip_conntrack_proto_sctp.o
  CC [M]  net/ipv4/netfilter/ip_conntrack_amanda.o


Is it almost done?

---

### Post by towsonu2003 on 2006-04-11
don't worry, it's gonna go like that for a while. you're good as long as it doesn't crap out with some error.

---

### Post by Harold P on 2006-04-11
Alright, thanks. I thought it was just looping or something, and you can't really check back because terminal only shows so many lines...

---

### Post by towsonu2003 on 2006-04-11
[QUOTE=Harold P]Alright, thanks. I thought it was just looping or something, and you can't really check back because terminal only shows so many lines...[/QUOTE]
you're welcome. I guess those are the name of the modules it just built or something. good luck. now, I'm gonna reboot mine and see if I'll survive ;)

---

### Post by Harold P on 2006-04-11
Haha, 

root@ubuntu:/usr/src# sudo dpkg -i kernel-image-2.6.16-cks3_ck3_i386.deb
Selecting previously deselected package kernel-image-2.6.16-cks3.
(Reading database ... 95616 files and directories currently installed.)
Unpacking kernel-image-2.6.16-cks3 (from kernel-image-2.6.16-cks3_ck3_i386.deb) ...
Setting up kernel-image-2.6.16-cks3 (ck3) ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.16-cks3
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


root@ubuntu:/usr/src#


It's done! :)

---

### Post by Harold P on 2006-04-11
Sorry for the double post, but it's absolutely great. It works fine for me. I was a little concerned when I didn't see anything after it booted the Kernel. Black screens are scary. As soon as I got into the GUI I was happy. Logged, and everything pretty much loaded twice as fast... (Panels, Gaim, GDesklets, etc.)

I definately recommend to upgrade. :)

---

### Post by towsonu2003 on 2006-04-11
weird. I rebooted (and survived), but I got too many errors about "you should upgrade your iptables or your kernel now" when I shut down the computer -> so I chickened out bc I like my iptables (firewall, firestarter) and uninstalled the new kernel. something is wrong/missing in the howto, but I don't know what... may be you need to recompile iptables too?? am clueless thought. [I used ubuntu's config w/ mentioned tweaks and ck4 w/ 2.6.16 source.] weird stuff...

---

### Post by massivevoid on 2006-04-11
When using this new kernel, it converted back to the default video driver. ](*,) 

Other than that, I noticed an increase in speed. :)

---

### Post by xXx 0wn3d xXx on 2006-04-11
[QUOTE=massivevoid]When using this new kernel, it converted back to the default video driver. ](*,) 

Other than that, I noticed an increase in speed. :)[/QUOTE]
sudo dpkg-reconfigure xserver-xorg

then select the driver.

---

### Post by dcstar on 2006-04-11
[QUOTE=massivevoid]When using this new kernel, it converted back to the default video driver. ](*,) 

Other than that, I noticed an increase in speed. :)[/QUOTE]
I had to recompile my Via and DRM modules with the new headers to restore my Via Unichrome Direct Rendering, after that everything worked fine.

---

### Post by ignorance on 2006-04-11
well if any reads the lines that the kernel shows someone should have figured out that he isn't giving a splash screen because he can't find one.
```
Searching for splash image... none found, skipping...
```

here's a link how to get one, duno if it works will try for myself to later:
[http://www.ubuntuforums.org/showthread.php?t=83009&highlight=bluebuntu](http://www.ubuntuforums.org/showthread.php?t=83009&highlight=bluebuntu)

---

### Post by Rizado on 2006-04-12
ck4 is out, but ck3 is still the one on the main page. And in the announce it says it's the patches from 2.6.16.2?
Then what is ck1, 2 and 3? 2.6.16.4 is out...

[http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/)

---

### Post by dcstar on 2006-04-12
[QUOTE=dcstar]I had to recompile my Via and DRM modules with the new headers to restore my Via Unichrome Direct Rendering, after that everything worked fine.[/QUOTE]
And of course, I found that I could have these items compiled in my new kernel anyway.... so I did it!

Also removed many (many) items from the configuration that were not necessary for my setup, this cut down the compile time as well as the size of the  created kernel - well worth the effort if anybody can be bothered (and knows what they are doing.......)

---

### Post by dcstar on 2006-04-12
> **MasterChief1234]I just finished compiling the newest 2.6.16 kernel from kernel.org and I am getting much better performance. In what follows, I will show you how to compile and configure the latest kernel. I don't have a splash screen at start up but the kernel works great. It is much faster.  said:**
> 1. Download the latest stable kernel and it's performance patch:[/COLOR]
[ The latest kernel ](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.tar.bz2)
[ Latest Kernel Patch ](http://ck.kolivas.org/patches/2.6/2.6.16/2.6.16-ck3/patch-2.6.16-cks3.bz2)
.......
I note from the patch README that the ck**s** patches are optimised for Servers, where the ck patches are for Desktops.

Perhaps in future people should choose the desktop version?

---

### Post by towsonu2003 on 2006-04-12
> **dxdemetriou]Another problem..  said:**
> 

The kernel defined by this directory of header files does not have the same
address space size as your running kernel.
----------------------------------
I have checked all kernel directories in /usr/src/linux(version)/include, but nothing
this is vmware? uninstall and reinstall vmware...

---

### Post by towsonu2003 on 2006-04-12
[QUOTE=sYs^]Hi!

Is this patch working with the latest  version kernel? (2.6.16.2)?
When I tried to apply the patch I got these lines:

```
sudo bzcat /home/dani/patch-2.6.16-cks3.bz2| patch -p1
patching file include/linux/sched.h
patching file kernel/sched.c
Hunk #6 FAILED at 153.
Hunk #7 succeeded at 203 (offset 1 line).
Hunk #8 succeeded at 212 (offset 1 line).
Hunk #9 succeeded at 222 (offset 1 line).
Hunk #10 succeeded at 248 (offset 1 line).
Hunk #11 succeeded at 270 (offset 1 line).
Hunk #12 succeeded at 407 (offset 1 line).
Hunk #13 succeeded at 445 (offset 1 line).
Hunk #14 succeeded at 504 (offset 1 line).
Hunk #15 succeeded at 638 (offset 1 line).
Hunk #16 succeeded at 647 (offset 1 line).
Hunk #17 succeeded at 831 (offset 1 line).
Hunk #18 succeeded at 844 (offset 1 line).
Hunk #19 succeeded at 873 (offset 1 line).
Hunk #20 succeeded at 910 (offset 1 line).
Hunk #21 succeeded at 930 (offset 1 line).
Hunk #22 succeeded at 938 (offset 1 line).
Hunk #23 succeeded at 968 (offset 1 line).
Hunk #24 succeeded at 993 (offset 1 line).
Hunk #25 succeeded at 1005 (offset 1 line).
Hunk #26 succeeded at 1014 (offset 1 line).
Hunk #27 succeeded at 1051 (offset 1 line).
Hunk #28 succeeded at 1105 (offset 1 line).
Hunk #29 succeeded at 1116 (offset 1 line).
Hunk #30 succeeded at 1138 (offset 1 line).
Hunk #31 succeeded at 1190 (offset 1 line).
Hunk #32 succeeded at 1213 (offset 1 line).
Hunk #33 succeeded at 1257 (offset 1 line).
Hunk #34 succeeded at 1274 (offset 1 line).
Hunk #35 succeeded at 1319 (offset 1 line).
Hunk #36 succeeded at 1365 (offset 1 line).
Hunk #37 succeeded at 1374 (offset 1 line).
Hunk #38 succeeded at 1385 (offset 1 line).
Hunk #39 succeeded at 1415 (offset 1 line).
Hunk #40 succeeded at 1432 (offset 1 line).
Hunk #41 succeeded at 1442 (offset 1 line).
Hunk #42 succeeded at 1452 (offset 1 line).
Hunk #43 succeeded at 1463 (offset 1 line).
Hunk #44 succeeded at 1493 (offset 1 line).
Hunk #45 succeeded at 1675 with fuzz 2 (offset 4 lines).
Hunk #46 FAILED at 1689.
Hunk #47 FAILED at 1725.
Hunk #48 succeeded at 1740 (offset 4 lines).
Hunk #49 succeeded at 1783 (offset 4 lines).
Hunk #50 succeeded at 1834 (offset 4 lines).
Hunk #51 succeeded at 1886 (offset 4 lines).
Hunk #52 succeeded at 1915 (offset 4 lines).
Hunk #53 succeeded at 1943 (offset 4 lines).
Hunk #54 succeeded at 1963 (offset 4 lines).
Hunk #55 succeeded at 1976 (offset 4 lines).
Hunk #56 succeeded at 1996 (offset 4 lines).
Hunk #57 succeeded at 2010 (offset 4 lines).
Hunk #58 succeeded at 2038 (offset 4 lines).
Hunk #59 succeeded at 2085 (offset 4 lines).
Hunk #60 succeeded at 2109 (offset 4 lines).
Hunk #61 succeeded at 2157 (offset 4 lines).
Hunk #62 succeeded at 2242 (offset 4 lines).
Hunk #63 succeeded at 2276 (offset 4 lines).
Hunk #64 succeeded at 2302 (offset 4 lines).
Hunk #65 succeeded at 2324 (offset 4 lines).
Hunk #66 succeeded at 2357 (offset 4 lines).
Hunk #67 succeeded at 2378 (offset 4 lines).
Hunk #68 succeeded at 2409 (offset 4 lines).
Hunk #69 succeeded at 2466 (offset 4 lines).
Hunk #70 succeeded at 2489 (offset 4 lines).
Hunk #71 succeeded at 2503 (offset 4 lines).
Hunk #72 succeeded at 2536 (offset 4 lines).
Hunk #73 succeeded at 2563 (offset 4 lines).
Hunk #74 succeeded at 2610 (offset 4 lines).
Hunk #75 succeeded at 2684 (offset 4 lines).
Hunk #76 succeeded at 2730 (offset 4 lines).
Hunk #77 succeeded at 2769 (offset 4 lines).
Hunk #78 succeeded at 2778 (offset 4 lines).
Hunk #79 succeeded at 2797 (offset 4 lines).
Hunk #80 succeeded at 2832 (offset 4 lines).
Hunk #81 succeeded at 2863 (offset 4 lines).
Hunk #82 succeeded at 2877 (offset 4 lines).
Hunk #83 succeeded at 2901 (offset 4 lines).
Hunk #84 succeeded at 2939 (offset 4 lines).
Hunk #85 succeeded at 2970 (offset 4 lines).
Hunk #86 succeeded at 2993 (offset 4 lines).
Hunk #87 succeeded at 3009 (offset 4 lines).
Hunk #88 succeeded at 3146 (offset 4 lines).
Hunk #89 succeeded at 3438 (offset 4 lines).
Hunk #90 succeeded at 3461 (offset 4 lines).
Hunk #91 succeeded at 3575 (offset 4 lines).
Hunk #92 succeeded at 3584 (offset 4 lines).
Hunk #93 succeeded at 3593 (offset 4 lines).
Hunk #94 succeeded at 3622 (offset 4 lines).
Hunk #95 succeeded at 3651 (offset 4 lines).
Hunk #96 succeeded at 3662 (offset 4 lines).
Hunk #97 succeeded at 3677 (offset 4 lines).
Hunk #98 succeeded at 3697 (offset 4 lines).
Hunk #99 succeeded at 3711 (offset 4 lines).
Hunk #100 succeeded at 3720 (offset 4 lines).
Hunk #101 succeeded at 3748 (offset 4 lines).
Hunk #102 succeeded at 3763 (offset 4 lines).
Hunk #103 succeeded at 3773 (offset 4 lines).
Hunk #104 succeeded at 3800 (offset 4 lines).
Hunk #105 succeeded at 3836 (offset 4 lines).
Hunk #106 succeeded at 3892 (offset 4 lines).
Hunk #107 succeeded at 3920 (offset 4 lines).
Hunk #108 succeeded at 3951 (offset 4 lines).
Hunk #109 succeeded at 3972 (offset 4 lines).
Hunk #110 succeeded at 4127 (offset 4 lines).
Hunk #111 succeeded at 4138 (offset 4 lines).
Hunk #112 succeeded at 4153 (offset 4 lines).
Hunk #113 succeeded at 4164 (offset 4 lines).
Hunk #114 succeeded at 4180 (offset 4 lines).
Hunk #115 succeeded at 4201 (offset 4 lines).
Hunk #116 succeeded at 4318 (offset 4 lines).
Hunk #117 succeeded at 4421 (offset 4 lines).
Hunk #118 succeeded at 4440 (offset 4 lines).
Hunk #119 succeeded at 4451 (offset 4 lines).
Hunk #120 succeeded at 4665 (offset 4 lines).
Hunk #121 succeeded at 6007 (offset 4 lines).
Hunk #122 FAILED at 6024.
Hunk #123 succeeded at 6079 (offset 5 lines).
Hunk #124 succeeded at 6090 (offset 5 lines).
4 out of 124 hunks FAILED -- saving rejects to file kernel/sched.c.rej
patching file fs/proc/array.c
patching file include/linux/sysctl.h
patching file kernel/exit.c
patching file kernel/sysctl.c
patching file include/linux/init_task.h
patching file block/Kconfig.iosched
patching file include/linux/ioprio.h
patching file mm/page-writeback.c
patching file arch/ia64/configs/tiger_defconfig
patching file arch/ia64/configs/zx1_defconfig
patching file arch/ppc/configs/common_defconfig
patching file arch/ppc/configs/pmac_defconfig
patching file kernel/Kconfig.hz
patching file Documentation/sysctl/vm.txt
patching file include/linux/swap.h
patching file init/Kconfig
patching file mm/Makefile
patching file mm/swap.c
patching file mm/swap_prefetch.c
patching file mm/swap_state.c
patching file mm/vmscan.c
patching file include/linux/mm_inline.h
patching file include/linux/swap-prefetch.h
patching file include/linux/mmzone.h
patching file mm/page_alloc.c
patching file fs/buffer.c
patching file kernel/power/disk.c
patching file drivers/block/loop.c
patching file fs/mpage.c
patching file fs/nfsd/vfs.c
patching file include/linux/fs.h
patching file include/linux/mm.h
patching file include/linux/page-flags.h
patching file include/linux/radix-tree.h
patching file include/linux/writeback.h
patching file lib/radix-tree.c
patching file mm/Kconfig
patching file mm/filemap.c
patching file mm/memory.c
patching file mm/readahead.c
patching file Documentation/DocBook/Makefile
patching file Makefile
Hunk #1 FAILED at 1.
1 out of 20 hunks FAILED -- saving rejects to file Makefile.rej
patching file arch/arm/Makefile
patching file arch/arm/boot/Makefile
patching file arch/arm/boot/bootp/Makefile
patching file arch/arm26/Makefile
patching file arch/arm26/boot/Makefile
patching file arch/i386/Makefile
patching file arch/ia64/Makefile
patching file arch/m32r/Makefile
patching file arch/powerpc/Makefile
patching file arch/ppc/Makefile
patching file arch/ppc/boot/Makefile
patching file arch/ppc/boot/openfirmware/Makefile
patching file arch/sh/Makefile
patching file arch/um/Makefile
patching file arch/x86_64/Makefile
patching file scripts/Kbuild.include
patching file scripts/Makefile.build
patching file scripts/Makefile.clean
patching file scripts/Makefile.modinst
patching file scripts/Makefile.modpost
patching file scripts/kconfig/Makefile
patching file scripts/kconfig/lxdialog/Makefile
patching file scripts/package/Makefile
patching file arch/i386/kernel/cpu/cpufreq/speedstep-smi.c
Reversed (or previously applied) patch detected!  Assume -R? [n]

```

What should I do? Thanks![/QUOTE]
patch and compile 2.6.16 instead of 2.6.16.2

---

### Post by towsonu2003 on 2006-04-12
[QUOTE=mechatronic]This is my problem when I build 2.6.16.2:

I'm newbie:confused:  and I see number 6031](*,) ... How can I solve them? Thanks.[/QUOTE]
use 2.6.16 to compile (sorry for me being repetitious).

---

### Post by towsonu2003 on 2006-04-12
[QUOTE=Rizado]ck4 is out, but ck3 is still the one on the main page. And in the announce it says it's the patches from 2.6.16.2?
Then what is ck1, 2 and 3? 2.6.16.4 is out...

[http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/)[/QUOTE]
you use 2.6.16 as base. ck1 gives you patched 2.6.16.1, ck2 gives 2.6.16.2 etc... so for latest kernel, you download 2.6.16, check the x in 2.6.16.x in kernel.org main page (latest), and you download ckx as your patch. that's my understanding of this thing.

---

### Post by decebal on 2006-04-12
I compiled and installed the kernel apparently without problems but it killed my fglrx driver and no matter what I did (reinstall, reconfigure, etc) I couldn't get rid of the mesa thing!
The other problem I had was with my fat partition - it just wouldn't let me mount it at all with the new kernel - it would say "device already mounted or busy" and if I tried to unmount it would say "device not mounted".

On the other hand, I didn't notice any major speed improvement with the new kernel - but I'm on a fast machine and the "old" kernel was already pretty fast.

And by the way, if you want to make the splash image work with the new kernel all you need to do is reinstall usplash in synaptic.

So .... back to 2.6.15 for me.

---

### Post by xXx 0wn3d xXx on 2006-04-12
ok, I linked to the desktop patch. Should I rewrite the tutorial for the newest kernel or should I wait until a new kernel comes out ?

---

### Post by massivevoid on 2006-04-12
How do you apply the cks4 patch?

```
root@crafford:/usr/src/linux# sudo bzcat /home/william/patch-2.6.16-cks4.bz2| patch -p1
patching file include/linux/sched.h
Reversed (or previously applied) patch detected!  Assume -R? [n]

```

---

### Post by ludzter on 2006-04-12
Hi and thnx for a nice howto. :D 

But here comes som newbie questions:
If i take just 2.6.16.4 without patch, am i in trubble then? (like always)
Why install 2.6.16, when 2.6.16.4 is out there?
what is the patch doing?

Just trying to understand what i am doing, not always so esay ;) 

//Ludz

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=ludzter]Hi and thnx for a nice howto. :D 

But here comes som newbie questions:
If i take just 2.6.16.4 without patch, am i in trubble then? (like always)
Why install 2.6.16, when 2.6.16.4 is out there?
what is the patch doing?

Just trying to understand what i am doing, not always so esay ;) 

//Ludz[/QUOTE]
The patch is improving proformance. You can use the 2.6.16.4 kernel without the patch. Also, this tutorial is about 4 days old and 2.6.16.4 was just released. I'm getting ready to compile and install it right now. You can use my tutorial for the new kernel. Just replace the 2.6.16 name in the command with the 2.6.16.4 one.

---

### Post by ludzter on 2006-04-12
ok, nice. i am about to reinstall my system anyway, so i will give it a try. Thanks again for the nice howto and the fast replay.

Now time to break my system ;)

---

### Post by xXx 0wn3d xXx on 2006-04-12
omg ! A new kernel was just released ! Wow..5 minutes ago it was 2.6.16.4.

---

### Post by gabng on 2006-04-12
Hi, I've been using Ubuntu for about a week now, and I've just done my very first kernel compile and intall, which was a success!  Thanks to MasterChief1234 :).

Now I'm running on 2.6.16 with ck4 patch but my wireless card isn't showing up in Networking.  I tried lspci and it does recognize it as
Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
, which is correct.
So my question is how can I get it to show up in Networks so I can activate it and get online with it again?

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=gabng]Hi, I've been using Ubuntu for about a week now, and I've just done my very first kernel compile and intall, which was a success!  Thanks to MasterChief1234 :).

Now I'm running on 2.6.16 with ck4 patch but my wireless card isn't showing up in Networking.  I tried lspci and it does recognize it as
Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
, which is correct.
So my question is how can I get it to show up in Networks so I can activate it and get online with it again?[/QUOTE]
Look under Troubleshooting ;)

---

### Post by massivevoid on 2006-04-12
[QUOTE=massivevoid]How do you apply the cks4 patch?

```
root@crafford:/usr/src/linux# sudo bzcat /home/william/patch-2.6.16-cks4.bz2| patch -p1
patching file include/linux/sched.h
Reversed (or previously applied) patch detected!  Assume -R? [n]

```[/QUOTE]

How do I apply a patch?

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=massivevoid]How do I apply a patch?[/QUOTE]
do just what I said. Sometimes you will need to redownload the kernel + patch and then everything should work.

---

### Post by Ob1 on 2006-04-12
How do i see what my current kernel is?

---

### Post by ErikTheRed on 2006-04-12
Sweet guide, it's always nice to a have a guide to show you how easy compiling a new kernel is.

---

### Post by towsonu2003 on 2006-04-12
no matter what I do, iptables won't work (even when enabled it in xconfig). :-k ](*,) + ndiswrapper won't compile + many device-mapper errors... I guess I'm not ready for this stuff yet...

---

### Post by towsonu2003 on 2006-04-12
[QUOTE=Ob1]How do i see what my current kernel is?[/QUOTE]
uname -r

---

### Post by massivevoid on 2006-04-12
[QUOTE=MasterChief1234]do just what I said. Sometimes you will need to redownload the kernel + patch and then everything should work.[/QUOTE]

So I have to recompile the kernel over again, just to apply the new patch?

---

### Post by towsonu2003 on 2006-04-12
[QUOTE=massivevoid]So I have to recompile the kernel over again, just to apply the new patch?[/QUOTE]
yep

---

### Post by massivevoid on 2006-04-12
[QUOTE=towsonu2003]yep[/QUOTE]

Ok, I got it now. Thanks. :D

---

### Post by Justbill on 2006-04-12
So, I gave this a whirl. Here is my output, after I ran make-kpkg -initrd --revision=ck3 kernel_image:

if [ -r System.map -a -x /sbin/depmod ]; then /sbin/depmod -ae -F System.map -b /usr/src/linux/debian/tmp-image -r 2.6.16-cks4; fi
make[2]: Leaving directory `/usr/src/linux-2.6.16ck3'
test ! -e debian/tmp-image/lib/modules/2.6.16-cks4/source ||     \
   mv debian/tmp-image/lib/modules/2.6.16-cks4/source ./debian/source-link
test ! -e debian/tmp-image/lib/modules/2.6.16-cks4/build ||     \
   mv debian/tmp-image/lib/modules/2.6.16-cks4/build ./debian/build-link
depmod -q -FSystem.map -b debian/tmp-image 2.6.16-cks4;
test ! -e ./debian/source-link ||                                              \   mv ./debian/source-link debian/tmp-image/lib/modules/2.6.16-cks4/source
test ! -e  ./debian/build-link ||                                              \   mv  ./debian/build-link debian/tmp-image/lib/modules/2.6.16-cks4/build
cp arch/i386/boot/bzImage debian/tmp-image/boot/vmlinuz-2.6.16-cks4
chmod 644 debian/tmp-image/boot/vmlinuz-2.6.16-cks4;
if test -d /usr/src/linux/debian/image.d ; then                             \
             IMAGE_TOP=debian/tmp-image version=2.6.16-cks4      \
                   run-parts --verbose /usr/src/linux/debian/image.d ;      \
         fi
if [ -x debian/post-install ]; then                                    \
        IMAGE_TOP=debian/tmp-image STEM=kernel version=2.6.16-cks4    \
                debian/post-install;                                  \
fi
test ! -s applied_patches || cp applied_patches                        \
                        debian/tmp-image/boot/patches-2.6.16-cks4
test ! -s applied_patches || chmod 644                                 \
                        debian/tmp-image/boot/patches-2.6.16-cks4
test ! -f System.map ||  cp System.map                         \
                        debian/tmp-image/boot/System.map-2.6.16-cks4;
test ! -f System.map ||  chmod 644                             \
                        debian/tmp-image/boot/System.map-2.6.16-cks4;
# For LKCD enabled kernels
test ! -f Kerntypes ||  cp Kerntypes                                   \
                        debian/tmp-image/boot/Kerntypes-2.6.16-cks4
test ! -f Kerntypes ||  chmod 644                                      \
                        debian/tmp-image/boot/Kerntypes-2.6.16-cks4
dpkg-gencontrol -DArchitecture=i386 -isp                   \
                        -pkernel-image-2.6.16-cks4 -Pdebian/tmp-image/
chmod -R og=rX debian/tmp-image
chown -R root:root debian/tmp-image
dpkg --build debian/tmp-image ..
dpkg-deb: building package `kernel-image-2.6.16-cks4' in `../kernel-image-2.6.16-cks4_ck3_i386.deb'.
rm -f -r debian/tmp-image
echo done >  stamp-image
make[1]: Leaving directory `/usr/src/linux-2.6.16ck3'
root@Goliath:/usr/src/linux# dpkg -i kernel-image-2.6.16-cks4
dpkg: error processing kernel-image-2.6.16-cks4 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kernel-image-2.6.16-cks4

of course, it did all the other stuff, this was just the end. Anyhow, I can't seem to install the new kernel. I'm thinking it put it in a directory, and I can't seem to find it (that or I'm just stupid, and shouldn't be trying this). 

Can anyone give me a clue here what to do?

Thanks in advance
Justbill

---

### Post by xXx 0wn3d xXx on 2006-04-12
> **Justbill]So, I gave this a whirl. Here is my output, after I ran make-kpkg -initrd --revision=ck3 kernel_image:

if [ -r System.map -a -x /sbin/depmod ] said:**
> : Leaving directory `/usr/src/linux-2.6.16ck3'
test ! -e debian/tmp-image/lib/modules/2.6.16-cks4/source ||     \
   mv debian/tmp-image/lib/modules/2.6.16-cks4/source ./debian/source-link
test ! -e debian/tmp-image/lib/modules/2.6.16-cks4/build ||     \
   mv debian/tmp-image/lib/modules/2.6.16-cks4/build ./debian/build-link
depmod -q -FSystem.map -b debian/tmp-image 2.6.16-cks4;
test ! -e ./debian/source-link ||                                              \   mv ./debian/source-link debian/tmp-image/lib/modules/2.6.16-cks4/source
test ! -e  ./debian/build-link ||                                              \   mv  ./debian/build-link debian/tmp-image/lib/modules/2.6.16-cks4/build
cp arch/i386/boot/bzImage debian/tmp-image/boot/vmlinuz-2.6.16-cks4
chmod 644 debian/tmp-image/boot/vmlinuz-2.6.16-cks4;
if test -d /usr/src/linux/debian/image.d ; then                             \
             IMAGE_TOP=debian/tmp-image version=2.6.16-cks4      \
                   run-parts --verbose /usr/src/linux/debian/image.d ;      \
         fi
if [ -x debian/post-install ]; then                                    \
        IMAGE_TOP=debian/tmp-image STEM=kernel version=2.6.16-cks4    \
                debian/post-install;                                  \
fi
test ! -s applied_patches || cp applied_patches                        \
                        debian/tmp-image/boot/patches-2.6.16-cks4
test ! -s applied_patches || chmod 644                                 \
                        debian/tmp-image/boot/patches-2.6.16-cks4
test ! -f System.map ||  cp System.map                         \
                        debian/tmp-image/boot/System.map-2.6.16-cks4;
test ! -f System.map ||  chmod 644                             \
                        debian/tmp-image/boot/System.map-2.6.16-cks4;
# For LKCD enabled kernels
test ! -f Kerntypes ||  cp Kerntypes                                   \
                        debian/tmp-image/boot/Kerntypes-2.6.16-cks4
test ! -f Kerntypes ||  chmod 644                                      \
                        debian/tmp-image/boot/Kerntypes-2.6.16-cks4
dpkg-gencontrol -DArchitecture=i386 -isp                   \
                        -pkernel-image-2.6.16-cks4 -Pdebian/tmp-image/
chmod -R og=rX debian/tmp-image
chown -R root:root debian/tmp-image
dpkg --build debian/tmp-image ..
dpkg-deb: building package `kernel-image-2.6.16-cks4' in `../kernel-image-2.6.16-cks4_ck3_i386.deb'.
rm -f -r debian/tmp-image
echo done >  stamp-image
make[1]: Leaving directory `/usr/src/linux-2.6.16ck3'
root@Goliath:/usr/src/linux# dpkg -i kernel-image-2.6.16-cks4
dpkg: error processing kernel-image-2.6.16-cks4 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kernel-image-2.6.16-cks4

of course, it did all the other stuff, this was just the end. Anyhow, I can't seem to install the new kernel. I'm thinking it put it in a directory, and I can't seem to find it (that or I'm just stupid, and shouldn't be trying this). 

Can anyone give me a clue here what to do?

Thanks in advance
Justbill
look in usr/src/ for the kernel image. It should be something like linux-image-2.16.6cks3_i386. The open terminal and type sudo dpkg -i then drag the kernel image which is a .deb into the terminal and it will automatically put it's location. Then press enter.

---

### Post by Justbill on 2006-04-12
I'm sorry, I didn't quite understand what you meant there. Here is the output from cd /usr/src , and then ls -l :

root@Goliath:/home/bill# cd /usr/src
root@Goliath:/usr/src# ls
kernel-image-2.6.16-cks4_ck3_i386.deb  linux-2.6.16.tar.bz2
linux                                  linux-headers-2.6.12-10
linux-2.6.16ck3                        linux-headers-2.6.12-10-386
root@Goliath:/usr/src# dpkg -i kernel-image-2.6.16-cks_ck3_i386.deb
dpkg: error processing kernel-image-2.6.16-cks_ck3_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kernel-image-2.6.16-cks_ck3_i386.deb
root@Goliath:/usr/src# ls -l
total 54160
-rw-r--r--   1 root src  14534526 2006-04-12 21:55 kernel-image-2.6.16-cks4_ck3_i386.deb
lrwxrwxrwx   1 root src        24 2006-04-12 20:54 linux -> /usr/src/linux-2.6.16ck3
drwxrwxrwx  21 root root     4096 2006-04-12 21:55 linux-2.6.16ck3
-rw-r--r--   1 root src  40845005 2006-04-12 20:51 linux-2.6.16.tar.bz2
drwxr-xr-x  18 root root     4096 2006-04-09 13:23 linux-headers-2.6.12-10
drwxr-xr-x   4 root root     4096 2006-04-09 13:23 linux-headers-2.6.12-10-386
root@Goliath:/usr/src#
 does kernel-image-2.6.16-cks4_ck3_i386.deb need to have permisions changed? and, is that what I want to install?

Thanks 
Justbill

---

### Post by dcstar on 2006-04-13
[QUOTE=Justbill]
.....
 does **kernel-image-2.6.16-cks4_ck3_i386.deb** need to have permisions changed? and, is that what I want to install?

Thanks 
Justbill[/QUOTE]
Just make sure you type the **exact **same .deb name in, or make sure you only have your latest compiled .deb in that directory and type:
```
sudo dpkg -i *deb
```

---

### Post by Phlod on 2006-04-13
I can't make xconfig?  When I try it puts out this perplexing output:

root@zim:/usr/src/linux# make xconfig
scripts/kconfig/qconf arch/i386/Kconfig
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

qconf: cannot connect to X server :0.0
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2

No idea why it wouldn't be able to connect to the server.  It's running, I'm using it right now.

---

### Post by dcstar on 2006-04-13
[QUOTE=MasterChief1234]ok, I linked to the desktop patch. Should I rewrite the tutorial for the newest kernel or should I wait until a new kernel comes out ?[/QUOTE]
Rewrite it so people have to find the latest patch, and then tweak the scripts to use it themselves.

---

### Post by dcstar on 2006-04-13
[QUOTE=Phlod]I can't make xconfig?  When I try it puts out this perplexing output:

root@zim:/usr/src/linux# make xconfig
scripts/kconfig/qconf arch/i386/Kconfig
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

qconf: cannot connect to X server :0.0
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2

No idea why it wouldn't be able to connect to the server.  It's running, I'm using it right now.[/QUOTE]
I believe xconfig is a KDE app, do you have the various kdelibs packages installed?

---

### Post by ludzter on 2006-04-13
I now have about 6 diffrent Kernels in my menu.lst , but how do i completly remove a old or non working kernel, i figure it might be pretty stupid to something wrong here, and have to it all over again.

title		Ubuntu, kernel 2.6.16-cks3 
kernel		/boot/vmlinuz-2.6.16-cks3 
initrd		/boot/initrd.img-2.6.16-cks3

Only these 2 that i have to remove? ill think i need a step by step howto here :-k

---

### Post by Justbill on 2006-04-13
[QUOTE=dcstar]Just make sure you type the **exact **same .deb name in, or make sure you only have your latest compiled .deb in that directory and type:
```
sudo dpkg -i *deb
```[/QUOTE]

Thanks dcstar! One of these days I'll learn to **NOT** try this stuff when half asleep! Thanks for noticing the typo in my last attempt (do I feel stupid).

New Kernel is working great!

Thanks Again!

Justbill

---

### Post by towsonu2003 on 2006-04-13
[QUOTE=MasterChief1234]
[COLOR="Blue"]12. Now we are going to import your current kernel configuration:[/COLOR]

[COLOR="Blue"]13. Now import it: Make sure to replace the kernel version in this following command from the one from uname -r.[/COLOR]

[COLOR="Blue"]14. Configure the kernel:[/COLOR]
[/QUOTE]
It seems the imported /boot/config-blabla is not very "compatible" with the latest kernels. It misses a lot of options originally present in Ubuntu's kernel (the output on the terminal when typed "sudo make xconfig" shows the incompatible arguments in .config I guess). And you have to manually go in there and double check everything (which I can't do, bc I'm clueless :) )

One example is iptables. The new config made from the old one totally misses the iptables configuration in the kernel. With the new kernel, you don't have a firewall anymore. To fix that, check out: [http://ubuntuforums.org/showthread.php?t=151824](http://ubuntuforums.org/showthread.php?t=151824)

---

### Post by xXx 0wn3d xXx on 2006-04-13
[QUOTE=ludzter]I now have about 6 diffrent Kernels in my menu.lst , but how do i completly remove a old or non working kernel, i figure it might be pretty stupid to something wrong here, and have to it all over again.

title		Ubuntu, kernel 2.6.16-cks3 
kernel		/boot/vmlinuz-2.6.16-cks3 
initrd		/boot/initrd.img-2.6.16-cks3

Only these 2 that i have to remove? ill think i need a step by step howto here :-k[/QUOTE]
Synaptic. Then search for kernel and find it. The name should be something like "linux-image-2.6.**.*" Where the * are the name then click the box on the left and select "Remove Completly."

---

### Post by towsonu2003 on 2006-04-13
[QUOTE=MasterChief1234]Synaptic. Then search for kernel and find it. The name should be something like "linux-image-2.6.**.*" Where the * are the name then click the box on the left and select "Remove Completly."[/QUOTE]
just to correct, it will say kernel-image-blabla. Just make sure you're not uninstalling the wrong kernel, and I think you shouldn't uninstall a kernel while you are running on it ;) :P

To make sure you're not removing the kernel you're using, use uname -r.

---

### Post by plush on 2006-04-15
Great thread... however I ran into some problems, which I'm sure are powerpc-related, who knows... I was hoping someone could shed some light on this.

I followed your directions, except I didn't implement the patch or rename the directory, though I don't think that should matter.  After doing "make kpkg-clean", and then the command to "make-kpkg -initrd kernel_image", it starts doing it's thing for quite some time (15-20 min) and then it stops with at the following:


> ld: drivers/built-in.o section .init.text exceeds stub group size
ld: arch/powerpc/kernel/built-in.o section .init.text exceeds stub group size
ld: init/built-in.o section .init.text exceeds stub group size
ld: net/built-in.o section .text exceeds stub group size
ld: drivers/built-in.o section .text exceeds stub group size
ld: block/built-in.o section .text exceeds stub group size
ld: security/built-in.o section .text exceeds stub group size
ld: ipc/built-in.o section .text exceeds stub group size
ld: fs/built-in.o section .text exceeds stub group size
ld: mm/built-in.o section .text exceeds stub group size
ld: kernel/built-in.o section .text exceeds stub group size
ld: arch/powerpc/platforms/built-in.o section .text exceeds stub group size
ld: arch/powerpc/kernel/built-in.o section .text exceeds stub group size
ld: arch/powerpc/kernel/head_64.o section .text exceeds stub group size
drivers/built-in.o: In function `.platinumfb_probe':platinumfb.c:(.text+0x84a0c): undefined reference to `.nvram_read_byte'
:platinumfb.c:(.text+0x84ab0): undefined reference to `.nvram_read_byte'
drivers/built-in.o: In function `.imsttfb_probe':imsttfb.c:(.text+0x88334): undefined reference to `.nvram_read_byte'
:imsttfb.c:(.text+0x88358): undefined reference to `.nvram_read_byte'
drivers/built-in.o: In function `.control_init':controlfb.c:(.init.text+0x52ec): undefined reference to `.nvram_read_byte'
drivers/built-in.o:controlfb.c:(.init.text+0x54dc): more undefined references to `.nvram_read_byte' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.16'
make: *** [stamp-build] Error 2

I used the old config from my config-2.6.15-19-powerpc64-smp.  And I used gconfig.

---

### Post by plush on 2006-04-15
K now it does that right away when I try to type "make-kpkg -initrd kernel_image" again... is it trying to compile from where I left off?  Should I erase everything and start over?

---

### Post by geearf on 2006-04-15
Hello,

I'm using dapper with the 2.6.15 patched for reiser4 and a little tweaked, is this kernel + patchset really better than the almost 'official' one ?

Thanks

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=geearf]Hello,

I'm using dapper with the 2.6.15 patched for reiser4 and a little tweaked, is this kernel + patchset really better than the almost 'official' one ?

Thanks[/QUOTE]
I don't think that you should upgrade. You won't really get that much better performance in my opinion.

---

### Post by geearf on 2006-04-15
Allright then, I will just tweak it a little more, is there any specific patch I should try ?

Thanks

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=geearf]Allright then, I will just tweak it a little more, is there any specific patch I should try ?

Thanks[/QUOTE]
I don't think there is a specific patch you could use but I just compilied the new 2.6.16.5 kernel and I tried to customize it for speed. I also didn't use any patch...let's see how fast it is...

---

### Post by eRoot on 2006-04-15
I was hoping I could get the newest kernel on my slowish computer, but alas, I have encountered a problem.

When I'm building the kernel I get the following error:

```
  
...
...
...
  CC      kernel/posix-timers.o
  CC      kernel/kthread.o
  CC      kernel/wait.o
  CC      kernel/kfifo.o
  CC      kernel/sys_ni.o
  CC      kernel/posix-cpu-timers.o
kernel/posix-cpu-timers.c: In function ‘run_posix_cpu_timers’:
kernel/posix-cpu-timers.c:1275: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[2]: *** [kernel/posix-cpu-timers.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16ck3'
make: *** [stamp-build] Error 2
root@box:/usr/src/linux#
```
I noticed that if I start building it again, it starts off where the error occured and continues until it reaches the next "Segment fault". 

This can't good, can it?

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=eRoot]I was hoping I could get the newest kernel on my slowish computer, but alas, I have encountered a problem.

When I'm building the kernel I get the following error:

```
  
...
...
...
  CC      kernel/posix-timers.o
  CC      kernel/kthread.o
  CC      kernel/wait.o
  CC      kernel/kfifo.o
  CC      kernel/sys_ni.o
  CC      kernel/posix-cpu-timers.o
kernel/posix-cpu-timers.c: In function ‘run_posix_cpu_timers’:
kernel/posix-cpu-timers.c:1275: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[2]: *** [kernel/posix-cpu-timers.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16ck3'
make: *** [stamp-build] Error 2
root@box:/usr/src/linux#
```
I noticed that if I start building it again, it starts off where the error occured and continues until it reaches the next "Segment fault". 

This can't good, can it?[/QUOTE]
ok, this can be the result of a bad patch. Try re-compiling the kernel and skip the patch step. Also compile the 2.6.16.5 kernel from kernel.org. Just follow the tutorial but replace the old kernel name (2.6.16) with the new one (2.6.16.5).

---

### Post by IsKall on 2006-04-15
what do you mean with <name of the fine> ?

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=IsKall]what do you mean with <name of the fine> ?[/QUOTE]
I mean name of file. Sorry, typo. Are you installing the kernel now ? If so I hope it works.

---

### Post by geearf on 2006-04-15
[quote=MasterChief1234]I don't think there is a specific patch you could use but I just compilied the new 2.6.16.5 kernel and I tried to customize it for speed. I also didn't use any patch...let's see how fast it is...[/quote]
Good, please tell us later about how it feels :)

---

### Post by kleeman on 2006-04-15
I upgraded to the 2.6.17-rc1 kernel on dapper to fix a scsi problem. Seems to work quite well so far.

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=geearf]Good, please tell us later about how it feels :)[/QUOTE]
Here are some speed tests:

My Old 2.6.12-10 Kernel:
Boot (No InitNG): 1 min 4 sec.
Boot With InitNG: 54.26 seconds

Internet Test (Tested at testmy.net)
Test 1: 387 kb/s
Test 2: 393 kb/s
Test 3: 369 kb/s
--------------------------------------------------
My new 2.6.16.5 Customized Kernel-Unpatched
Boot (No InitNG): 54.46 seconds
Boot With InitNG: 43.58 seconds

Internet Test (Tested at testmy.net about the same time as the last test)
Test 1: 718 kb/s
Test 2: 711 kb/s 
Test 3: 720 kb/s
---------------------------------------------------
I will now compare the 2.6.16.5 kernel - unpatched to 2.6.16 patched kernel.

My observations for 2.16.5 up (compared to 2.6.16 p)
1. It seems to be much more stable- true, no apps have crashed
2. Apps load quicker - From a cold boot, swiftfox loads in 3 seconds compared to 4.3 on the old one.
3. My net seems a little faster - semi-true. Download speed is down 20 kb/s (this could be because alot of people are on now) but page rendering is much faster. 
4. Not much difference between patched and unpatched except for those above. 


My observations for 2.6.16p compared to 2.6.16.5up
1. Gives the impression of being faster - this is untrue.
2. Much more unstable. I had a few apps crash on 2.6.16p
----------------------------------------------------
There the tests are in.

---

### Post by plush on 2006-04-15
Any clues on my nvram issue?  I'm trying everything I can to compile this thing...

---

### Post by eRoot on 2006-04-15
[QUOTE=MasterChief1234]ok, this can be the result of a bad patch. Try re-compiling the kernel and skip the patch step. Also compile the 2.6.16.5 kernel from kernel.org. Just follow the tutorial but replace the old kernel name (2.6.16) with the new one (2.6.16.5).[/QUOTE]
Thank you for your advice, but unfortunately it didn't help. I'm still getting the same message.

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=eRoot]Thank you for your advice, but unfortunately it didn't help. I'm still getting the same message.[/QUOTE]
ok go under /usr/src as root and delete the 2.6.16 folders. Then just do the tutorial again and skip the patch. I also just thought of something, redownload the kernel. I have a feeling that your download may be corrupt. Good luck.

---

### Post by eRoot on 2006-04-15
[QUOTE=MasterChief1234]ok go under /usr/src as root and delete the 2.6.16 folders. Then just do the tutorial again and skip the patch. I also just thought of something, redownload the kernel. I have a feeling that your download may be corrupt. Good luck.[/QUOTE]
Hmm, that still didn't do the trick. It did actually compile somewhat longer, but it assume that's just coincidence. You said I might have a corrupt download. well, I used the following link and downloaded it for a second time, as you suggested: [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.5.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.5.tar.bz2) That is the correct one, right?
Anyway, It's past 01.00, so I should problaby go to bed. I'll try to figure it out tomorrow. Good night :)

---

### Post by geearf on 2006-04-15
Thanks for the feedback, it's strange to get worse perfomance with the ck patchset, but I'll stay with just the ubuntu patches then :)

---

### Post by dcstar on 2006-04-15
[QUOTE=ludzter]I now have about 6 diffrent Kernels in my menu.lst , but how do i completly remove a old or non working kernel, i figure it might be pretty stupid to something wrong here, and have to it all over again.
.......[/QUOTE]
Just some little hints to those getting used to all the arcane things that go with compiling new kernels:

1/ Always (ALWAYS!) leave the existing "Official" kernel on your system and available to boot up from if things go "Pear-shaped"!

2/ If you want to recompile and re-install the new kernel multiple times (for instance, you may want to remove unnecessary config items that don't apply to your hardware/environment to make the kernel smaller - as well as compile quicker) - then you need to not be running the new kernel of you want to replace it. Once, you have recompiled a new .deb file, reboot you old kernel to then remove the old "new" kernel, and then do the dkpg step to install your new "new" kernel.

Just out of interest, removing many (many) items from my config gave me a generated .deb file of 4.0 MB, and the complie time was a fraction of the full config. My new kernel still does everything it should on my system but uses less memory because it has less never (ever) used code.

BTW, my boot time with old K7 kernel, 70 seconds, with new kernel (cut down items compile), 52 seconds and yes, it does seem faster in so many other areas........

---

### Post by geearf on 2006-04-15
I've never had any troubles reinstalling the already running kernel.. maybe I was just lucky ?

---

### Post by bunnieofdoom on 2006-04-15
i followed this guide exactly and xserver wont start. it says Fatal cant load module nvidia.

all nvidia related modules are updated to latest version allready anythoughts?

---

### Post by towsonu2003 on 2006-04-15
[QUOTE=bunnieofdoom]i followed this guide exactly and xserver wont start. it says Fatal cant load module nvidia.

all nvidia related modules are updated to latest version allready anythoughts?[/QUOTE]
aren't you supposed to recompile nvidia module everytime you change the kernel? have a look at an nvidia howto on how to recompile it. In the meantime, change your xorg.conf: instead of nvidia, use nv. 
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bustedcopy04152006
sudo nano /etc/X11/xorg.conf
```
Navigate with arrows and page up-down. replace nvidia with nv (and if that doesn't work, replace that with vesa). save with ctrl + o (letter O), say yes. Exit with ctrl + x. Start X with startx (command). Once X is up and running, go to your favorite nvidia howto, check out how to recompile driver (?if needed?) etc. 

Well, another alternative is to wait for an nvidia expert to reply :)

---

### Post by kalifi on 2006-04-16
Hi,

after compilling the new kernel, lots of these
> device-mapper: error adding target to table
errors appeared.

I have no clue what caused them. I've googled something about LVM, but in my case I have only one hdd and I think that LVM is useless for me.

Any ideas?

Miro

---

### Post by Abild on 2006-04-16
Thanks a lot for the howto. It worked great and i got a significant speed improvement.

I have only one problem: When i try to install vmware i get the following error: 

```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The kernel defined by this directory of header files does not have the same
address space size as your running kernel.

```

Can anyone help me out?

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=Abild]Thanks a lot for the howto. It worked great and i got a significant speed improvement.

I have only one problem: When i try to install vmware i get the following error: 

```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The kernel defined by this directory of header files does not have the same
address space size as your running kernel.

```

Can anyone help me out?[/QUOTE]
Try backing up your configuration, remove it, then try getting the latest version an compile it from source. Then it should work.

---

### Post by Abild on 2006-04-16
[QUOTE=MasterChief1234]Try backing up your configuration, remove it, then try getting the latest version an compile it from source. Then it should work.[/QUOTE]

Should i remove the old vmware configuration or the kernel configuration?

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=Abild]Should i remove the old vmware configuration or the kernel configuration?[/QUOTE]
You should/can remove your vmware configuration. DON'T Delete your kernel config.

---

### Post by Abild on 2006-04-16
[QUOTE=MasterChief1234]You should/can remove your vmware configuration. DON'T Delete your kernel config.[/QUOTE]

Ok. Now i have uninstalled vmware with the vmware-uninstall.pl script and i have deleted the .vmware dir in my home folder but i still get the same error... :(

Thanks for your help so far :)

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=Abild]Ok. Now i have uninstalled vmware with the vmware-uninstall.pl script and i have deleted the .vmware dir in my home folder but i still get the same error... :(

Thanks for your help so far :)[/QUOTE]
Sorry that I'm not of much help. Let's see if anyone else knows.

---

### Post by greenbmw530i on 2006-04-16
MasterChief1234, I greatly appreciate your HowTo! But, one thing, my wifi isn't working, so I read the bottom of your HowTo and followed the ndiswrapper installation, but I'm stuck on the last step:
[QUOTE=foxy123]
5. Install
```
sudo dpkg -i ndiswrapper-modules-[your kernel]_[current version]-1_i386.deb ndiswrapper-utils_[current version]-1_i386.deb
```
[/QUOTE]
I'm not sure as to what I put in each bracket. An example would be incredibly helpful to me.

          2.6.16 is my kernel version (thanks to MasterChief1234 :D )
          1.13 is my ndiswrapper version

Thanks a lot in advance,
greenbmw

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=greenbmw530i]MasterChief1234, I greatly appreciate your HowTo! But, one thing, my wifi isn't working, so I read the bottom of your HowTo and followed the ndiswrapper installation, but I'm stuck on the last step:

I'm not sure as to what I put in each bracket. An example would be incredibly helpful to me.

          2.6.16 is my kernel version (thanks to MasterChief1234 :D )
          1.13 is my ndiswrapper version

Thanks a lot in advance,
greenbmw[/QUOTE]
ok, the brackets mean to put the name of the file in there. Assuming that you compilied ndiswrapper in your home directory:

1. Open terminal

2. in terminal type

sudo dpkg NAME HERE

then 

sudo dpkg -i OTHER NAME HERE

3. You may need to install one package before the other.

What I like to do is drag the .deb file into terminal so I don't need to do anything else so do this.

sudo dpkg -i then put a space and drag the .deb file into terminal.

---

### Post by greenbmw530i on 2006-04-16
The thing is, is that I'm on kernel 2.6.12 right now (since my wifi doesn't work on 2.6.16)
What should I do in this case?
For instance:
```

mike@Jamestown:~$ sudo dpkg -i ndiswrapper-modules-2.6.12-10-386_1.13-1_i386.deb ndiswrapper-utils_1.8-1_i386.deb
```
OR
```

mike@Jamestown:~$ sudo dpkg -i ndiswrapper-modules-2.6.16-cks4_ck3_1.13-1_i386.deb ndiswrapper-utils_1.8-1_i386.deb
```

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=greenbmw530i]The thing is, is that I'm on kernel 2.6.12 right now (since my wifi doesn't work on 2.6.16)
What should I do in this case?
For instance:
```

mike@Jamestown:~$ sudo dpkg -i ndiswrapper-modules-2.6.12-10-386_1.13-1_i386.deb ndiswrapper-utils_1.8-1_i386.deb
```
OR
```

mike@Jamestown:~$ sudo dpkg -i ndiswrapper-modules-2.6.16-cks4_ck3_1.13-1_i386.deb ndiswrapper-utils_1.8-1_i386.deb
```[/QUOTE]

Do this, one may need to be installed before the other:
> 
sudo dpkg -i ndiswrapper-modules-2.6.16-cks4_ck3_1.13-1_i386.deb 
 
If that one ^ returns an error, install the other one first.

> sudo dpkg -i ndiswrapper-utils_1.8-1_i386.deb

---

### Post by ashrack on 2006-04-16
[QUOTE=Abild]Thanks a lot for the howto. It worked great and i got a significant speed improvement.

I have only one problem: When i try to install vmware i get the following error: 

```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The kernel defined by this directory of header files does not have the same
address space size as your running kernel.

```

Can anyone help me out?[/QUOTE]
Just to let U know, that Ure not alone. I get the same thing with my 2.6.15 CUSTOM COMPILED KERNEL.
I started a new thread here, so please post there from now on about VMWARE error.
[http://ubuntuforums.org/showthread.php?p=927789#post927789](http://ubuntuforums.org/showthread.php?p=927789#post927789)

---

### Post by ashrack on 2006-04-16
[QUOTE=greenbmw530i]The thing is, is that I'm on kernel 2.6.12 right now (since my wifi doesn't work on 2.6.16)
What should I do in this case?
For instance:
```

mike@Jamestown:~$ sudo dpkg -i ndiswrapper-modules-2.6.12-10-386_1.13-1_i386.deb ndiswrapper-utils_1.8-1_i386.deb
```
OR
```

mike@Jamestown:~$ sudo dpkg -i ndiswrapper-modules-2.6.16-cks4_ck3_1.13-1_i386.deb ndiswrapper-utils_1.8-1_i386.deb
```[/QUOTE]

4 2.6.16 kernel U must use:
```

mike@Jamestown:~$ sudo dpkg -i ndiswrapper-modules-2.6.16-cks4_ck3_1.13-1_i386.deb ndiswrapper-utils_1.8-1_i386.deb
```
since the other one is meant for kernel 2.6.12

---

### Post by xXx 0wn3d xXx on 2006-04-16
I'm getting ready to compile the latest 2.6.17-rc1. Has anyone used it ? How stable is it/how does it run ?

---

### Post by kleeman on 2006-04-16
You missed my comment above. 2.6.17-rc1 runs fine on my dapper install.

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=kleeman]You missed my comment above. 2.6.17-rc1 runs fine on my dapper install.[/QUOTE]
ok, well let's see how it runs on breezy...

---

### Post by zapcojake on 2006-04-16
I seem to be having trouble getting fglrx working after the recompile.  If I do the xorg reconfigure command I can select the driver but the 3d is horrid and 3ddesk won't work.  I tried a couple of the ATI howto's but apt can't find restricted modules for the kernel.  I'm sure somebody here has cured this if they can just point me in the right direction that would be great.  Thanks.

---

### Post by meepy on 2006-04-17
Oh god. I'm in trouble atm.

I did all what the guide said, but I think I got a serious problem. It was building for hours and then it gave me an error with it could not access a file because it was a read-only filesystem (stamp-error?). I could not start firefox or anything else, nothing worked so I tried reboot in hope it would be fixed, grub loaded, and I chose my kernel (the new wasent listed) It began loading and then at "Checking filesystem" it said it still was a read-only filesystem and I should fix it manually with "mount -n -o remount,rw /" I did that but it dident work. I tried in fail-safe enviroment aswell - no luck?

What happened and how can I save my system, I'm sitting on a horrible Windows system atm. Hoping for some help. Thanks in advance. :( :(

---

### Post by xXx 0wn3d xXx on 2006-04-17
I just added some mirrors for the new kernels. I uploaded the 2.6.16, 2.6.16.5, and 2.6.17-rc1 kernels. The mirrors are hosted on rapidshare.

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=meepy]Oh god. I'm in trouble atm.

I did all what the guide said, but I think I got a serious problem. It was building for hours and then it gave me an error with it could not access a file because it was a read-only filesystem (stamp-error?). I could not start firefox or anything else, nothing worked so I tried reboot in hope it would be fixed, grub loaded, and I chose my kernel (the new wasent listed) It began loading and then at "Checking filesystem" it said it still was a read-only filesystem and I should fix it manually with "mount -n -o remount,rw /" I did that but it dident work. I tried in fail-safe enviroment aswell - no luck?

What happened and how can I save my system, I'm sitting on a horrible Windows system atm. Hoping for some help. Thanks in advance. :( :([/QUOTE]
What kernel did you compile ? Did it return any errors when it was compiling it ?

---

### Post by meepy on 2006-04-17
The only error was something with ns/some file (or something) that it could not access it because it was read-only. 

I compiled the kernel in your first topic, top link incl. the patch. And followed the guide all the way, is there anyway to save my system?

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=meepy]The only error was something with ns/some file (or something) that it could not access it because it was read-only. 

I compiled the kernel in your first topic, top link incl. the patch. And followed the guide all the way, is there anyway to save my system?[/QUOTE]
Did you get any errors while applying the patch ?

---

### Post by meepy on 2006-04-17
No errors during patching. :(

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=meepy]No errors during patching. :([/QUOTE]
Well, since the error came when compiling the kernel, it doesn't seem to be the kernel that caused the problem. Did you do anything else before compiling the kernel ? Like tweak your filesystem ?

---

### Post by xXx 0wn3d xXx on 2006-04-17
A new kernel is out ! The 2.6.16.7 is now the latest stable kernel.

---

### Post by Kibbo on 2006-04-17
Hi all, 

Trying to follow the HowTo, and the patching and compiling both seemed to go smoothly.  

I dpkg'ed the file, and it hangs at "Setting up kernel-image (version) ..."

Here is the last few lines in the terminal:

dpkg-deb: building package `kernel-image-2.6.16-cks4' in `../kernel-image-2.6.16-cks4_ck3_i386.deb'.
rm -f -r debian/tmp-image
echo done >  stamp-image
make[1]: Leaving directory `/usr/src/linux-2.6.16ck3'

root@ubuntu:/usr/src/linux# cd /usr/src/
root@ubuntu:/usr/src# sudo dpkg -i kernel-image-2.6.16-cks4_ck3_i386.deb
Selecting previously deselected package kernel-image-2.6.16-cks4.
(Reading database ... 96070 files and directories currently installed.)
Unpacking kernel-image-2.6.16-cks4 (from kernel-image-2.6.16-cks4_ck3_i386.deb) ...
Setting up kernel-image-2.6.16-cks4 (ck3) ...

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=Kibbo]Hi all, 

Trying to follow the HowTo, and the patching and compiling both seemed to go smoothly.  

I dpkg'ed the file, and it hangs at "Setting up kernel-image (version) ..."

Here is the last few lines in the terminal:

dpkg-deb: building package `kernel-image-2.6.16-cks4' in `../kernel-image-2.6.16-cks4_ck3_i386.deb'.
rm -f -r debian/tmp-image
echo done >  stamp-image
make[1]: Leaving directory `/usr/src/linux-2.6.16ck3'

root@ubuntu:/usr/src/linux# cd /usr/src/
root@ubuntu:/usr/src# sudo dpkg -i kernel-image-2.6.16-cks4_ck3_i386.deb
Selecting previously deselected package kernel-image-2.6.16-cks4.
(Reading database ... 96070 files and directories currently installed.)
Unpacking kernel-image-2.6.16-cks4 (from kernel-image-2.6.16-cks4_ck3_i386.deb) ...
Setting up kernel-image-2.6.16-cks4 (ck3) ...[/QUOTE]
It takes a while to set up the kernel. On my 2.2 ghz, 512 of ram system it can take as long as 4 minutes. Sometimes longer.

---

### Post by aktiwers on 2006-04-17
Thanks for a great guide! This worked out easy and painless for me :)
I have been running Linux for about a month now, and never thought I would compile a kernel so fast!

Thanks again! :)

---

### Post by Kibbo on 2006-04-17
Thanks for the quick reply, Chief.

I've left it running now for 30 mins, on a PIV@2.0 Ghz with a gig of ram.  And my system monitor is pretty quiet on both the proccessor and the HD activity. 

Barring other suggestions, I think I'm going to cancel the proccess and try to redownload and recompile the kernel.  Based on what you see in my previous post, does it seem that i've downloaded the right files?

Thanks for any help and suggestions.

Edit: Is there anything that I should delete or uninstall before I try again?

---

### Post by xXx 0wn3d xXx on 2006-04-17
You should go under /usr/src and delete the directory that you extracted the faulty kernel to. Right now I'm compiling the newly released (as of 1 hour ago) 2.6.16.7 kernel. I uploaded it to rapidshare because when a new kernel is released, lol download speeds on kernel.org get slow. I spent 30 minutes disabling uneeded modules and filesystems in xconfig x_x I hope it boots.

---

### Post by timczer on 2006-04-18
I have successfully compiled and am using the 2.6.16.7 kernel.  I am trying to now get the latest Nvidia drivers installed and working (8756 I believe).  When I get to running the nvidia installer, I get to where it is going to compile the module but it errors out saying

 " /lib/modules/2.6.16.7/build/include/linux/version.h does not exist.  The most likely reason for this is that the kernel source files in /lib/modules/2.6.16.7/build have not been configured."

What am I doing wrong?  How do I get the Nvidia drivers to install?

---

### Post by ashrack on 2006-04-18
[QUOTE=meepy]Oh god. I'm in trouble atm.
 It began loading and then at "Checking filesystem" it said it still was a read-only filesystem and I should fix it manually with "mount -n -o remount,rw /" I did that but it dident work. I tried in fail-safe enviroment aswell - no luck?
[/QUOTE]

Could U copy paste your errors here.

---

### Post by Kibbo on 2006-04-18
The deb file completed its setup this time.  I'm not going to reboot tonight, I'm in the middle of a movie and I expect to have to tinker with ndiswrapper to get online tomorrow.  

Good luck with your kernel, Chief, and thanks for the great guide.

---

### Post by dvader on 2006-04-18
MC  

followed your "howto" , and nothing as happened , didn't even crash my OS    Uname -r gives the original kernel , did run the grub command .  Printed out all the imfo ane will go over it again.  Used the copy/paste operation to eliminate any typos ...  

What is next to see what went wrong ????

dvader

Ps where do I find avatars ?????

---

### Post by xXx 0wn3d xXx on 2006-04-18
[QUOTE=dvader]MC  

followed your "howto" , and nothing as happened , didn't even crash my OS    Uname -r gives the original kernel , did run the grub command .  Printed out all the imfo ane will go over it again.  Used the copy/paste operation to eliminate any typos ...  

What is next to see what went wrong ????

dvader

Ps where do I find avatars ?????[/QUOTE]
Did you install the .deb ? It is in /usr/src. If you did install it try running "sudo update-grub" then it should show up. If it doesn't, you compilied a bad kernel. It can and does happen. Just delete the .deb, .tar.bz2, and the 2.6.16.7 kernel folder from  under /urs/src. Then re-download and recompile. Did you try using the patch on 2.6.16.7 or a newer kernel then 2.6.16 ? It only works on 2.6.16.

---

### Post by timczer on 2006-04-18
still having issues getting the nvidia driver to work.  I went back to the "nv" driver in xorg.conf, works fine.  Using synaptic I installed the nvidia-glx driver (7667) and enabled the driver.  Restarted and get can't start the x server.  it says it can't find or load the nvidia kernel module.  Is there an issue with how the kernel was compiled, is it an issue with the 2.6.16.7 kernel?  Any help would be appreciated.

---

### Post by Rizado on 2006-04-18
[QUOTE=timczer]still having issues getting the nvidia driver to work.  I went back to the "nv" driver in xorg.conf, works fine.  Using synaptic I installed the nvidia-glx driver (7667) and enabled the driver.  Restarted and get can't start the x server.  it says it can't find or load the nvidia kernel module.  Is there an issue with how the kernel was compiled, is it an issue with the 2.6.16.7 kernel?  Any help would be appreciated.[/QUOTE]Older drivers have problem compiling on 2.6.16
You should use the drivers from nvidia instead. Keep your kernel source in /usr/src like it was when compiling and run the installer and it should work fine.

---

### Post by Rizado on 2006-04-18
[QUOTE=MasterChief1234][COLOR="Blue"][ Latest Kernel Patch ](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/2.6.16-ck4/patch-2.6.16-cks4.bz2)[/COLOR] Don't apply the patch if you are compiling a kernel other then 2.6.16 otherwise you are going to get errors.[/QUOTE]That's a link to the server patch. Desktop patches are labled ck.

---

### Post by dvader on 2006-04-18
master C

followed your suggestions , but before i go any further , best get things right    up to here , and here is the error message  (using 2.6.16.7)
Setting up kdelibs (3.4.3-0ubuntu2) ...
root@local:/home/harry#  sudo make xconfig
make: *** No rule to make target `xconfig'.  Stop.
root@local:/home/harry#  cd /usr/src/linux
root@local:/usr/src/linux#  sudo make xconfig
scripts/kconfig/qconf arch/i386/Kconfig
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

qconf: cannot connect to X server :0.0
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2
root@local:/usr/src/linux# 

I installed kdee libs , still get the error message 

Assistance appreciated

Dvader

---

### Post by xXx 0wn3d xXx on 2006-04-18
[QUOTE=dvader]master C

followed your suggestions , but before i go any further , best get things right    up to here , and here is the error message  (using 2.6.16.7)
Setting up kdelibs (3.4.3-0ubuntu2) ...
root@local:/home/harry#  sudo make xconfig
make: *** No rule to make target `xconfig'.  Stop.
root@local:/home/harry#  cd /usr/src/linux
root@local:/usr/src/linux#  sudo make xconfig
scripts/kconfig/qconf arch/i386/Kconfig
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

qconf: cannot connect to X server :0.0
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2
root@local:/usr/src/linux# 

I installed kdee libs , still get the error message 

Assistance appreciated

Dvader[/QUOTE]

I haven't seen an error like this before...this isn't going to be much help but delete the 2.6.16.7 kernel .bz2 file and the 2.6.16.7 directory. Then redownload and try again. Not every kernel will compile correctly all the time. I have compilied alot of kernels and a few of them wouldn't boot. This can be caused by trying to apply a new patch to an old kernel or by trying to import a kernel config from a very old kernel. Sometimes kernel downloads can be corrupt. I hope you can compile it :) It seems like a problem with your x server. I don't know what to do about that...

---

### Post by plush on 2006-04-18
For all you PPC users out there, after a ton of homework I found the following .config entries which could be possible fixes for a problem I've encountered in compiling 2.6.16 on a PPC:

CONFIG_GENERIC_NVRAM=y
CONFIG_PPCBUG_NVRAM=y
CONFIG_NVRAM=y 

 I tried adding these all to my .config before another compilation, but I get the same nvram_byte error message, and furthermore after each compile attempt when I go back and check on the .config file, I find that it does not have these entries any longer!!!  I've tried setting the .config file to read only, as well as a number of other possibilities, but I'm guessing there either exist different new switches in the new 2.6.16-compatible configs to handle this bug, or they simply haven't been implemented into the build.

---

### Post by xXx 0wn3d xXx on 2006-04-18
The new 2.6.16.8 kernel is out :) I hope it works well on dapper.

---

### Post by dvader on 2006-04-19
.


MC  

I have gone over all the printouts on the kernel 'hoto'  here is where I have a problem
with the xserver

13. Now import it: Make sure to replace the kernel version in this following command from the one from uname -r.

sudo cp /boot/config-2.6.14-ck1 .config .......................   is .config require a little more information 

Looks like a hidden file or it is part of a destination for the the /boot/config-2.6.12-9-386  (uname -r) on my machine   

Can you clarify  ????? 

Thanks 

Dvader

---

### Post by PriceChild on 2006-04-19
[quote=oxEz]Don't go in Devices Drivers first, go in "Block layers". I looked in the .config file, and it's where I learned where IO schedulers were hidden.[/quote]

My pc's currently compiling the kernel when i just found this comment.

Will this make a big difference? Do you think i should go and try and find this option again? If so, how? I noticed something about deleting the .configure file and starting from "make xconfig" again?

pricey

---

### Post by xXx 0wn3d xXx on 2006-04-19
[QUOTE=PriceChild]My pc's currently compiling the kernel when i just found this comment.

Will this make a big difference? Do you think i should go and try and find this option again? If so, how? I noticed something about deleting the .configure file and starting from "make xconfig" again?

pricey[/QUOTE]
I woudn't make a huge difference, possibly not even a noticeable one. If you have a newer computer, it's not worth re-compiling the kernel. However, if you have a 5 year+ older computer, it is worth it.

---

### Post by PriceChild on 2006-04-19
Ok i'll be fine then :)

Or not... having troubles with starting the xserver:

[http://ubuntuforums.org/showthread.php?t=162611](http://ubuntuforums.org/showthread.php?t=162611)

---

### Post by dvader on 2006-04-19
Compile the new 2.6.16 kernel

After three seperate install trys 

harry@local:~$ uname -r
2.6.16.7


A learning expirence and a few obsverations 

Try 1  Apress cd , added nvidia and kde desk top ... xserver problems 

Try 2  Kubuntu  down load cd just a try  but xserver problems 

Try 3 Apress cd , installed as Ubuntu , then kernel install

Noticed in the last try some of the dirs were not the same as in the howto  used the ls command and file browser to find where the necessary files were 

Now I need to install nvidia - glx and the kde desk top   and I am not interedted in breaking any thing  

Dvader

---

### Post by PriceChild on 2006-04-19
All sorted :) running 2.16.6 patched to 6... and just noticed the latest version is 7 :)

Ah well :)

Thanks MasterChief for the How to!

Oh and there's DEFINATELY a noticable performance increase :)

---

### Post by uqbar on 2006-04-19
You could do the
sudo -s -H
at the very first in order to save all the subsequent sudos.
We are recompiling the whole kernel so we are supposed to be as careful as the friendly root.

---

### Post by PriceChild on 2006-04-20
Hey again... i've compiled 2.6.16.9 (downloaded from the front page)

And all seems to have gone perfectly.

However, i'm trying to re-install vmware player, and it gives the following errors:

> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux/include

The kernel defined by this directory of header files does not have the same
address space size as your running kernel. 
This seems wierd and shouldn't happen.

Please help! :)

Pricey

---

### Post by play0r on 2006-04-20
im running 2.6.17-rc2 on my home desktop using dapper right now & it runs great, only downside is this iptables issue. 
for some reason when i try & issue "iptables -t filter" it spazes out & says its not compatible with my current kernel or something similar to that. :confused: 
i assume its something to do with config-2.6.17-rc2.
i guess ill just compile iptables 1.3.5 when i get home from classes today & see if that works. i dont really mind not having firestarter or any gui firewall for that matter, but id like to take a peek at my existing filter table lol. 
if anyone has some useful & informative insight on this problem it'd be much appreciated.
thx for the tut/howto masterchief. i didnt have to try & recover the information from the deepest void of my brain to compile this newest kernel lol. :-# 
worked seamlessly the first time around. ;) 

ez,
play0r

p.s.
the internet seems to run a lot faster as far as incoming data transfers via http https & especially secure ftp.

---

### Post by play0r on 2006-04-21
[QUOTE=play0r]
for some reason when i try & issue "iptables -t filter" it spazes out & says its not compatible with my current kernel or something similar to that. :confused: 
i assume its something to do with config-2.6.17-rc2.
[/QUOTE]

eureka!
after some deep thought i figured out what was wrong. duh2me of course my kernel isnt going to be compatible with iptables if it doesnt have them configured in "make menuconfig" (or make xconfig if you do it step by step in the howto) & both the kernel source & iptables source need to be patched by the latest snapshot of patch-o-matic from netfliters website. all i need to do now is recompile & install both patched kernel & iptables-1.3.5. :-D 
but im using the current stable kernel image (2.6.16.9) instead of 2.6.17-rc2.

ez,
play0r

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=play0r]eureka!
after some deep thought i figured out what was wrong. duh2me of course my kernel isnt going to be compatible with iptables if it doesnt have them configured in "make menuconfig" (or make xconfig if you do it step by step in the howto) & both the kernel source & iptables source need to be patched by the latest snapshot of patch-o-matic from netfliters website. all i need to do now is recompile & install both patched kernel & iptables-1.3.5. :-D 
but im using the current stable kernel image (2.6.16.9) instead of 2.6.17-rc2.

ez,
play0r[/QUOTE]
I'm using the new 2.6.17rc2 kernel, so to get iptables to work I would need to use the latest stable kernel and compile the latest iptables. Is that correct ?

---

### Post by play0r on 2006-04-21
when i was reading through the readme it seemed as if it would only apply to a "stable" kernel, but you can try it. 
also it seemed as if it would only apply to the most current iptables source code.

ez,
play0r

ps
if it works for 2.6.17-rc2 plz post that it did lol :-#

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=play0r]when i was reading through the readme it seemed as if it would only apply to a "stable" kernel, but you can try it. 
also it seemed as if it would only apply to the most current iptables source code.

ez,
play0r[/QUOTE]
ok, I compilied the latest iptables and tested my ports. All my ports are stealth and none of them replied to a single packet. Where can I find this patch so I can apply it and compile the new stable kernel ?

---

### Post by play0r on 2006-04-21
sorry i didnt include the link in my last post.

[http://ftp.netfilter.org/pub/patch-o-matic/snapshot/](http://ftp.netfilter.org/pub/patch-o-matic/snapshot/)
^^^^

you need to recompile **both** sources (kernel & iptables) after you use patch-o-matic, because this patches both iptables & the kernel's source code.

ez,
play0r

ps
im in class right now (ah the joys of being a full-time IT student lol), but in an hour or two i can tell you if it worked out for me using the stable kernel source & iptables-1.3.5.

---

### Post by play0r on 2006-04-21
yay! 
it worked.
also, firestarter is fully functional.

here is my core & ip netfilter configuration:

> #
# Core Netfilter Configuration
#
CONFIG_NETFILTER_NETLINK=y
CONFIG_NETFILTER_NETLINK_QUEUE=m
CONFIG_NETFILTER_NETLINK_LOG=m
CONFIG_NETFILTER_XTABLES=m
# CONFIG_NETFILTER_XT_TARGET_CLASSIFY is not set
CONFIG_NETFILTER_XT_TARGET_MARK=m
# CONFIG_NETFILTER_XT_TARGET_NFQUEUE is not set
# CONFIG_NETFILTER_XT_MATCH_COMMENT is not set
CONFIG_NETFILTER_XT_MATCH_CONNTRACK=m
# CONFIG_NETFILTER_XT_MATCH_DCCP is not set
# CONFIG_NETFILTER_XT_MATCH_HELPER is not set
CONFIG_NETFILTER_XT_MATCH_LENGTH=m
CONFIG_NETFILTER_XT_MATCH_LIMIT=m
CONFIG_NETFILTER_XT_MATCH_MAC=m
CONFIG_NETFILTER_XT_MATCH_MARK=m
# CONFIG_NETFILTER_XT_MATCH_PHYSDEV is not set
# CONFIG_NETFILTER_XT_MATCH_PKTTYPE is not set
# CONFIG_NETFILTER_XT_MATCH_REALM is not set
# CONFIG_NETFILTER_XT_MATCH_SCTP is not set
CONFIG_NETFILTER_XT_MATCH_STATE=m
# CONFIG_NETFILTER_XT_MATCH_STRING is not set
CONFIG_NETFILTER_XT_MATCH_TCPMSS=m

#
# IP: Netfilter Configuration
#
CONFIG_IP_NF_CONNTRACK=m
# CONFIG_IP_NF_CT_ACCT is not set
# CONFIG_IP_NF_CONNTRACK_MARK is not set
# CONFIG_IP_NF_CONNTRACK_EVENTS is not set
# CONFIG_IP_NF_CONNTRACK_NETLINK is not set
# CONFIG_IP_NF_CT_PROTO_SCTP is not set
CONFIG_IP_NF_FTP=m
CONFIG_IP_NF_IRC=m
# CONFIG_IP_NF_NETBIOS_NS is not set
# CONFIG_IP_NF_TFTP is not set
# CONFIG_IP_NF_AMANDA is not set
# CONFIG_IP_NF_PPTP is not set
# CONFIG_IP_NF_QUEUE is not set
CONFIG_IP_NF_IPTABLES=m
# CONFIG_IP_NF_MATCH_IPRANGE is not set
CONFIG_IP_NF_MATCH_MULTIPORT=m
CONFIG_IP_NF_MATCH_TOS=m
# CONFIG_IP_NF_MATCH_RECENT is not set
# CONFIG_IP_NF_MATCH_ECN is not set
# CONFIG_IP_NF_MATCH_DSCP is not set
CONFIG_IP_NF_MATCH_AH_ESP=m
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_MATCH_OWNER=m
# CONFIG_IP_NF_MATCH_ADDRTYPE is not set
# CONFIG_IP_NF_MATCH_HASHLIMIT is not set
# CONFIG_IP_NF_MATCH_POLICY is not set
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_LOG=m
CONFIG_IP_NF_TARGET_ULOG=m
CONFIG_IP_NF_TARGET_TCPMSS=m
CONFIG_IP_NF_NAT=m
CONFIG_IP_NF_NAT_NEEDED=y
CONFIG_IP_NF_TARGET_MASQUERADE=m
CONFIG_IP_NF_TARGET_REDIRECT=m
# CONFIG_IP_NF_TARGET_NETMAP is not set
# CONFIG_IP_NF_TARGET_SAME is not set
CONFIG_IP_NF_NAT_SNMP_BASIC=m
CONFIG_IP_NF_NAT_IRC=m
CONFIG_IP_NF_NAT_FTP=m
# CONFIG_IP_NF_MANGLE is not set
# CONFIG_IP_NF_RAW is not set
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
# CONFIG_IP_NF_ARP_MANGLE is not set

the easiest way to setup these properly is to use "make menuconfig" in place of "make xconfig".
masterchief you should prolly edit your howto to include links & howto steps to patch the newest version of iptables & the 2.6.16.x kernel sources with patch-o-matic.

ez,
play0r

---

### Post by xXx 0wn3d xXx on 2006-04-22
I'm planning to add pre-compilied kernels to the main thread. I will compile them with performance in mind. I am planning to make the kernels for AMD and Intel processors. Does anyone think that this is a good idea ? I think it would help people who are new to linux get the latest kernel.

---

### Post by PriceChild on 2006-04-23
[quote=MasterChief1234]I'm planning to add pre-compilied kernels to the main thread. I will compile them with performance in mind. I am planning to make the kernels for AMD and Intel processors. Does anyone think that this is a good idea ? I think it would help people who are new to linux get the latest kernel.[/quote]

Hmm... don't really like the idea of that. If people are interested enough to want to optimize a kernel, then they're going to get more from it than speed, if they do it themselves!

Pricey

---

### Post by Didjit on 2006-04-23
[quote=PriceChild]

However, i'm trying to re-install vmware player, and it gives the following errors:

 
This seems wierd and shouldn't happen.

Please help! :)

Pricey[/quote]

I originaly had to do this for the install:

Install the kenal headers, which I think you already have if recompiling the new kernal.

uname -r
sudo ln -s  /usr/src/linux-headers-<your version from uname> linux

Then run to reconfigure for the new kernal: sudo /usr/bin/vmware-config.pl

HTH

Didjit

---

### Post by zasf on 2006-04-23
Hello and thanks for the howto.

I succesfully patched and installed the kernel, then I compiled fglrx module and installed the firmware for the wireless card.

I have only one problem, the cdrom doesn't work, when I put a cdrom, the cd doesn't get mounted neither automatically or manually, anyone experienced this? What should I do?

Thanks,
Matteo

---

### Post by PriceChild on 2006-04-23
Didjit, it was an actual problem with vmware and the 2.6.16 kernel. There is a patch availiable if you follow my link.

[quote=zasf]Hello and thanks for the howto.

I succesfully patched and installed the kernel, then I compiled fglrx module and installed the firmware for the wireless card.

I have only one problem, the cdrom doesn't work, when I put a cdrom, the cd doesn't get mounted neither automatically or manually, anyone experienced this? What should I do?

Thanks,
Matteo[/quote]

I think i might be having the same problem... maybe...

They do mount (check system admin disks) but the icons don't appear on the desktop, or on gnome menus.

This includes the ipod

---

### Post by Trunkz on 2006-04-23
Hey folks, well just wanna confirm that this lovely guide works. Details below:

Dell Inspiron 2500 Laptop
Intel P3 900Mhz
256MB Ram
10GB HD

Kernel used was 2.6.16 with the ck3 patch. Linux headers used were a 686 branch for the same kernel, and this works fine with ndiswrapper as well :) Thanks again ;) (I'm tempted to compile the latest stable kernel, but this one took around 2hrs to actually compile.. mehhh!! ](*,) )

---

### Post by zasf on 2006-04-23
[QUOTE=PriceChild]I think i might be having the same problem... maybe...

They do mount (check system admin disks) but the icons don't appear on the desktop, or on gnome menus.

This includes the ipod[/QUOTE]

Hum.. here they do not mount, since /media/cdrom is empty, I can't even mount them manually, can you browse your cdrom? The usual cdrom device (/dev/scd0) is not even there. Any ideas?

---

### Post by dawg on 2006-04-23
anyone have issues with fglrx/mesa?  i can't fix it and i know im running 2.6.16.

---

### Post by mkools on 2006-04-23
Nice guide! Great job!

I used the latest CK7 patch on a clean 2.6.16 kernel and that worked also for me.

Ehh one thing, it's advisable to deselect any modules that you are not using, otherwise the kernel compiling takes ages even on my brand new 2 ghz Pentium-M notebook.

Of course you have to know what you are doing when doing that, but I'm sure people that follow this guide are a little more advanced users and will ;)

Thanks again!

---

### Post by gschoper on 2006-04-23
First off I would like to say that this is a great How-To. Many thanks to MasterChief1234. I've only been running Ubuntu for about a month now, but I have been running various flavors of linux for many years and since my first install of Slackware ~1996 this is the first time I have tried to compile kernel sources.

I ran into the same wifi and iptables issues as others have expressed in this thread and wanted to share my solutions.

For ndiswrapper issues I followed:

> 
Troubleshooting:

Q: My Wifi Doesn't work !

A:To get wifi working, compile the new ndiswrapper from source. Follow the [tutorial]("http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source"). 


To fix iptables I edited .config after running
> sudo make xconfig
and replaced the

> 
#
# Core Netfilter Configuration
#

and
> 
#
# IP: Netfilter Configuration
#


sections with:

> 
#
# Core Netfilter Configuration
#
CONFIG_NETFILTER_NETLINK=y
# CONFIG_NETFILTER_NETLINK_QUEUE is not set
# CONFIG_NETFILTER_NETLINK_LOG is not set
CONFIG_NETFILTER_XTABLES=m
# CONFIG_NETFILTER_XT_TARGET_CLASSIFY is not set
CONFIG_NETFILTER_XT_TARGET_MARK=m
# CONFIG_NETFILTER_XT_TARGET_NFQUEUE is not set
# CONFIG_NETFILTER_XT_MATCH_COMMENT is not set
CONFIG_NETFILTER_XT_MATCH_CONNTRACK=m
# CONFIG_NETFILTER_XT_MATCH_DCCP is not set
# CONFIG_NETFILTER_XT_MATCH_HELPER is not set
CONFIG_NETFILTER_XT_MATCH_LENGTH=m
CONFIG_NETFILTER_XT_MATCH_LIMIT=m
CONFIG_NETFILTER_XT_MATCH_MAC=m
CONFIG_NETFILTER_XT_MATCH_MARK=m
# CONFIG_NETFILTER_XT_MATCH_PHYSDEV is not set
# CONFIG_NETFILTER_XT_MATCH_PKTTYPE is not set
# CONFIG_NETFILTER_XT_MATCH_REALM is not set
# CONFIG_NETFILTER_XT_MATCH_SCTP is not set
CONFIG_NETFILTER_XT_MATCH_STATE=m
# CONFIG_NETFILTER_XT_MATCH_STRING is not set
CONFIG_NETFILTER_XT_MATCH_TCPMSS=m

#
# IP: Netfilter Configuration
#
CONFIG_IP_NF_CONNTRACK=m
# CONFIG_IP_NF_CT_ACCT is not set
# CONFIG_IP_NF_CONNTRACK_MARK is not set
# CONFIG_IP_NF_CONNTRACK_EVENTS is not set
# CONFIG_IP_NF_CONNTRACK_NETLINK is not set
# CONFIG_IP_NF_CT_PROTO_SCTP is not set
CONFIG_IP_NF_FTP=m
CONFIG_IP_NF_IRC=m
# CONFIG_IP_NF_NETBIOS_NS is not set
# CONFIG_IP_NF_TFTP is not set
# CONFIG_IP_NF_AMANDA is not set
# CONFIG_IP_NF_PPTP is not set
# CONFIG_IP_NF_QUEUE is not set
CONFIG_IP_NF_IPTABLES=m
# CONFIG_IP_NF_MATCH_IPRANGE is not set
CONFIG_IP_NF_MATCH_MULTIPORT=m
CONFIG_IP_NF_MATCH_TOS=m
# CONFIG_IP_NF_MATCH_RECENT is not set
# CONFIG_IP_NF_MATCH_ECN is not set
# CONFIG_IP_NF_MATCH_DSCP is not set
CONFIG_IP_NF_MATCH_AH_ESP=m
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_MATCH_OWNER=m
# CONFIG_IP_NF_MATCH_ADDRTYPE is not set
# CONFIG_IP_NF_MATCH_HASHLIMIT is not set
# CONFIG_IP_NF_MATCH_POLICY is not set
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_LOG=m
CONFIG_IP_NF_TARGET_ULOG=m
CONFIG_IP_NF_TARGET_TCPMSS=m
CONFIG_IP_NF_NAT=m
CONFIG_IP_NF_NAT_NEEDED=y
CONFIG_IP_NF_TARGET_MASQUERADE=m
CONFIG_IP_NF_TARGET_REDIRECT=m
# CONFIG_IP_NF_TARGET_NETMAP is not set
# CONFIG_IP_NF_TARGET_SAME is not set
CONFIG_IP_NF_NAT_SNMP_BASIC=m
CONFIG_IP_NF_NAT_IRC=m
CONFIG_IP_NF_NAT_FTP=m
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_TOS=m
# CONFIG_IP_NF_TARGET_ECN is not set
# CONFIG_IP_NF_TARGET_DSCP is not set
# CONFIG_IP_NF_TARGET_TTL is not set
# CONFIG_IP_NF_RAW is not set
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
# CONFIG_IP_NF_ARP_MANGLE is not set

before building the kernel.

Everything on my system runs fine except I cannot mount my vfat filesystems and I'm running the "nv" nvidia drivers as I have not yet attemtped to install the latest nvidia drivers. If anyone has any suggestions for these I would appreciate them.

Also, I have noticed a lot of peole have been disabling un-needed items from their kernel configs in order to streamline and speed them up. Can anyone offer any suggestions/tips for doing this as I'm not sure what it is or is not safe to get rid of.

TIA,

G

Also, noted in an earlier post it ws suggested that usplash be re-installed to get the splash screen back. I have done this (re-installed via Synaptic) and still get a blank screen from grub through GDM.

---

### Post by mkools on 2006-04-24
One other tip, I suggest using make menuconfig i.o. xconfig since you need al those QT libraries for that.
Just install ncurses5 and ncurses5 devel, it's only a couple of MB and you get the same results, I think menuconfig is even more comfortable.

Btw. after my upgrade on Dapper my Wifi stopped working also.
I thought I might just as well download the newest ipw2200 drivers from the net, so I did, ran the remove-old script that came with it, and did a reinstallation.
Copied the firmwarefiles to /lib/firmware, and I'm back online again within a few minutes :mrgreen:

---

### Post by Efwis on 2006-04-24
I was reading this thread and found a few comments dealing with the kde libs, Nvidia drivers and not being able to load windows partitions so here is some help for those of you with this issue.

first kde libs.
```
$ sudo apt-get install qt3-apps-dev
$ sudo apt-get install qt3-dev-tools
```
now you have the necessary files to do **make xconfig**

Nvidia Drivers.

After making sure you have all the necessary tools, including the qt3 ibs, type:
```
$ make xconfig
```
click on graphics, then remove the "nvidia framebuffer support" by doubleclicking on the [ ] so it's blank. save, recompile

go get the latest Nvidia driver from Nvidia from here 
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Kill X ctrl-alt-backspace or use ctrl-alt-F1 and type 
```
$ sudo killall /etc/init.d/gdm
```
Install the Nvidia Driver from tty1
```
$ sudo sh NVIDIA-Linux-x86-1.0-8756-pkg1.run
```
When it asks you if you would like it to make the new xorg.conf choose yes. it only changes the Nvidia driver specs.
restart X
```
$ sudo /etc/init.d/gdm restart
```

finally loading the Windows partitions
to solve this edit /boot/grub/menu.lst
```
$ sudo gedit /boot/grub/menu.lst
```
in this line
> /boot/vmlinuz-2.6.16 root=/dev/hdb1 ro quiet splash
remove the ro so you have this
> /boot/vmlinuz-2.6.16 root=/dev/hdb1 quiet splash

save and reboot and now you will be able to load the Windows partitions.

---

### Post by glaze on 2006-04-24
[QUOTE=dvader]master C

root@local:/home/harry#  sudo make xconfig
make: *** No rule to make target `xconfig'.  Stop.
root@local:/home/harry#  cd /usr/src/linux
root@local:/usr/src/linux#  sudo make xconfig
scripts/kconfig/qconf arch/i386/Kconfig
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

qconf: cannot connect to X server :0.0
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2
root@local:/usr/src/linux# 

I installed kdee libs , still get the error message 

Assistance appreciated

Dvader[/QUOTE]

You should not be root at this point.

---

### Post by la3r on 2006-04-24
Im not sure what processor family mine is so please help, it is a 
"Intel Celeron M 380 1.6GHz"

---

### Post by Trunkz on 2006-04-24
I still need the linux headers for the 2.6.16-ck3 kernel =/ Following the ndiswrapper guide just tells me that apt-get cant find that package.

---

### Post by Don_Toni on 2006-04-24
Please help me, this screan i see every time when I reboot my Ubunti 5.10, I'v got this problem since I install the new kernel .[IMG]http://dontoni.net/gallery/albums/userpics/10001/normal_DSC00493.JPG[/IMG]

---

### Post by Efwis on 2006-04-24
[quote=la3r ] 	Im not sure what processor family mine is so please help, it is a
"Intel Celeron M 380 1.6GHz"[/quote]

you would just choose the Pentium M option if you are doing your own compilation.

[quote=Trunkz] 	I still need the linux headers for the 2.6.16-ck3 kernel =/ Following the ndiswrapper guide just tells me that apt-get cant find that package.[/quote]]
Trunks, the headers will be located in /usr/src/linux-2.6.16-ck3, providing this is where you put that patch when you compiled it. you will have to manually tell the ndiswrapper where to look for them using this arguement
```
ln -s /usr/src/linux-2.6.16-ck3 /lib/modules/2.6.16-ck3/build
```
Then start your normal installation process.

[quote=Don_Toni]Please help me, this screan i see every time when I reboot my Ubunti 5.10, I'v got this problem since I install the new kernel [/quote]

boot your system to the new kernel, when that screen pops up, use the down arrow key to look for the entry that has [**] in front of it. then tell us what that line was. Usually xorg.conf will pop that up under one of two reason. Mouse Driver problems or Graphics card problems. Let us know where the errors are exactly and we can help you out better.

---

### Post by Trunkz on 2006-04-24
Thanks, although I dont think the laptop liked that kernel.. It suddenly shut off twice o.O Might try ck7, anyone had any luck with that patch?

---

### Post by Efwis on 2006-04-24
[QUOTE=Trunkz]Thanks, although I dont think the laptop liked that kernel.. It suddenly shut off twice o.O Might try ck7, anyone had any luck with that patch?[/QUOTE]
good luck, i personally don't do the patch system to upgrade my kernel, I had to compile my kernel from source so that certain things worked properly. I am running the latest Kernel even though it only shows as 2.6.16 :)

The original Ubuntu Kernels aren't coded properly to support my mouse, plus they are way to bloated with stuff I don't need. :mrgreen:

---

### Post by xXx 0wn3d xXx on 2006-04-24
[QUOTE=Trunkz]Thanks, although I dont think the laptop liked that kernel.. It suddenly shut off twice o.O Might try ck7, anyone had any luck with that patch?[/QUOTE]
I would recommend compiling the latest kernel, and not using any patches. Sometimes patching a kernel can go horribly wrong...and in response to your other question, you don't need the kernel headers for your wifi card. And for anyone who wanted to know, the new 2.6.16.10 kernel is out.

---

### Post by Efwis on 2006-04-24
[QUOTE=MasterChief1234]And for anyone who wanted to know, the new 2.6.16.10 kernel is out.[/QUOTE]
actually I was just looking at Kerenl.org. Latest stable is 2.6.16.11 released today. thats at least if you want to compile your own kernel from source. I'll probably install it tomorrow :)

---

### Post by John64 on 2006-04-24
Whats the difference between all the ck#'s???

I see ck3 and ck7 most often.  i am running ck3 right now but i dont mind redoing it if its better.  btw, this is SOO much faster than the stock kernel!

---

### Post by Efwis on 2006-04-25
[QUOTE=John64]Whats the difference between all the ck#'s???

I see ck3 and ck7 most often.  i am running ck3 right now but i dont mind redoing it if its better.  btw, this is SOO much faster than the stock kernel![/QUOTE]
only true answer to that is by looking at the changelog to see what has been fixed because of bug reports.

From looking at the changelog for 2.6.16.11 kernel, I have decided there isn't enough difference for me to update mine. The bug fixes that they have added to the kernel were mostly specialized fixes for settings that don't affect me. About the only thing in the changelog is a bug fix in regards to ip6v4tables.

---

### Post by Don_Toni on 2006-04-25
[QUOTE=Efwis]boot your system to the new kernel, when that screen pops up, use the down arrow key to look for the entry that has [**] in front of it. then tell us what that line was. Usually xorg.conf will pop that up under one of two reason. Mouse Driver problems or Graphics card problems. Let us know where the errors are exactly and we can help you out better.[/QUOTE]
Thank you for atention Efwis, I'v done what you say, but I see a new pop screen:
> The X server is now disabled. Restart GDM when it is configured correctly.](*,)

---

### Post by LordMau on 2006-04-25
Hello!

Just installed 2.6.16 ck7 here. Seems ok but I do get the following message at boot and if if try to manually start ALSA:

```

 * Setting up ALSA...                                                                          * /etc/init.d/alsa-utils: Warning: 'alsactl restore' failed with error message 'alsactl: set_control:894: warning: name mismatch (Mic Boost/Mic Boost Playback Switch) for control #22
alsactl: set_control:896: warning: index mismatch (0/0) for control #22
alsactl: set_control:898: failed to obtain info for control #22 (Broken pipe)'.

```

During menuconfig for sound devices I intentionally left OSS unchecked.

What can solve this?

TIA.

---

### Post by LordMau on 2006-04-25
Scratch that, now works after reinstalled in synaptic alsa base, utils, et al then rebooted. Not sure if I needed to reinstall, maybe the reboot would have been enough.

---

### Post by Didjit on 2006-04-25
[I]Running the new kernel, I'm having troubles mounting additonal EXT3 drives. These are my FSTAB entires.

 /dev/hdb1 /media/max250 ext3    defaults,errors=remount-ro 0       1
 /dev/hdd1 /media/max60 ext3    defaults,errors=remount-ro 0       1

When I try to manually mount, it tells me /dev/hdb1 is busy or already mounted. However, its not. Also, using Gnome - System->Adminstration->Disks show the drive is not mounted, when I try to Enable, nothing happens.

 Any help would be appreciated. I did run into the initial VMWare issues too, not sure if VMWare messes w/fstb....

 Tx

 Didjit

[/I]Did more digging and found this: [http://evms.sourceforge.net/faq.html](http://evms.sourceforge.net/faq.html)
As a quick fix I edited /etc/evms.conf
Under ** sysfs_devices **polutated the ie "exclude = [hdb* hdd* ]

Now my drives mount ok. 

Didjit

---

### Post by Efwis on 2006-04-25
[QUOTE=Don_Toni]Thank you for atention Efwis, I'v done what you say, but I see a new pop screen:
](*,)[/QUOTE]
At this point I would recommend compiling your own kernel from scratch. It's not as hard as you think and there is a great guide for helping you along the way. The nice part is you can do it all while in the old kernel.

download the source from [http://www.kernel.org](http://www.kernel.org) get the latest version, not the patch but the actual kernel source.

Then go to this site and follow the instructions posted there. 

[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html)

You can skip the part in regards to apply the patch. Replace all instances of 2.6.0 that he uses in the guide to 2.6.16.xx.xx also make sure you download and install initrdtools from synaptic if you want to use the initrd image like like Ubunutu installs, although you don't have to use it.

if you run into problems feel free to pm me for help, I've done this 4 times in the last two months for different computers.

---

### Post by ashrack on 2006-04-26
Ive compiled a far amount of kernels so am not a total NEWBIE. 
When I compiled the 2.6.16 kernel my network card isnt working anymore.

And I believe that because there is no module for:
```
forcedeth
```
Which is the module my nForce2 NIC is using. And I checked the DAPPER's original kernel's CONFIG list and there module 'forcedeth' is specified. But with the new 2.6.16 kernel that module doesnt exist anymore...
What am I suppose to do?

---

### Post by Efwis on 2006-04-26
[QUOTE=ashrack]Ive compiled a far amount of kernels so am not a total NEWBIE. 
When I compiled the 2.6.16 kernel my network card isnt working anymore.

And I believe that because there is no module for:
```
forcedeth
```
Which is the module my nForce2 NIC is using. And I checked the DAPPER's original kernel's CONFIG list and there module 'forcedeth' is specified. But with the new 2.6.16 kernel that module doesnt exist anymore...
What am I suppose to do?[/QUOTE]
open terminal and type 
```
lspci
```
post the contents here.

---

### Post by ashrack on 2006-04-26
[QUOTE=Efwis]open terminal and type 
```
lspci
```
post the contents here.[/QUOTE]
```
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:0a.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800]
0000:02:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800] (Secondary)
```

---

### Post by Efwis on 2006-04-26
[QUOTE=ashrack]```
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:0a.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800]
0000:02:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800] (Secondary)
```[/QUOTE]
have you tried to install it by using modprobe?

```
modprobe forcedeth
```

---

### Post by f3tus on 2006-04-26
I downloaded 2.6.16-11 and compiled it without a patch. Can I somehow add the kc7 patch now?

---

### Post by Efwis on 2006-04-26
[QUOTE=f3tus]I downloaded 2.6.16-11 and compiled it without a patch. Can I somehow add the kc7 patch now?[/QUOTE]
you don't need to add the patch, 2.6.16-11 already has the patch in place.

---

### Post by ashrack on 2006-04-27
[QUOTE=Efwis]have you tried to install it by using modprobe?

```
modprobe forcedeth
```[/QUOTE]

```
tom@tom:~/network$ modprobe forcedeth
FATAL: Module forcedeth not found.

```

ps. ATM I am using NVNET driver from NVIDIA for my NIC. But I would still like to get the open source driver working. And Ive also recompiled the kernel 3times and its all the same.

-------
FOUND A FIX:
When crating kernel I disabled:
Prompt for development and/or incomplete code/drivers
which doesnt show experimental drivers

---

### Post by zasf on 2006-04-28
To the people who normally compile their own kernel: do you usually download the source from kernel.org or do you use ubuntu kernel source?

I strongly beleive that ubuntu kernel source (the one you get with linux-source packages) is stronly patched. 

If you compile source from kernel.org some functionalities are missing, ie cdrom, usb support, etc even if you do ```
sudo cp /boot/config-2.6.14-ck1 .config
```

Note that I'm not talking about restricted modules (fglrx, madwifi, ipw2200, etc)
It is not a matter of configuration but source and how this works with the other packages.

---

### Post by daboochmeister on 2006-04-28
I'm confused, and can't find the answer on kernels.org -- do the stable releases available there always include the Con Kolivas patches up to that point?  E.g., i just built 2.6.16.11 -- does it have all the ck performance improvements in it already?

I did see the post earlier mentioning that ck7 is included in whatever release the asker was building -- but I wasn't sure if it's always true, or if on a case-by-case basis it can still be worth applying a ck patch.  The kernel changelogs don't seem to say one way or the other.

---

### Post by geearf on 2006-04-28
no ck patch is included in the vanilla kernel you'll find on kernel.org

---

### Post by Defscanguci on 2006-04-29
After a couple hours of debugging, I finally got the package to be built. After trying to install with DebInstaller, I got this:
[COLOR="Red"]
The link /initrd.img is a dangling linkto /boot/initrd.img-2.6.16-ck3
Searching for GRUB installation directory ... found: /boot/grub .

DebInstaller used the command:
dpkg --status-fd 1 -i /usr/src/kernel-image-2.6.16-ck8_ck8_i386.deb[/COLOR]

I know it's got to do something with the link, but I don't know where to change that. Any ideas would be greatly appreciated.

Edit: OK, I fixed that by deleting the Modules folder from a previous attempt. Now I just need help with configuring the ck8 patch. Is there any place that tells exactly what *every* specific configuration is for? A lot of the infor in the GUI just...isn't helpful.

---

### Post by ashrack on 2006-04-29
[QUOTE=zasf]To the people who normally compile their own kernel: do you usually download the source from kernel.org or do you use ubuntu kernel source?

I strongly beleive that ubuntu kernel source (the one you get with linux-source packages) is stronly patched. 

If you compile source from kernel.org some functionalities are missing, ie cdrom, usb support, etc even if you do ```
sudo cp /boot/config-2.6.14-ck1 .config
```

Note that I'm not talking about restricted modules (fglrx, madwifi, ipw2200, etc)
It is not a matter of configuration but source and how this works with the other packages.[/QUOTE]
UBUNTU's kernel is patched pretty heavily. DApper will be run by kernel 2.6.15. But in that kernel also patches from 2.6.16 kernel are already applied.

But if U use the VANILLA kernel U get a bear bone kernel. Without any performance or other patches whatsover. Thats why we usually apply CK or ARCHCK's patches

---

### Post by zasf on 2006-04-29
[QUOTE=ashrack]UBUNTU's kernel is patched pretty heavily. DApper will be run by kernel 2.6.15. But in that kernel also patches from 2.6.16 kernel are already applied.[/QUOTE]

That means that if you're running dapper, it doesn't make any sense to compile 2.6.16 source from kernel.org, because it won't improve performance and you'll have problems with cdrom, usb, etc

---

### Post by chucktg on 2006-04-29
Great guide:D 
Compiled 2.6.17rc3 in dapper and everything flys now. Much faster:) 
Had to do some messing around with config to get firestarter to work but other then that everything works great.

---

### Post by thasheep on 2006-04-30
[edit: improved 20060501]
I have a habit of testing and compiling various kernels and normally I apply various patches/patchsets. Patching the source can be annoying sometimes so I wrote a bash script to semi-automate the process. You tell it the name of the source tarball (.tar.bz2 or .tar.gz), where to unpack it, what patches (.patch, .gz or .bz2) to apply (in order) and finally what to rename the source directory because if you're patching a 2.6.16 source up to 2.6.17-rc2-mm1 and then applying your own patches, you'll probably want to call it something else. It makes some basic sanity checks but it's not quite foolproof. I suggest saving it to /usr/local/bin/unpackkernel and marking it executable (sudo chmod 755 /usr/local/bin/unpackkernel). Call it with no arguments for the correct syntax (or look at the top few lines of the script)
```

#!/bin/bash

if (( $# < 3 )) ; then
  echo "Call script as:"
  echo "$0 LINUX_ARCHIVE TARGET_DIR KERNEL_DIR [PATCH1 [PATCH2 ...]]"
  exit
fi

ARCHIVE=$1
if ! [ -f $ARCHIVE ] ; then
  echo "Archive $ARCHIVE does not exist"
  ERR=1
fi

if [ -d $2 ] ; then
  if [ -w $2 ] ; then
    SRC_DIR=$2
  else
    echo "Error: Target directory $2 is not writable!"
    ERR=1
  fi
else
  echo "Error: Target directory $2 does not exist!"
  ERR=1
fi

KNN=$3

shift; shift; shift

THISDIR=`pwd`

PATCHES=""
for i in $* ; do
  if [ `basename $i` == `basename $i .patch` ] && [ `basename $i` == `basename $i .gz` ] && [ `basename $i` == `basename $i .bz2` ] ; then
    echo "Error: Invalid patch $i!"
    echo "Patch must have suffix .patch, .gz or .bz2"
    ERR=1
  elif [ -f $THISDIR/$1 ]; then
    PATCHES="$PATCHES $THISDIR/$1"
  elif [ -f $1 ]; then
    PATCHES="$PATCHES $1"
  else
    echo "Error: patch $1 does not exist!"
    ERR=1
  fi
  shift
done

if [ $ERR ] ; then
  exit 1
fi

echo "all's good"

echo -n "Unpacking $ARCHIVE... "
if [ `basename $ARCHIVE` != `basename $ARCHIVE .tar.bz2` ] ; then
  KERNELDIR=$SRC_DIR/`basename $ARCHIVE .tar.bz2`
  tar -C $SRC_DIR -jxf $ARCHIVE || exit
elif [ `basename $ARCHIVE` != `basename $ARCHIVE .tar.gz` ] ; then
  KERNELDIR=$SRC_DIR/`basename $ARCHIVE .tar.gz`
  tar -C $SRC_DIR -zxf $ARCHIVE || exit
else
  echo
  echo "Error: $ARCHIVE is not a recognised archive."
  echo "Must be .tar.bz2 or .tar.gz"
  exit 1
fi
echo "done"

cd $KERNELDIR
KERNELDIR=`pwd`

# Apply patches
for PATCH in $PATCHES
do
  echo -n "Applying $PATCH... "
  if [ `basename $PATCH` != `basename $PATCH .patch` ] ; then
    cat $PATCH | patch -s -p1 || exit
  elif [ `basename $PATCH` != `basename $PATCH .gz` ] ; then
    zcat $PATCH | patch -s -p1 || exit
  elif [ `basename $PATCH` != `basename $PATCH .bz2` ] ; then
    bzcat $PATCH | patch -s -p1 || exit
  fi
  echo "done"
done

cd .. && mv $KERNELDIR $KNN

echo "All done"

```

---

### Post by Efwis on 2006-05-01
[QUOTE=zasf]To the people who normally compile their own kernel: do you usually download the source from kernel.org or do you use ubuntu kernel source?

I strongly beleive that ubuntu kernel source (the one you get with linux-source packages) is stronly patched. 

If you compile source from kernel.org some functionalities are missing, ie cdrom, usb support, etc even if you do ```
sudo cp /boot/config-2.6.14-ck1 .config
```

Note that I'm not talking about restricted modules (fglrx, madwifi, ipw2200, etc)
It is not a matter of configuration but source and how this works with the other packages.[/QUOTE]
I will only compile from source at Kernel.org. I think patching is overstated. I compiled my Kernel from the source, and have never had any issues in regards cdrom, usb, etc.. they all worked like the original Kernel that was installed with ubuntu did. Also, in my case, if I used the source files from Ubuntu, certain parts of my computer don't work. mouse, video, Keyboard extras, webcam, and microphone.
I use my computer for my business, if I had to rely on the Ubuntu kernel only, I would not use Ubuntu, I would go through the process of using Linux from Scratch.

---

### Post by zerocapacity on 2006-05-01
hey guys I new to ubuntu and am having fun with this. I have figured my way through it thus far with the help of many great posters and responders in this communtiy. 

I have run into one problem though this line here

sudo apt-get install libqt3-headers libqt3-mt-dev

returns the error =  libqt3-mt-dev: Depends: xlibs-static-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libmng-dev (>= 1.0.3) but it is not going to be installed
                 Depends: libpng12-0-dev
                 Depends: zlib1g-dev but it is not going to be installed
                 Depends: libfreetype6-dev but it is not going to be installed
                 Depends: libxft-dev but it is not going to be installed

now When I try to install these I get this error =@ubuntu:~$ sudo apt-get install libqt3-headers libqt3-mt-dev xlibs-static-dev libmng-dev libmng-dev libpng12-dev zlib1g-dev lib freetype6-dev libxft-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package lib


: Note I changed the libpng12-0-dev to libpng-dev because it told me to


I will appreciate any help in this matter and hope to help others as I get to know this wonderful OS.

Thanks

Z

---

### Post by thasheep on 2006-05-01
In short, I suggest skipping the `apt-get install bqt3-headers libqt3-mt-de` step and instead of `sudo make xconfig`, do `sudo make gconfig`. More detailed explanation follows.

I suspect the problem could lie in mixed repositories or bad apt-pinning. But, libqt3-headers isn't needed unless you want to do `make xconfig`. That method of kernel configuration relies on the qt libraries, upon which kde is partly built. `make gconfig` will work fine without it and is probably a better choice anyway if you're running ubuntu (gnome) rather than kubuntu (kde). The console-based `make menuconfig` doesn't need it either but you might need to get libncurses5-dev if you don't already have it.

---

### Post by zerocapacity on 2006-05-01
Thank you for the quick response and I will try this right now

---

### Post by zerocapacity on 2006-05-01
still the same crap now I am running into not having gtk installed but it is kinda wierd no?


Z

Edit NVM saw the menuconfig and did that

Thanks

Z

---

### Post by ninocass on 2006-05-03
Thanks for the guide it worked a treat and everything runs faster but i seem to be having a probelm with my wireless {ipw2200}

I have followed the help section at the bottom of the first post and installed the latest version of ndis wrapper

i did something along the lines of:

```

ndiswrapper -i w22n51.INF

sudo rmmod ipw2200

modprobe ndiswrapper


```

at the last command it reports that ndiswrapper is not present.

Im i going along the right lines here?

---

### Post by Efwis on 2006-05-03
[QUOTE=ninocass]Thanks for the guide it worked a treat and everything runs faster but i seem to be having a probelm with my wireless {ipw2200}

I have followed the help section at the bottom of the first post and installed the latest version of ndis wrapper

i did something along the lines of:

```

ndiswrapper -i w22n51.INF

sudo rmmod ipw2200

modprobe ndiswrapper


```

at the last command it reports that ndiswrapper is not present.

Im i going along the right lines here?[/QUOTE]
From the looks of it you need to recompile ndiswrapper. that statement will only occur if the file isn't compiled and installed.

---

### Post by razahel on 2006-05-03
Hi I do not know if someone hat the same problem before so:
I've tried so compile the new 2.6.16 kernel from kernel org together with the fglrx source available for dapper and the fglrx fails with following error:

Kernel compiler version : 4.0.3
Detected compiler version : 4.0.3
Using compiler gcc-4.0 version 4.0.3
touch /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/gcc-check
touch /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/cc-sanity-check
## Main Make ##
IGNORE_CC_MISMATCH=1 CC="gcc-4.0"  /usr/bin/make -C /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x -f Makefile SYSSRC=/usr/src/linux   KBUILD_PARAMS="-C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x"
make[3]: Entering directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[3]: Makefile: Datei oder Verzeichnis nicht gefunden
make[3]: *** Keine Regel, um »Makefile« zu erstellen.  Schluss.
make[3]: Leaving directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'make[2]: *** [build-stamp] Fehler 2
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel'
make[1]: *** [kdist_image] Fehler 2
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.

---

### Post by raid517 on 2006-05-06
Why have you got a link to kernel 2.6.16.7 on the top of your guide? Is it needed for anything? There doesn't seem to be any explanation for it being there. First you say the performance patches should only be applied to a clean 2.6.16 kernel - then you mysteriously link to  2.6.16.7 (on rapidshare of all places - which never works for me anyway (at least not without demanding money). Why link a Kernel to a notorious warez and virus commercial download web site, when you can obtain it directly from Kernel.org FTP? And as I said, what is the point in linking to it anyway?

GJ

---

### Post by neoaddict on 2006-05-06
What unneeded files can I remove?  

I only have a 3.2 GB hard drive, and there's only 380 MB of space left of it, so I really want to delete as much garbage as I can.

---

### Post by Resurrection on 2006-05-07
Not a bad guide.  THIS WAS MY FIRST KERNEL COMPILE!!!!!! :p  I just installed a vanilla kernel 2.6.16.14 from kernel.org.  Latest stable release as of yesterday.  Since I did it that way, I didn't patch the kernel and skipped that step.  

Only problem I had was the issue of changing my graphics driver over to the regular "nv" one for my nVidia card.  When I finished installing my compiled kernel and restarted, it crashed the Xserver, and all I got was a CLI.  I had to go to /etc/X11 and edit the xorg.conf file, as mentioned in one of the other kernel compiling threads the guide links to.

I do have a few recommended changes to make the guide better though:
1)  Step 6 doesn't seem required.  Especially if you are compiling the latest version and not patching.

2)  Step 7 should be more clear.  Noobs like me have to read up on symbolic links in order to understand what you are doing here.  Again, this seems like an unnecessary step since most people probably won't have a "linux" link in that directory.  Maybe I'm wrong on that though.

3)  After Step 10, no more need to sudo since you are root.

4)  In Step 14 you say:  
> In "Device drivers" go to "Block devices" and in "IO Schedulers" leave only the "CFQ I/O scheduler" activated, which provides the best performance.

I had no entry for IO Schedulers under Block devices in the config window.  Am I crazy and can't see it, or is this been changed with the kernel version I am using?

And only other change I would recommend is remind people about the graphics card issue at the beginning that I mentioned above.

But still a good guide.  Thanks for the hard work and help.

---

### Post by Resurrection on 2006-05-07
[QUOTE=neoaddict]What unneeded files can I remove?  

I only have a 3.2 GB hard drive, and there's only 380 MB of space left of it, so I really want to delete as much garbage as I can.[/QUOTE]
In my case, I deleted the kernel tar.bz2 file that I first downloaded (it was on my Desktop).  Then I went into /usr/src and deleted these files:
linux-2.6.16.14
linux
linux-2.6.16.14.tar.bz2

I left the kernel-image .deb file in there, although I think you can get rid of that one as well.  I will wait for someone else to confirm however.

---

### Post by neoaddict on 2006-05-07
So you deleted the linux "shortcut" folder?

---

### Post by Resurrection on 2006-05-07
Yes, I deleted the symbolically linked "linux" directory.  I figured that since I had successfully compiled the kernel package and that installed without any issues, that I did not need the source code files or the directory they were uncompressed into anymore.

I am not an expert though, so don't blame me if I totally screwed it up.  I was taking the common sense approach which isn't always guaranteed to be right.

---

### Post by neoaddict on 2006-05-07
OK.

Is there any way I can delete the old kernel?

---

### Post by xXx 0wn3d xXx on 2006-05-07
[QUOTE=neoaddict]OK.

Is there any way I can delete the old kernel?[/QUOTE]
In synaptic search for the kernel and then make it for removal. I would however recommend using the new kernel as your primary kernel and the old one as your "safe kernel" in case anything ever goes wrong.

---

### Post by xXx 0wn3d xXx on 2006-05-07
My custom compilied kernels for AMD processors are up there are two seperate kernels. There is an smp version and a regular version. I uploaded them to rapidshare because I don't have another host. I have sucessfully tested the non-smp version on an AMD processor running 32-bit Ubuntu 6.06 Beta 2 Dapper Drake. Please leave feedback on them :)

---

### Post by neoaddict on 2006-05-07
I'll backup the hard drive of my Linux computer into an archive and put it on my Windows computer (with 6 GB of free space left).

Also, can I apply the latest kernel patches from Synaptic or no?  Thinking no because they're for 2.6.12....

---

### Post by Fedcer on 2006-05-07
[QUOTE=Resurrection]
I had no entry for IO Schedulers under Block devices in the config window.  Am I crazy and can't see it, or is this been changed with the kernel version I am using? [/QUOTE]

In the kernel 2.6.16.14 the "IO Schedulers" can be found under the "Block Layer" menu.

---

### Post by Resurrection on 2006-05-08
[QUOTE=Fedcer]In the kernel 2.6.16.14 the "IO Schedulers" can be found under the "Block Layer" menu.[/QUOTE]
Yeah , I figured that out after I read this thread a little more carefully....D'oh.

Thanks though.

---

### Post by geearf on 2006-05-08
[quote=Resurrection]Yes, I deleted the symbolically linked "linux" directory.  I figured that since I had successfully compiled the kernel package and that installed without any issues, that I did not need the source code files or the directory they were uncompressed into anymore.

I am not an expert though, so don't blame me if I totally screwed it up.  I was taking the common sense approach which isn't always guaranteed to be right.[/quote]

Well now you cannot install any module related to the kernel.
If you wish to install one, you will have to recompile the kernel to reget the same sources.

---

### Post by geearf on 2006-05-08
By the way, like a lot of distros are having, we should have a repos from user packages, and put there a few optimized kernels, so that it gets automagically updated, and so that there is no need for everyone to build their own.
I'm thinking of that because I'm also an Arch user, and my beyond kernel is getting upgraded often without me doing anything so I'm quite happy with that :)

---

### Post by Sokraates on 2006-05-08
That would be a great idea. Now all we need is a host and lots of bandwith, since most ubuntu-users will certainly want to update to the latest kernel.

But seriously. Before opening a repo, there should be criteria on who can upload new kernels and how they need to be checked before released to the public.

---

### Post by geearf on 2006-05-08
I agree, but we would need a community repos not only for the kernel, but maybe for some other packages.

It should be maintained by a team, for the BP and space that would be the hard part.

---

### Post by xXx 0wn3d xXx on 2006-05-08
[QUOTE=geearf]I agree, but we would need a community repos not only for the kernel, but maybe for some other packages.

It should be maintained by a team, for the BP and space that would be the hard part.[/QUOTE]
That would be cool but I think that only the new release cycles of the kernels would be in the repos (ex: 2.6.15, 2.6.16 not 2.6.16.12) that would leave time to experment with the other kernels and make/apply patches. Although I think that it is a good idea I doubt it would happen but it might.

---

### Post by Resurrection on 2006-05-08
[QUOTE=geearf]Well now you cannot install any module related to the kernel.
If you wish to install one, you will have to recompile the kernel to reget the same sources.[/QUOTE]
Well since this was my first kernel compile, I didn't know anything about what you are talking about.  Can you give me some examples of what you mean?  I saw in the how-tos about compiling restricted modules along with the kernel, but I didn't quite get what it was saying.  Maybe you can explain some more or point me in the right direction?

---

### Post by geearf on 2006-05-09
@MasterChief1234 : Well let's hope, but we should have one community repos if we want ubuntu to be a community distro and not only canonical's one.

@Resurrection : Well now you should not be able to install something like NVIDIA/ATI drivers and such, because those need either the kernel sources or kernel headers to compile against.

But if you don't need those and you don't compile too much things you should be safe.

---

### Post by Resurrection on 2006-05-09
[QUOTE=geearf]
@Resurrection : Well now you should not be able to install something like NVIDIA/ATI drivers and such, because those need either the kernel sources or kernel headers to compile against.

But if you don't need those and you don't compile too much things you should be safe.[/QUOTE]
Well I still don't understand the whole restricted modules compiling thing.  How do you compile restricted modules, are they part of the kernel compile or just some kind of secondary operation you do after the kernel compile?  I don't expect you to give me a long drawn out explanation, perhaps just quote me something from a web page or point me in the direction of something that can explain restricted module compiling.

---

### Post by Steve1961 on 2006-05-09
I've just installed dapper beta 2 and decided to use a 2.6.16 kernel I compiled in Mepis (the ubuntu alpha version) as it ran really well in Mepis, and the same config also works well in slackware.  The problem: the ip tables issue mentioned in this thread and a failure to start the enterprise volume manager on boot (with the result that I can't mount a fat32 partition).  So I decided to follow this guide but got the same problem.  I tried using a patched vanilla kernel, an unpatched kernel, the config file from my existing ubuntu kernel, and a custom config file that's worked well in other distros.  Unfortunately nothing seemed to solve these issues.  I've reverted to the stock 686 dapper kernel - 2.6.15-22 - and everything works again, but has anyone got any ideas why this is happening?

---

### Post by xXx 0wn3d xXx on 2006-05-09
[QUOTE=Steve1961]I've just installed dapper beta 2 and decided to use a 2.6.16 kernel I compiled in Mepis (the ubuntu alpha version) as it ran really well in Mepis, and the same config also works well in slackware.  The problem: the ip tables issue mentioned in this thread and a failure to start the enterprise volume manager on boot (with the result that I can't mount a fat32 partition).  So I decided to follow this guide but got the same problem.  I tried using a patched vanilla kernel, an unpatched kernel, the config file from my existing ubuntu kernel, and a custom config file that's worked well in other distros.  Unfortunately nothing seemed to solve these issues.  I've reverted to the stock 686 dapper kernel - 2.6.15-22 - and everything works again, but has anyone got any ideas why this is happening?[/QUOTE]
There is a tutorial on how to get iptables to work with new kernels :) Check the first page of this thread. It's all the way on the bottom of the first post.

---

### Post by Steve1961 on 2006-05-09
[QUOTE=MasterChief1234]There is a tutorial on how to get iptables to work with new kernels :) Check the first page of this thread. It's all the way on the bottom of the first post.[/QUOTE]


Thanks, I saw that, but haven't tried it as my main concern is the enterprise volume manager issue.

---

### Post by geearf on 2006-05-09
[quote=Resurrection]Well I still don't understand the whole restricted modules compiling thing.  How do you compile restricted modules, are they part of the kernel compile or just some kind of secondary operation you do after the kernel compile?  I don't expect you to give me a long drawn out explanation, perhaps just quote me something from a web page or point me in the direction of something that can explain restricted module compiling.[/quote]
if you look at this page : [http://packages.ubuntulinux.org/dapper/base/linux-restricted-modules-686](http://packages.ubuntulinux.org/dapper/base/linux-restricted-modules-686)

you will see that restricted modules are modules that are not free, so they do not come with the kernel itself, but you can still compile them as another package.

Sorry it's a bit late, and I'm not thinking very right right now ...

---

### Post by Resurrection on 2006-05-09
I appreciate you sticking with me on this geearf.  I think I am very slowly getting the idea now, kind of like pounding a nail into my head.

[http://www.faqs.org/docs/Linux-HOWTO/Module-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/Module-HOWTO.html")

That site talks about LKMs (Loadable Kernel Modules).  Is that along the same lines as a restricted kernel module?  As I think I understand, a restricted module is one that must be compiled based on the kernel image you are using, but I don't get this:  Does that restricted module have to be done as part of the kernel compile or can it be done separately like a LKM?

---

### Post by neoaddict on 2006-05-09
Can I apply the latest kernel patches from Synaptic or no? Thinking no because they're for 2.6.12....

---

### Post by jdusablon on 2006-05-10
Wow! What a difference! Thanks, MasterChief1234! My system is pretty snappy now!

---

### Post by eproject on 2006-05-10
i try to compile new kernel by follow how to 2.6
mounting root file system.14 Vanilla kernel + ck Patchset like this

my labtop spec
ASUS M5200AE
Centrino 740 1.73GHz
512MB
Digital Flat Panel on Mobile intel(R) 915GM/GSM

sudo apt-get install build-essential bin86 kernel-package
sudo apt-get install libqt3-headers libqt3-mt-dev (needed for make xconfig) 
sudo cp linux-2.6.14.tar.bz2 /usr/src
cd /usr/src
sudo tar -xvjf linux-2.6.14.tar.bz2
sudo mv linux-2.6.14/ linux-2.6.14cK1
sudo rm -rf linux
sudo ln -s /usr/src/linux-2.6.14cK1 linux
cd /usr/src/linux
sudo -s -H
Password: <specify user password>
sudo bzcat /home/username/patch-2.6.14-ck1.bz2| patch -p1
sudo cp /boot/config-2.6.12-9-686 .config 
sudo make xconfig
(chang config:
In "General Setup" activate:
-Support for paging of anonymous memory (swap)
--Support for prefetching swapped memory
In "Processor type and features":
-Processor family Choose the model of your processor.
Activate:
-Preemption Model
--Voluntary Kernel Preemption (Desktop)
-High Memory Support
--off -if you have less than 1 GB of RAM
--1GB Low Memory Support -if you have 1GB of RAM
--4GB -if you have more than 1GB of RAM
-Timer frequency
--1000 Hz
In "Device drivers" go to "Block devices" and in "IO Schedulers" 
leave only the "CFQ I/O scheduler" activated, which provides the best performance.
In "Kernel hacking" uncheck "Kernel debugging".)

make-kpkg clean
make-kpkg -initrd --revision=ck1 kernel_image
sudo dpkg -i kernel-image-2.6.14*.deb
sudo reboot

but after i reboot my ubuntu ... it show me about can run new kernel
but after loading "Mounting root file system" .... it's hang, stop running and show problem

[IMG]http://juszt.exteen.com/images/Untitled-1%20copy.jpg[/IMG]

thank you

---

### Post by bepcyc on 2006-05-10
my problem is that I boot my breezy from usb hdd

so I need to build a special initrd image, because kernel need to wait about 10 seconds after inserting usb modules before it can mount root partition from usb hdd

I have a /etc/mkinitrd/mkinitrd.conf which worked with previous versions of kernel (from Ubuntu)

but with compiled 2.6.16 kernel it doesn't work

I do as usual
mkinitrd -o /boot/initrd-`uname -r`

everything ok here

but when I try to boot this kernel I get a lot of errors

it looks like 
> ... unknown filesystem type 'devfs' ...

what does it mean?
devfs is not in kernel, as far as I know

---

### Post by yoshic on 2006-05-10
thnks men, it worked perfect for me :KS thanks many thanks

---

### Post by Resurrection on 2006-05-10
Well after muching tweaking, reading, and learning, I have discovered that geearf was right, I do need to compile restricted modules with my kernel.  When I compiled my kernel before, it worked, but it was just a compile of the latest kernel with nothing else.  When I went to install the latest nVidia drivers, the little install script for it from nVidia would not let me because it couldn't find information on the kernel I compiled (looking for headers or something :-k ).  So I could only use the nVidia drivers that are in the repository.  

Then, my basic kernel did not support some of the things I like, like usplash and some other functionality.  So its back to learning for now until I figure out how to compile the kernel with restricted modules or whatever I need to do to make my own kernel work how I want it to.  Yes, I've read all the how tos on here I could find with regard to kernel compiling but they didn't help much with regard to restricted modules.

---

### Post by moore.bryan on 2006-05-10
*on kernel.org there a 2.6.16.15 and patch-2.6.16.15.  shouldn't that be used instead of the ck stuff?*

---

### Post by geearf on 2006-05-10
[quote=moore.bryan]*on kernel.org there a 2.6.16.15 and patch-2.6.16.15.  shouldn't that be used instead of the ck stuff?*[/quote]
why?

---

### Post by moore.bryan on 2006-05-10
[QUOTE=geearf]why?[/QUOTE]
*there's all this talk of the ck patch... but if kernel.org supplies something named a patch, shouldn't that be used?  maybe i just don't understand the whole ck part of the kernel update.*

---

### Post by geearf on 2006-05-10
well the patch from kernel.org takes you to the last kernel available that'is.
The ck patch, is a patchset to enhance your kernel, but as such thing it may not be stable, that is why it is not in the kernel yet...

---

### Post by moore.bryan on 2006-05-10
*i think i'm still at somewhat of a loss then.  there's a kernel (2.6.16.15.tar.gz) on kernel.org, a patch (patch-2.6.16.15.gz), and there's ALSO a ck?*

---

### Post by Resurrection on 2006-05-10
Unless I am mistaken the patch on kernel.org is only a patch for updating your kernel in that series with the latest stable updates.  

For example the patch-2.6.16.15.gz updates a 2.6.16.x kernel with the latest stable updates.  I know when I compiled my own kernel last, I used the 2.6.16.14 source and I tried to patch it with the patch-2.6.16.14.  It wouldn't patch properly, and I found out that this is because my source already had the improvements of the patch.

the ck patch on the other hand is not from kernel.org.  <- Ignore this, see next post (thx).
Its from [Con Kolivas]("http://members.optusnet.com.au/ckolivas/kernel/").  The ck patch you apply to the last new kernel but only to improve performance, so you would apply patch-2.6.16-ck10.bz2 to the kernel 2.6.16 but NOT to kernel 2.6.16.15.

Looking for a how-to that expains the kernel naming system right now........

Edit:  Good ole [Wikipedia]("http://en.wikipedia.org/wiki/Linux_kernel"):
> 
Version numbering

The version number of the Linux kernel currently consists of four numbers, following a recent change in the long-standing policy of a three-number versioning scheme. For illustration, let it be assumed that the version number is composed thus: A.B.C[.D] (e.g. 2.2.1, 2.4.13 or 2.6.12.3).

    * The A number denotes the kernel version. It is changed least frequently, and only when major changes in the code and the concept of the kernel occur. It has been changed twice in the history of the kernel: In 1994 (version 1.0) and in 1996 (version 2.0).

    * The B number denotes the major revision of the kernel. Even numbers indicate a stable release, i.e. one that is deemed fit for production use, such as 1.2, 2.4 or 2.6. Odd numbers have historically been development releases, such as 1.1 or 2.5. They were for testing new features and drivers until they became sufficiently stable to be included in a stable release. This has changed with the Linux 2.6.x series, with new feature development going on in the same kernel series. Linus Torvalds has stated that this will be the model for the foreseeable future.

    * The C number indicates the minor revision of the kernel. In the old three-number versioning scheme, this was changed when security patches, bugfixes, new features or drivers were implemented in the kernel. With the new policy, however, it is only changed when new drivers or features are introduced; minor fixes are handled by the D number.

    * A D number first occurred when a grave error, which required immediate fixing, was encountered in 2.6.8's NFS code. However, there were not enough other changes to legitimize the release of a new minor revision (which would have been 2.6.9). So, 2.6.8.1 was released, with the only change being the fix of that error. With 2.6.11, this was adopted as the new official versioning policy. Bug-fixes and security patches are now managed by the fourth number, whereas bigger changes are only implemented in minor revision changes (the C number).

Also, sometimes after the version there will be some more letters such as 'rc1' or 'mm2'. The 'rc' refers to release candidate and indicates a non-official release. Other letters are usually (but not always) the initials of a person. This indicates a slight fork of the kernel by that person. e.g. ck stands for Con Kolivas, ac stands for Alan Cox, whereas mm stands for Andrew Morton.

---

### Post by thasheep on 2006-05-11
[QUOTE=Resurrection]the ck patch on the other hand is not from kernel.org.
Its from [Con Kolivas]("http://members.optusnet.com.au/ckolivas/kernel/").[/quote]
It's not talked about on the front page, but the CK patches are hosted by kernel.org (just look at the URL of the download links from Con's webpage). Here're all his 2.6.16 patches [http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/)

---

### Post by Resurrection on 2006-05-11
[QUOTE=thasheep]It's not talked about on the front page, but the CK patches are hosted by kernel.org (just look at the URL of the download links from Con's webpage). Here're all his 2.6.16 patches [http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/)[/QUOTE]
Your right, I fixed what I said.  At least most of the rest was correct though.

---

### Post by Bokonon on 2006-05-11
The ck patches seem closely linked to the main patches anyway.

[Check Here]("http://members.optusnet.com.au/ckolivas/kernel/")

As of the time of my writing this, the 2.6.16.14 patches are included in the ck10 patch, which I downloaded.  Thus, you can take the base 2.6.16 kernel and just apply the ck patches and get nearly everything that the main ones have, plus his custom mods for performance.

I guess it is just personal preference,&#12288;but it seems that most people like the ck patches so I went with those.  The best route would be to compile both sets and benchmark to see which ones work best for your particular configuration.  :cool:

Oh yeah, and thanks to the OP for a great how to!!

---

### Post by moore.bryan on 2006-05-11
*bokonon, i think you read my mind; my next question was about which to use.  thanks to all who contributed to my little sub-thread.  i started compiling late last night and fell asleep on the keyboard.  i hope to reboot into a speedy kernel this evening...:p*

---

### Post by neoaddict on 2006-05-11
What specific packages would I have to remove in Synaptic to remove the old kernel?

---

### Post by bepcyc on 2006-05-12
Did anyone have a problem with usb mounting in kde?

In my case, when I insert a pendrive it shows me standard pop-up where I select to open my flash in a new window

and after it konqueror shows me that he is waiting for something (mounting of flash, I guess), but it doesn't happen ;(

anyway, the flash is mounted after it, but I can't get it with media:/mydevice, only with standart /media/mydevice


did anyone solve this problem?

---

### Post by Resurrection on 2006-05-12
[QUOTE=neoaddict]What specific packages would I have to remove in Synaptic to remove the old kernel?[/QUOTE]
Search in synaptic for something like "linux-image-2.6.12-10-386".  Obviously your kernel version may be different from that one.   Also, its been recommended by many people on here that if you custom compile your kernel that you keep at least one other stable kernel.  I had two stable kernels from Ubuntu install when I made my custom kernel.  So I just deleted the oldest of the installed kernels, but left one of them just in case.

---

### Post by BKK on 2006-05-12
Well this is my first time doing a new kernel. Things could be worse I guess.

- I can't access my second hard drive at all. It was hdb5 before. I have edited fstab as instructed on various forums here. Also when I am in dev/hdb5 no files show up ( the drive is fine in XP )

- I lost my sound! One guy said this upgrade fixed his sound! quite ironic eh?

- I lost my splash screen even after reinstalling in synaptic, it still wont show.

I am kinda stumped now! I am a noob, but kinda getting used to linux.

I hope someone can help out. Thanks

---

### Post by neoaddict on 2006-05-12
Splash screen - Open up Synaptic and reinstall usplash.

Sound - Search for your sound card on the forums.

---

### Post by play0r on 2006-05-13
ive troubleshot this down to a kernel issue. 
i believe i may have gone wrong in my menuconfig some where along the line. 
i have an intermitten network connection if i use the newer kernel. ive tried several things to resolve it (resolvconf etc etc, no pun intended). :-# 
it will randomly drop without rhyme or reason, any where from a few minutes to a day. i can ping my loopback & my own ip, but not the gateway or outside the gateway. when i try & bring my connection connection up with ifup/down or renew it with dhclient, i get an error about a temporary loss in name resolution. i have to reboot to regain a properly functioning connection again.
when i use the stock ubuntu kernel its fine.
thx in advance for any help.

ez,
play0r

---

### Post by Melvil on 2006-05-13
Hi everybody!

Great howto. I just compiled kernel 2.6.16.16 and it boots up fine, but I can't login from GDM. As soon as I enter my password and hit enter GDM just restarts.
I can't find any errors in Xorg.0.log or dmesg.

Any suggestions how to fix this?

/edit: Okay, suddenly it works :)
This kernel is bloody fast, application startup time is way superior to the dapper 2.6.15-22 kernel

---

### Post by geearf on 2006-05-13
I was thinking of trying this kernel, and from the last comment I definitely want to try it.

I'm thinking of giving a try to the beyond patch-set [http://iphitus.loudas.com/](http://iphitus.loudas.com/).
but nothing for .16, but I guess it's not so bad.

---

### Post by WishMaster on 2006-05-13
Before: standard Ubuntu kernel 2.6.12-10-686
Now: 2.6.16-ck3 - i686

- I don't notice any 'improvement'. No extra stability, no faster apps,...
- My webcam is recognized, but gives no image
- Usplash is gone (reinstalled it, have to reboot to check it out)
- My external HD shows up in /media, but there seems to be no auto-mounting (at least: the icons for usb-device don't show op on desktop)

I'm on an laptop with Centrino processor, so I chose "pentium M", but in the end it gave an *386.deb :-k

I'd say: stick with your default Ubuntu kernel, upgrading isn't worth it.

---

### Post by play0r on 2006-05-13
> i believe i may have gone wrong in my menuconfig some where along the line. 
i answered my own question. :-# 
sorry for the bump.

ez,
play0r

---

### Post by geearf on 2006-05-14
Well my kernel did not boot, problem loading modules.dep (I don't know why) and some problem with the IDE already registered.

I guess it was not a so good idea to customize all the options.

---

### Post by christhemonkey on 2006-05-14
I have the same problem as someone a page or so back.
When i try and login it just sends me straight back to the gdm.

They said that it just started working, but mine hasnt so far....

Nothing unusal in the xorg logs...

---

### Post by RavenOfOdin on 2006-05-14
My experience with the 2.6.16 kernel was as follows:

Last night, after a game of Wesnoth, I decided I'd put off upgrading the kernel long enough. So, I got the recent patch from kernel.org and the kernel from this HOWTO, and started updating. Followed every instruction to the letter, but when I hit "sudo make xconfig" things got a little crazy.

Xlib kept spitting notices back at me which said "Could not start X server on display 0:0" and after a look in Xorg.0.conf I saw that I was basically trying to audit the display via client.  So, I typed in "sudo make menuconfig" instead and my console, being small enough to satisfy a minimalist, whined at me with the words "Your terminal session must be 80X50 in size" (Or whatever the actual digits were, but I figure them to be somewhere around that.)  Then, I went to full screen mode.  

I wasn't able to find the prefetching option (this was the 2.6.16 kernel without patch, mind you) and I had to guess at a few other things. But eventually, I got the config done (with Processor Type as Athlon/K7) and thought I was through the worst of it.

Little did I know. :eek:

The compilation process was HORRIBLY long. And when I use the word "horribly" with only capital letters, I mean it!!  I started that step at 11:30 PM or so and got done with the compile + build roughly an hour later.  If it weren't so late at night I would have gone to find something decent on TV.

As for the rest of the process:

I hit a couple of snags with make-kpkg clean and deb file compilation, mostly due to my tiredness at that hour. . .

But eventually, it was done and the kernel was installed.

My performance was a lot faster, but I noticed that halfway through the boot process I was able to type at a blinking underscore. The typing didn't affect the boot process, but when HP Linux Printing and Imaging System started, I got a bunch of errors which said "Cannot set scancode (256)". . .Or, something to that effect.

I notice that now ALSA plays as default in Amarok. No more manually starting ESD in the background. Yay. :D

Just a question to anyone else that may have compiled this kernel -- What the blue hell is process "shpchpd_event" ? 

It was owned by root and in my process table, and I've never seen it up until last night.

@MasterChief1234: Thanks for writing this out.

Now. . .I'm going to have to patch it. I hope to God that the patch isn't as long as the kernel compilation was. ;)

[QUOTE=geearf]Well my kernel did not boot, problem loading modules.dep (I don't know why) and some problem with the IDE already registered.

I guess it was not a so good idea to customize all the options.[/QUOTE]

Ya think? :p

---

### Post by ashrack on 2006-05-14
[QUOTE=geearf]Well my kernel did not boot, problem loading modules.dep (I don't know why) and some problem with the IDE already registered.

I guess it was not a so good idea to customize all the options.[/QUOTE]

Yea I remember my first try outs. I always wanted to remove to much stuff. But after several retries U learn and its a smooth ride. And whats best is that my slimmed kernel only requires around 15min to compile. And even that time could be shortened  by removing even more unnecesary weed...

---

### Post by RavenOfOdin on 2006-05-14
[QUOTE=ashrack]Yea I remember my first try outs. I always wanted to remove to much stuff. But after several retries U learn and its a smooth ride. And whats best is that my slimmed kernel only requires around 15min to compile. And even that time could be shortened  by removing even more unnecesary weed...[/QUOTE]

:eek: 15 MINUTES?!?

You little! . . .
#^%! *&@# @#@# !! *&@# !! @#() $%!@ !! !!11!!!

*laughing like a maniac* :D

---

### Post by xXx 0wn3d xXx on 2006-05-14
[QUOTE=RavenOfOdin]:eek: 15 MINUTES?!?

You little! . . .
#^%! *&@# @#@# !! *&@# !! @#() $%!@ !! Ffff. . . !!!!!

*laughing like a maniac* :D[/QUOTE]
10-15 minute's is what I get too. I disable all uneeded features/modules and then my kernel size (this is the debian file built after complication) is about 10.46-11 mb compared to 13.7-16 MB. Disabling everything that is uneeded has alot of performance payoffs and faster compile times but don't go crazy with trying to minimize your kernel. Otherwise, it won't boot/cause alot of problems and you will waste all that saved time on compiling it again and figuring out what you did wrong. :)

---

### Post by RavenOfOdin on 2006-05-14
[QUOTE=MasterChief1234]don't go crazy with trying to minimize your kernel. Otherwise, it won't boot/cause alot of problems and you will waste all that saved time on compiling it again and figuring out what you did wrong. :)[/QUOTE]

That's very good advice.

BTW: The kernel update killed my ATI drivers.

---

### Post by RavenOfOdin on 2006-05-14
. . .Oops.

---

### Post by RavenOfOdin on 2006-05-14
Sorry for the double posts, someone delete this.

I can't believe my stupidity. >.<

---

### Post by geearf on 2006-05-14
kernel compilation here is more like 2 - 3 hours.
Even stripped a lot it was still way more than an hour (it was about 8Mb).
Maybe because of my comp (SDR is slow, and an FSB of 100 MHz too).

And because of that I don't try to build the kernel many times to get the right one, cause it is way too long :(

I may try again tomorrow to see how it goes this time.

---

### Post by CrashOverKill on 2006-05-14
Im compiling right now so far so good been runing about 20 minutes. I can recall back to a Intel Pentium with dual 200mghz CPU's and 64 megs of ram. Compiled my first kernel on it...........took 12 hours LMFAO!!!!!!!!!!!!!!!

---

### Post by Melvil on 2006-05-14
Damn, I thought the kernel update caused no problems, but my wireless interface is gone (ipw2200). It's compiled into the kernel, but this is the only message in dmesg:

> ipw2200: failed to register network device
ipw2200: probe of 0000:02:02:0 failed with error -5

sudo modprobe ipw2200 doesn't add anything to dmesg. Help! :(

---

### Post by Resurrection on 2006-05-14
I've done a couple now and thats about how long it takes me, usually about 2 hours even for a stripped down version.  Thats on a 1.2 Celeron with 512 Ram.  I stopped sitting there to see how long it takes now the best way I have found is to just set it up so that I start the actual compile when I go to sleep at night.  Then when I wake up, its all done, and I don't have to sit there and watch stuff scrolling in my terminal window.

---

### Post by xXx 0wn3d xXx on 2006-05-14
[QUOTE=Melvil]Damn, I thought the kernel update caused no problems, but my wireless interface is gone (ipw2200). It's compiled into the kernel, but this is the only message in dmesg:



sudo modprobe ipw2200 doesn't add anything to dmesg. Help! :([/QUOTE]
Did you compile the latest ndiswrapper from source ?

---

### Post by CrashOverKill on 2006-05-14
On a side note. When I loaded up Dapper my wifi card is detected automatically. On the current stock kernel wiht breezy I have to use ndiswrappers. Im hoping that with 2.6.16 kernel this wont be required anylonger. If not oh well Ill load ndiswrappers again LMFAO. By the way............still compiling LOL

---

### Post by godsfilth on 2006-05-14
im sorry if it was posted somewhere but i couldnt find it anywhere.

this is the 3rd or 4th time ive compiled a kernel and i always have this one issue that i cant solve im on a laptop and my touchpad dosnt let me drag, normally i can tap once then tap and hold and drag things around, also i have a button in the middle that usually emulates page up, page down, forward page, back page but it no longer works either. does anyone know how to help with this because i want to use my custom kernal but i dont wanna change my habbits   thanks in advance


also nice guide especially the part where it makes a .deb instead of just installing it now i can back it up if i screw up and i can reinstall much easier

---

### Post by CrashOverKill on 2006-05-15
What  make  model laptop. Might have to do some digging in that direction. I know my old thinkpad took some kernel tweaking to work right

---

### Post by xtacocorex on 2006-05-15
I just wanted to say thanks for the guide that helped me to successfully compile  the 2.6.16 kernel with the ck9 patch that actually got my prism54 wireless card to work with minimal tweaking. One thing I will say is that if you have a prism54 card, the vanilla kernel looks for the firmware in /lib/firmware so you need to edit $FIRMWARE_DIRS in /etc/hotplug/firmware.agent to point to /lib/firmware. 

I've attempted kernel compiling before and they either failed or just didn't have the config I wanted, namely wireless not working.

With the success of this, I think I might try another one with the suspend2 patch for my laptop and further removal of components I don't need. I read through the first 6 pages of this thread, but I think somewhere someone might have gotten usplash to work. I might figure that out too since my laptop is old and seeing the black screen just makes me think that something isn't working.

EDIT:
It appears that my touchpad doesn't allow sidescrolling now, but I think it comes down to the device I put in my xorg.conf file for the default kernels. Once I figure this out, I can create an init script to read my kernel version and then link the proper xorg.conf file to get the touchpad working and hopefully not break my system.

---

### Post by mi33 on 2006-05-15
How long (usually) compilation should take ?
Last time it taked really long time...
What's with this kernel ?

(My PC > Intel Celeron 1GHz & 256MB RAM)

[SIZE="2"]Sorry for my english[/SIZE] :)

---

### Post by thasheep on 2006-05-15
[QUOTE=mi33]How long (usually) compilation should take ?
Last time it taked really long time...
What's with this kernel ?

(My PC > Intel Celeron 1GHz & 256MB RAM)

[SIZE="2"]Sorry for my english[/SIZE] :)[/QUOTE]
It all depends on how well you know your computer and how much you can cut out. Eg, you probably only have one sound card and one ethernet card so you can get rid of all the rest. If you don't use raid, remove everything that mentions raid. Apart from "system" filesystems (proc, dev, sys, tmpfs, initrd), You'll probably never see any filesystems other than ext2 ext3 reiserfs, vfat (removable drives/shared shared with windows), ntfs (windows) and iso9660 (cds/dvds). NLS for languages you can't read is probably useless too. If you don't have floppy or tapes drives, you don't need to support them.
On your computer, an optimised kernel would (as a guess) take somewhere in the range of 20-30 minutes.

---

### Post by Melvil on 2006-05-15
[QUOTE=MasterChief1234]Did you compile the latest ndiswrapper from source ?[/QUOTE]

ndiswrapper? I'm sure it's not necessary for the ipw driver because it's a native linux driver and worked without ndiswrapper before.

---

### Post by thasheep on 2006-05-15
[QUOTE=Melvil]Damn, I thought the kernel update caused no problems, but my wireless interface is gone (ipw2200). It's compiled into the kernel, but this is the only message in dmesg:



sudo modprobe ipw2200 doesn't add anything to dmesg. Help! :([/QUOTE]
You also need to have the ipw firmware. It can be downloaded from somewhere but it's also in linux-restricted. I find the easiest way is to create a link from a standard kernel's firmware package. If it worked with the 2.6.15-22-686 kernel then do the following...
```
cd /lib/firmware
sudo ln -s 2.6.15-22-686 `uname -r`
```Make sure you use `uname -r` rather than 'uname -r'.

---

### Post by godsfilth on 2006-05-15
[QUOTE=CrashOverKill]What  make  model laptop. Might have to do some digging in that direction. I know my old thinkpad took some kernel tweaking to work right[/QUOTE]


its an Acer Aspire 3000 (the AS3002LCi model)


edit:
well i just did a dist-upgrade to dapper since ive been meaning to and it appers to have fixed the touchpad issues while still useing my custom kernel

---

### Post by RavenOfOdin on 2006-05-15
OK, finally got the kernel patched and I think performance is even better now.

I took out a bunch of drivers and customized some features.

There are a few things which are really wrong, mostly with the APM and printing (and I may recompile the kernel to put these back in), but the general issues I can live with.

---

### Post by neoaddict on 2006-05-18
I recompiled the 2.6.16 kernel again with no driver support for the things I don't need.  The original Ubuntu kernel is so slow compared to this one. 

Any news on any new kernels?

---

### Post by RavenOfOdin on 2006-05-18
I've gotten the new iptables and patch-o-matic from netfilter.org as per the HOWTO (former from its snapshot directory - 1.3.5-20060518 - and latter from its main dir), but when I try to update the kernel source with them it spits out errors as follows:

```

Cannot apply - <n> missing files.

```

```

ERROR - <n> rejects out of <n> hunks.

```

```

ERROR - missing files.

```

These errors happen on the unpatched 2.6.16 kernel as well as the patched 2.6.16-16 one, using the source which is already unzipped into /usr/src/linux.  They also happen with every individual netfilter patch, using "t" and "n" to skip.

Any idea what could be going wrong?  Do I need to "make" the kernel source over again? 

(EDIT: I don't need to download the source again, since the .tar file isn't corrupt as checked with md5sum, and I've unzipped it again into another directory and tried from there.)

PS: Is there a reason patch-o-matic was cited in post #177 and not patch-o-matic-ng as in the HOWTO? This process isn't working with either, and they're both the latest version.

---

### Post by hikitsu4 on 2006-05-18
I got a question about the nvidia driver i got installed now with my k7 kernel, when i install the new kernel deb file do i need to install the nvidia driver at the same time again or?

---

### Post by mucha on 2006-05-18
I only get a black screen when I tries to start with the new kernel. The only I did was to change my processortype.

---

### Post by neoaddict on 2006-05-18
Does it show the login screen eventually?

---

### Post by mucha on 2006-05-18
No, nothing happens. Well I hear it's loading the kernel or something.

---

### Post by xXx 0wn3d xXx on 2006-05-18
[QUOTE=mucha]No, nothing happens. Well I hear it's loading the kernel or something.[/QUOTE]
Try waiting and see if you just have no usplash. To get it back, once you are at a usable desktop, open synaptic, search for "usplash" and then select it for re-install. Then hit "Apply."

---

### Post by [Yatta] on 2006-05-19
[QUOTE=MasterChief1234]Try waiting and see if you just have no usplash. To get it back, once you are at a usable desktop, open synaptic, search for "usplash" and then select it for re-install. Then hit "Apply."[/QUOTE]

I tried the re-install for usplash no go[-(  .... 
Otherwise from that THANKS!!! i compiled my own kernel successfully. Now to really twek it out ans get rid of the stuff i really don 't need.
I have to install back my ivtv drivers but i think i can handle that now :D

---

### Post by mucha on 2006-05-19
[QUOTE=MasterChief1234]Try waiting and see if you just have no usplash. To get it back, once you are at a usable desktop, open synaptic, search for "usplash" and then select it for re-install. Then hit "Apply."[/QUOTE]

I wait about 10 minutes at max and nothing happens. It seems it just stops loading.

---

### Post by Cirrocco on 2006-05-19
I just successfully performed the contents of the how to, but I have one problem:

the comuter I did it on has a 10 gig harddrive and this little ditty cost me 10% of my drive.

is there any post-upgrade files that are safe to delete?
maybe all the stuff in /usr/src ?

---

### Post by neoaddict on 2006-05-19
It cost me 600 MB of my hard drive.

Anyways, you can go into terminal and type in these commands:

sudo apt-get clean
sudo apt-get autoclean

That'll get rid of old Synaptic packages on your hard drive.

Then, go into /usr/src and delete the linux symbolic directory.

If that doesn't work, restart your comp using your old kernel, open up Synaptic and search for 2.6.16 - you should find the new kernel package.  Completely remove it.

Then go to /usr/src and remove the linux-2.6.16ck3 directory.

Now it's time to once again recompile the kernel!

When you reach the xconfig stage, deselect stuff you don't need (if you don't have bluetooth, disable that, etc).

It made my kernel a little bit faster and saved me 10 MB of space.

---

### Post by Yoriko on 2006-05-19
I compiled this fine, much faster, thanks. 
But it completely screwed my eciadsl drivers, I'm guessing recompiling would fix it, but I havn't gotten around to that yet.

---

### Post by [Yatta] on 2006-05-19
i want to run the patch-2.6.16-ck9.gz  
is it alright to do 
```

gunzip  /home/enigma/Desktop/patch-2.6.16-ck9.gz| patch -p1
```
When i do that i get 
```

gunzip: /home/enigma/Desktop/patch-2.6.16-ck9 already exists; do you wish to overwrite (y or n)?
```
Can someone explain to me .. wat is going on please... and lead me into the right direction?
TIA

EDIT.. i found patch-2.6.16-ck10.bz2 so i'll use that... BUT i would still like to know what is going on here?
EDIT 2 :D ... I just noticed i did grab the wrong file from the wrong folder from .. SHeeshh........  Chalk it down to a learning experince compilig ck10 now... THEN i'm going to have to add my ivtv and lircd modules.... whhooopiies

---

### Post by Yoriko on 2006-05-19
for .gz, it is gzip not bzip, 

so it is gzcat, or cat.

---

### Post by jz_element on 2006-05-19
What is your 16th step <name of the file> ? If it is kernel_image-2.6.16-ck3, than where can I find it. I don't see in /usr/src/linux. Thanks

---

### Post by Yoriko on 2006-05-19
in /usr/src, should be kernel-image-2.6.16-ck3*.deb, but just FYI ck10 is out now.

---

### Post by xXx 0wn3d xXx on 2006-05-19
[QUOTE=jz_element]What is your 16th step <name of the file> ? If it is kernel_image-2.6.16-ck3, than where can I find it. I don't see in /usr/src/linux. Thanks[/QUOTE]
It's in /usr/src.

---

### Post by jz_element on 2006-05-19
Thanks. I found it. BUT it didn't boot. The error is no /dev/sad1 found. In memu.lst there are a few places like this in using 'root=/dev/sda1 ro quiet splash"

title		Ubuntu, kernel 2.6.16-ck3 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.16-ck3 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.16-ck3
savedefault
boot

Any idea what should I do? Thanks

---

### Post by customs on 2006-05-20
Well, I've compiled the 2.6.16 kernel with the 2.6.16.16 patch over it. I've added the ipw2100 firmware to /lib/firmware

The new kernel is faster and stable, but my synaptics touchpad functions (scroll areas and scroll button) don't work and the system can't find a splash screen. Also laptop keys don't work (Volume, Screen Brightness) with the new kernel. And ATI original driver is gone.

I've reinstalled usplash with no effect. I've recompile and reinstalled ATI driver with no effect. I've checked xorg.conf, where everything is fine and configured.

Any suggestions?

---

### Post by customs on 2006-05-20
Strange things are going on...

After few reboots the ATI driver begun to work, but the Synaptics touchpad still don't work ](*,)  I've found these lines in Xorg.0.log :

> (II) Synaptics touchpad driver version 0.13.6
Synaptics Touchpad no synaptics event device found (checked 1 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

---

### Post by RavenOfOdin on 2006-05-21
Is anyone else having trouble uninstalling iptables at the last step?

---

### Post by airzer0 on 2006-05-21
very nice how to, im sorta new to linux, used redhat for about 3 months but nothing..NOTHING touches ubuntu, building the new kernel was awsome

---

### Post by Xor van Dorf on 2006-05-21
I installed the latest kernel and I now want to remove the other one. In Synaptic, I "Mark for removal" linux-image..., but it also want to remove "linux 386", "linux-image-386", "linux-restricted-modules-2.6.12.10-386" and "linux-restricted-modules-386". Should I remove them too?

Also, reinstalling the usplash with Synaptic did not work, any other way to get it back?

---

### Post by [Yatta] on 2006-05-21
[QUOTE=Rizado]Originally Posted by dpicker
To get usplash you need to make sure you enable this in the config:

Graphics support:
-VGA 16-color graphics support - module (m)
-VESA VGA graphics support - build in kernel (y)

Console display driver support:
-VGA text console and Video mode selection support- build in kernel (y)
-MDA text console-module (m)
-Framebuffer Console and Framebuffer Console Rotation support-build in kernel (y)

Not sure how to change from "m" to "y" and vice versa in xconfig so I opened the .config file in gedit and checked it manually.

Archck patch includes the Con Kolivas patch but with lots of other cool things too like acpi updates and suspend2 but I had trouble compiling it.[/QUOTE]
Like [Rizado]("http://www.ubuntuforums.org/showpost.php?p=907072&postcount=24")  Stated earlier in the thread.
I had the same thing happen to me... i uninstalled usplash and re-installed it. NADA!!! ](*,)  After re-compiling i made sure the settings above were made re-compiled rebooted it was black screen :-( BUT after installed uspalsh again and rebooting VOILA it came back. 
PS... I need some indication to know my PC is loading up even if it's just a bar increasing in need to ssee soemthign and not just a blank screen.

---

### Post by Yoriko on 2006-05-21
you can edit /boot/grub/menu.lst and remove "splash" from your kernel line,
that way you  get text output, I kinda prefer it to usplash.

Just sucessfully compiled my kernel (ck10) with everything I don't need.
Works like a charm, and for those using eciadsl, remove DABUSB from the kernel when you compile it (it is under USB)

---

### Post by geearf on 2006-05-21
Hello,

I've recompiled my kernel, but now I have the iptable problem. I've seen the solution on the first page, but it's quite odd, anyone knows why is that.?

---

### Post by Xor van Dorf on 2006-05-21
[QUOTE='[Yatta]']Like [Rizado]("http://www.ubuntuforums.org/showpost.php?p=907072&postcount=24")  Stated earlier in the thread.
I had the same thing happen to me... i uninstalled usplash and re-installed it. NADA!!! ](*,)  After re-compiling i made sure the settings above were made re-compiled rebooted it was black screen :-( BUT after installed uspalsh again and rebooting VOILA it came back. 
PS... I need some indication to know my PC is loading up even if it's just a bar increasing in need to ssee soemthign and not just a blank screen.[/QUOTE]
How can I open the .config file?

---

### Post by neoaddict on 2006-05-21
Xor van Dorf, you should keep the old kernel in case you ever want to compile the kernel again.

MasterChief, have you tried compiling the kernel yet with the ck10 patch?

---

### Post by RavenOfOdin on 2006-05-21
Well, I just broke my kernel.

These are the notices I now get on startup (more or less :p): 

```

Warning: error inserting /drivers/video/console/bitblit.ko
Warning: error inserting /drivers/video/console/fbcon.ko
Warning: cannot find /drivers/video/cfbcopyarea.ko
Warning: cannot find /drivers/video/cfbfillrect.ko
Warning: cannot find /drivers/video/cfbimgblt.ko
Warning: cannot find /drivers/video/softcursor.ko
Fatal: error inserting unix : can't/remember/path/to/unix.ko : bunch of stuff

``` 

After that, it just sits there.

It looks like I'm going to have fun fixing menuconfig.
Either that or I'll just download the ck10 patch and be done with it.

(EDIT: After nosing around a little bit, this is what I come up with.

1: /var/log/kern.log gives me a bunch of messages related to l2cap and rfcomm when I try to start the faulty kernel. They go as follows, with <symbol> being an entry in the l2cap or rfcomm *struct*s:

```

l2cap: unknown symbol <symbol> 
l2cap: disagrees about version of symbol <symbol>

```

Same thing with rfcomm, ad nauseam.  After doing "locate l2cap" I noticed these modules were/are related to Bluetooth support. What would happen if I took Bluetooth support out of the kernel completely? I assume these messages would stop showing, but after seeing a few things on these forums related to the forced integration of Bluetooth and KDE - the latter of which I use at the moment - I'm uneasy with that idea.

2. For anyone who is having trouble removing iptables through modprobe, try this:

```

rmmod iptable_filter
rmmod ip_tables

```

3. Just out of curiosity. . .*uneasy grin*. . .What are TPM/TCG modules doing in the character devices section?
)

(EDIT #2: I think I know what the /video/console problem is now, I have a built in S3 ProSavage as well as an ATI Radeon. I took out the Savage drivers thinking the ATI would pick up the slack on OS pre-load.  . .which may have been wrong. Just gotta re-compile it and see.)

---

### Post by xXx 0wn3d xXx on 2006-05-21
[QUOTE=neoaddict]Xor van Dorf, you should keep the old kernel in case you ever want to compile the kernel again.

MasterChief, have you tried compiling the kernel yet with the ck10 patch?[/QUOTE]
No, I don't patch my kernels.

---

### Post by garijon on 2006-05-21
Hi, I compiled the kernel, following the steps. The improvement was amazing. The thing is after booting I have the lost my second HD. I have 2 IDE hard drives, but my box only sees one now. 
When I try to manually mount the second one, I get a message saying that it is either mounted or busy. If I try to unmount it, it says it was not mounted at all. 
If I boot using the original kernel I see it just fine. Any help will be greatly appreciated.

G.

---

### Post by neoaddict on 2006-05-22
For anyone who has used the ck10 patch, is there a minor or major difference compared to ck3?

---

### Post by [Yatta] on 2006-05-22
[QUOTE=Xor van Dorf]How can I open the .config file?[/QUOTE]
If your using xconfig you can go to 
OPEN --> Then point it to the .config file

[QUOTE=neoaddict]For anyone who has used the ck10 patch, is there a minor or major difference compared to ck3?[/QUOTE]
I'm not sure if there is.. the easiest thign to do is the check the changelog.

---

### Post by neoaddict on 2006-05-23
Here's the ck11 patch:

[http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/2.6.16-ck11/patch-2.6.16-ck11.bz2](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/2.6.16-ck11/patch-2.6.16-ck11.bz2)

Guess I'm compiling another vanilla kernel.  :P

---

### Post by Xor van Dorf on 2006-05-23
[QUOTE='[Yatta]']If your using xconfig you can go to 
OPEN --> Then point it to the .config file
[/QUOTE]
Thanks for that, I'll try it when I'm at home.

Other question: How can I compile the latest kernel (2.6.16.18 atm) with the ck patch? I tried to patch the kernel with the patch and I get lot of errors. Do I need to patch it on the 2.6.16 kernel AND apply the 2.6.16.18 patch after?

---

### Post by a9db0 on 2006-05-23
[QUOTE=PriceChild]Hey again... i've compiled 2.6.16.9 (downloaded from the front page)

And all seems to have gone perfectly.

However, i'm trying to re-install vmware player, and it gives the following errors:

 
This seems wierd and shouldn't happen.

Please help! :)

Pricey[/QUOTE]

Here are a couple of suggested steps for getting vmware reconfigured on kernel 2.6.16:

1) If you haven't already, reboot your system so it is running on the new kernel.

2) Download the file vmware-any-any-updateYYY.tar.gz from [this link]("http://mirror.vmmatrix.net/vmware-any-any-update/").   Replace the YYY with the most current version, 101 as of this writing.

3) Untar the file, and run the runme.pl script.  This perl script patches several of the vmware files to match the ever-changing kernel headers.

4) The script will then ask if you wnat to run the vmware-config.pl script.  Do so, and enjoy the return of vmware.

I've tested this on 2.6.16.18 and it works fine.

---

### Post by RavenOfOdin on 2006-05-23
EDIT: Scratch that, I have my 2.6.12-10-32 kernel usable, and iptables 1.3.5 seems to be running on it without any errors that I can detect.

Now, the hard part is getting Firestarter to recognize the changes and making sure they'll be available in the 2.6.16.18 kernel.

I've used these from the command line:

```

modprobe iptable_filter
modprobe ip_tables
modprobe ip_conntrack

```

and the last one seems to get rid of the "/proc/net/ip_conntrack: No such file or directory" error in my "Active Connections" tab. But I know from /usr/local/etc/firestarter/firewall that there are quite a few more modules to load. And preferably, these must be done automatically. The best option I have at the moment is to recompile 2.6.16.18 with netfilter in, needed core and *all* IP modules. Gonna see if that works to load the modules and get Firestarter to recognize iptables at the same time. . .might be tricky, but I'll get it done.

@MasterChief1234: You might want to update your HOWTO with links to the iptables programs, like so:

```

cd /usr/local
ln -s /usr/src/iptables iptables
ln -s /usr/src/iptables-save iptables-save
ln -s /usr/src/iptables-restore iptables-restore

```

Or, just install it in /usr/local as the README states. :D

---

### Post by argie on 2006-05-25
When I check the /dev/agpart section for Via and I check the DRM for Via Unichrome and compile, I still get a kernel that gives me no direct rendering.

I tried it some 3 times and checked that the .config file had it enabled before I compiled.

glxinfo still gives me "Direct Rendering: No"

Is there anything else I need to enable to get that?
glxinfo:
"__driCreateNewScreen_20050727 - succeeded
AllocateDmaBuffer fail
display: :0  screen: 0
direct rendering: No
"

Also, when I start up, I get lots of insmod: File not found errors. something about video, bitblit.ko and stuff, if that matters, tell me I'll try to get the whole thing.

---

### Post by RavenOfOdin on 2006-05-25
[QUOTE=argie]
Also, when I start up, I get lots of insmod: File not found errors. something about video, bitblit.ko and stuff, if that matters, tell me I'll try to get the whole thing.[/QUOTE]

I'm still getting that in 2.6.16.18.
Are you unable to go beyond the boot process and stuck at a black screen with those messages?

---

### Post by argie on 2006-05-25
Well, it pauses there for quite a long time, after the last error. Then I get a long list of errors that scrolls by super quickly, too fast to notice and then Ubuntu starts normally.

But yeah, it starts after that. No black screen for me.

---

### Post by RavenOfOdin on 2006-05-25
[QUOTE=argie]Well, it pauses there for quite a long time, after the last error. Then I get a long list of errors that scrolls by super quickly, too fast to notice and then Ubuntu starts normally.

But yeah, it starts after that. No black screen for me.[/QUOTE]

Okay. . .then. . .

Do you have support for Matrox enabled in your character and/or graphics sections? (Device Drivers) G200 and G400 especially.

I put those in and those messages similar to yours vanished. Now I'm getting a defunct Kubuntu usplash - where it doesn't load modules or anything, just sits there -with recovery mode notices like:

```

[4294674.148000]unix: disagrees about version of symbol sock_register
[4294674.148000]unix: unknown symbol sock_register
[4294674.148000]unix: disagrees about version of symbol sock_wake_async
[4294674.148000]unix: unknown symbol sock_wake_async

```

Try doing it even if you don't use a Matrox card, because I'm running a 128 MB ATI Radeon 9200 over a built in S3 ProSavage DDR.

---

### Post by lex1 on 2006-05-25
how about useing these scripts but just tweak them a little

[http://www.howtoforums.net/viewtopic.php?t=5](http://www.howtoforums.net/viewtopic.php?t=5)

---

### Post by zymazyt on 2006-05-27
Hi
I've tried compiling 2.6.16 kernel with ck11 patches, after some reading on mail lists and forums. But unfortunately I'm stuck.
Every time I boot, start up procces freezes at "Mounting root file system" message. All drives are correctly found, before that, and everything seems normal, but start proccess just stops there. Oh, maybe I shouldn't say it freezes because I can scroll kernel messages(there are none errors), and system reboots instantly on ctrl-alt-del. I've tried compilling it with "my" cut down configuration, and default one (the one that is provided with clean install system kernel and definately works). I've also tried 2.6.16.18 kernel without any patches...
Maybe someone knows what is happening?

---

### Post by neoaddict on 2006-05-28
I just compiled my own kernel with the ck11 patch with no problems...

Did you follow the steps word by word, except to replace ck3 with ck11?

---

### Post by djpate on 2006-05-28
I just followed the how to to make my DVB-T card work and it does now but i have no sound.
What can i do?
linux newbie here

---

### Post by zymazyt on 2006-05-28
True, I went step by stap...and I think I did it like 3 or 4 times. I'll try one more thing as far as all my build were made for AMD64 - I'll try to build x86_64 generic kernel...

Edit:
Tested building 2.6.16 kernel w/o patches for x86_64 --->same problem
Tested building 2.6.17rc5 kernel for x86_64 and AMD64 ----> same problem

Now I really don't know why it is not working. The only kernel that had worked afhttp://ubuntuforums.org/images/smilies/icon_biggrin.gif
ter compilation was old one 2.6.15.8 from ubuntu reps...

Edit2:
Uff, hopefully solved it. It looks like the problem was in version/configuration of device mapper. After reinstalling it the new compilled kernels starts smoothly as them should.
It looks that obsolete version works only with 2.6.15 kernel versionfamily.

---

### Post by Progressive on 2006-05-28
I am just wondering why Ubuntu doesn't just give us the latest kernels.  Do they, or debian, do any work on their kernels?

---

### Post by zymazyt on 2006-05-28
I think that now, they are concerning all efforts on kinishing work with dapper stable. Their dead line is close, and they have some thing to do with it :)
But true is that, at least, 2.6.16 kernel should already be shipped with beta, so they could check it for errors and compatibility...

---

### Post by ravpaul on 2006-05-28
My Terminal has been running for 1hour after typing the following commands:

"make-kpkg clean

make-kpkg -initrd --revision=ck3 kernel_image"

Is that normal or have I buggered something up?

---

### Post by ravpaul on 2006-05-28
How To Compile the new 2.6.16 kernel from kernel.org

---

### Post by RavenOfOdin on 2006-05-28
[QUOTE=ravpaul]My Terminal has been running for 1hour after typing the following commands:

"make-kpkg clean

make-kpkg -initrd --revision=ck3 kernel_image"

Is that normal or have I buggered something up?[/QUOTE]


Its normal.

---

### Post by extremecarver on 2006-05-28
I did the normal compile with Ck11 and it worked. However I didn't get wifi to run even with deb ndiswrapper??????  Can anyone help me out? I need to have linux-phc compiled into my kernel - using dapper RC1 currently.

Now I tried to compile the no.oldos source but it crashes on build with the following errors[HTML] CC [M]  drivers/usb/misc/sisusbvga/sisusb.o
In file included from drivers/usb/misc/sisusbvga/sisusb.c:56:
drivers/usb/misc/sisusbvga/sisusb_init.h:222: error: array type has incomplete element type
drivers/usb/misc/sisusbvga/sisusb_init.h:228: error: array type has incomplete element type
drivers/usb/misc/sisusbvga/sisusb_init.h:237: error: array type has incomplete element type
drivers/usb/misc/sisusbvga/sisusb_init.h:275: error: array type has incomplete element type
drivers/usb/misc/sisusbvga/sisusb_init.h:307: error: array type has incomplete element type
drivers/usb/misc/sisusbvga/sisusb_init.h:375: error: array type has incomplete element type
drivers/usb/misc/sisusbvga/sisusb_init.h:434: error: array type has incomplete element type
drivers/usb/misc/sisusbvga/sisusb_init.h:693: error: array type has incomplete element type
drivers/usb/misc/sisusbvga/sisusb_init.h:813: warning: ‘struct SiS_Private’ declared inside parameter list
drivers/usb/misc/sisusbvga/sisusb_init.h:813: warning: its scope is only this definition or declaration, which is probably not what you want
drivers/usb/misc/sisusbvga/sisusb_init.h:814: warning: ‘struct SiS_Private’ declared inside parameter list
drivers/usb/misc/sisusbvga/sisusb_init.h:837: warning: ‘struct vc_data’ declared inside parameter list
drivers/usb/misc/sisusbvga/sisusb.c:1339: error: static declaration of ‘sisusb_setidxreg’ follows non-static declaration
drivers/usb/misc/sisusbvga/sisusb_init.h:819: error: previous declaration of ‘sisusb_setidxreg’ was here
drivers/usb/misc/sisusbvga/sisusb.c:1351: error: static declaration of ‘sisusb_getidxreg’ follows non-static declaration
drivers/usb/misc/sisusbvga/sisusb_init.h:821: error: previous declaration of ‘sisusb_getidxreg’ was here
drivers/usb/misc/sisusbvga/sisusb.c:1364: error: static declaration of ‘sisusb_setidxregandor’ follows non-static declaration
drivers/usb/misc/sisusbvga/sisusb_init.h:823: error: previous declaration of ‘sisusb_setidxregandor’ was here
drivers/usb/misc/sisusbvga/sisusb.c:1395: error: static declaration of ‘sisusb_setidxregor’ follows non-static declaration
drivers/usb/misc/sisusbvga/sisusb_init.h:825: error: previous declaration of ‘sisusb_setidxregor’ was here
drivers/usb/misc/sisusbvga/sisusb.c:1404: error: static declaration of ‘sisusb_setidxregand’ follows non-static declaration
drivers/usb/misc/sisusbvga/sisusb_init.h:827: error: previous declaration of ‘sisusb_setidxregand’ was here
make[5]: *** [drivers/usb/misc/sisusbvga/sisusb.o] Error 1
make[4]: *** [drivers/usb/misc/sisusbvga] Error 2
make[3]: *** [drivers/usb/misc] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17-rc3-no1'
make: *** [stamp-build] Error 2
[/HTML]

---

### Post by ravpaul on 2006-05-29
I tried twice to compile the kernel (copying and pasting the information on the first page) and on both occasions got the same result(s)

1) Bootsplash not loading;
2) The sound playing continously on the login screen;
3) Not loading Gnome.

I have got an AMD processor and am currently using the amd generic kernel, is there anything different that I have to do?

P.S. Is there any way of getting rid of failed kernels apart from removing them from the grub menu?

---

### Post by RavenOfOdin on 2006-05-29
[QUOTE=ravpaul]I tried twice to compile the kernel (copying and pasting the information on the first page) and on both occasions got the same result(s)

1) Bootsplash not loading;
2) The sound playing continously on the login screen;
3) Not loading Gnome.

I have got an AMD processor and am currently using the amd generic kernel, is there anything different that I have to do?

P.S. Is there any way of getting rid of failed kernels apart from removing them from the grub menu?[/QUOTE]

1) 2.6.16.18 loads bootsplash for me correctly, I just had to put CONFIG_FB_MATROX and the Matrox G200/G400 support in along with the console display instructions on the bottom half of the first page.

Even though I'm using an ATI card, and not a Matrox. :p

2) You have sound on the login screen? :confused:
3) Did you reconfigure xserver to use the default system display driver before changing kernels?

P.S.: Yes there is, go into terminal and type
```

sudo dpkg -P <name of kernel image file>

```

This would assume that you're using a custom built kernel.
All kernel files reside in your /boot/ directory (Config, system.map, initrd and that other one.)

---

### Post by ravpaul on 2006-05-29
Tried two more times, got the same message.

Noticed that I am getting the following errors when typing in "bzcat /home/rav/patch-2.6.16-ck3.bz2| patch -p1 -R". Could that be of any significance?


patching file include/linux/sched.h
patching file kernel/sched.c
patching file fs/proc/array.c
patching file include/linux/sysctl.h
patching file kernel/exit.c
patching file kernel/sysctl.c
patching file include/linux/init_task.h
patching file block/Kconfig.iosched
patching file include/linux/ioprio.h
patching file mm/page-writeback.c
patching file arch/ia64/configs/tiger_defconfig
patching file arch/ia64/configs/zx1_defconfig
patching file arch/ppc/configs/common_defconfig
patching file arch/ppc/configs/pmac_defconfig
patching file kernel/Kconfig.hz
patching file Documentation/sysctl/vm.txt
patching file include/linux/swap.h
patching file init/Kconfig
patching file mm/Makefile
patching file mm/swap.c
patching file mm/swap_prefetch.c
patching file mm/swap_state.c
patching file mm/vmscan.c
patching file include/linux/mm_inline.h
patching file include/linux/swap-prefetch.h
patching file include/linux/mmzone.h
patching file mm/page_alloc.c
patching file fs/buffer.c
patching file kernel/power/disk.c
patching file drivers/block/loop.c
patching file fs/mpage.c
patching file fs/nfsd/vfs.c
patching file include/linux/fs.h
patching file include/linux/mm.h
patching file include/linux/page-flags.h
patching file include/linux/radix-tree.h
patching file include/linux/writeback.h
patching file lib/radix-tree.c
patching file mm/Kconfig
patching file mm/filemap.c
patching file mm/memory.c
patching file mm/readahead.c
patching file Documentation/DocBook/Makefile
patching file Makefile
patching file arch/arm/Makefile
patching file arch/arm/boot/Makefile
patching file arch/arm/boot/bootp/Makefile
patching file arch/arm26/Makefile
patching file arch/arm26/boot/Makefile
patching file arch/i386/Makefile
patching file arch/ia64/Makefile
patching file arch/m32r/Makefile
patching file arch/powerpc/Makefile
patching file arch/ppc/Makefile
patching file arch/ppc/boot/Makefile
patching file arch/ppc/boot/openfirmware/Makefile
patching file arch/sh/Makefile
patching file arch/um/Makefile
patching file arch/x86_64/Makefile
patching file scripts/Kbuild.include
patching file scripts/Makefile.build
patching file scripts/Makefile.clean
patching file scripts/Makefile.modinst
patching file scripts/Makefile.modpost
patching file scripts/kconfig/Makefile
patching file scripts/kconfig/lxdialog/Makefile
patching file scripts/package/Makefile
[COLOR="Red"]Hunk #1 FAILED at 32.
Hunk #2 FAILED at 54.
Hunk #3 FAILED at 72.
Hunk #4 FAILED at 82.[/COLOR]
4 out of 4 hunks FAILED -- saving rejects to file scripts/package/Makefile.rej
patching file arch/i386/kernel/cpu/cpufreq/speedstep-smi.c
patching file arch/i386/kernel/dmi_scan.c
patching file drivers/base/cpu.c
patching file drivers/base/firmware_class.c
patching file drivers/block/cciss.c
patching file drivers/md/dm.c
patching file drivers/media/video/Kconfig
patching file drivers/media/video/tuner-types.c
patching file drivers/scsi/sata_mv.c
patching file drivers/video/i810/i810_main.c
patching file fs/9p/vfs_inode.c
patching file fs/proc/proc_misc.c
patching file fs/sysfs/dir.c
patching file fs/sysfs/inode.c
patching file fs/sysfs/symlink.c
patching file fs/xfs/linux-2.6/xfs_aops.c
patching file include/linux/cpu.h
patching file include/linux/raid/raid1.h
patching file include/linux/rtc.h
patching file net/core/sock.c
patching file net/ipv4/ip_output.c
root@bedroom:/usr/src/linux# uname -r
2.6.15-23-amd64-generic
root@bedroom:/usr/src/linux# sudo cp /boot/config-2.6.15-23-amd64-generic .config
root@bedroom:/usr/src/linux# sudo make xconfig
  CHECK   qt
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/x86_64/Kconfig
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
#
# using defaults found in .config
#
[COLOR="Red"].config:23:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:43:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:101:warning: trying to assign nonexistent symbol X86_64_NOLONG_MSG
.config:115:warning: trying to assign nonexistent symbol ENABLE_ALT_SMP
.config:178:warning: trying to assign nonexistent symbol ACPI_SBS
.config:190:warning: trying to assign nonexistent symbol ACPI_PCC
.config:191:warning: trying to assign nonexistent symbol ACPI_SONY
.config:198:warning: trying to assign nonexistent symbol ACPI_TC1100
.config:199:warning: trying to assign nonexistent symbol ACPI_INITRD
.config:200:warning: trying to assign nonexistent symbol ACPI_DEV
.config:263:warning: trying to assign nonexistent symbol PCMCIA_PROBE_MEM
.config:405:warning: trying to assign nonexistent symbol IP_NF_MATCH_LIMIT
.config:407:warning: trying to assign nonexistent symbol IP_NF_MATCH_MAC
.config:408:warning: trying to assign nonexistent symbol IP_NF_MATCH_PKTTYPE
.config:409:warning: trying to assign nonexistent symbol IP_NF_MATCH_MARK
.config:416:warning: trying to assign nonexistent symbol IP_NF_MATCH_LENGTH
.config:418:warning: trying to assign nonexistent symbol IP_NF_MATCH_TCPMSS
.config:419:warning: trying to assign nonexistent symbol IP_NF_MATCH_HELPER
.config:420:warning: trying to assign nonexistent symbol IP_NF_MATCH_STATE
.config:421:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNTRACK
.config:423:warning: trying to assign nonexistent symbol IP_NF_MATCH_PHYSDEV
.config:425:warning: trying to assign nonexistent symbol IP_NF_MATCH_REALM
.config:426:warning: trying to assign nonexistent symbol IP_NF_MATCH_SCTP
.config:427:warning: trying to assign nonexistent symbol IP_NF_MATCH_DCCP
.config:428:warning: trying to assign nonexistent symbol IP_NF_MATCH_COMMENT
.config:429:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNMARK
.config:430:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNBYTES
.config:432:warning: trying to assign nonexistent symbol IP_NF_MATCH_STRING
.config:438:warning: trying to assign nonexistent symbol IP_NF_TARGET_NFQUEUE
.config:455:warning: trying to assign nonexistent symbol IP_NF_TARGET_MARK
.config:456:warning: trying to assign nonexistent symbol IP_NF_TARGET_CLASSIFY
.config:458:warning: trying to assign nonexistent symbol IP_NF_TARGET_CONNMARK
.config:461:warning: trying to assign nonexistent symbol IP_NF_TARGET_NOTRACK
.config:471:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LIMIT
.config:472:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MAC
.config:479:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MARK
.config:482:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LENGTH
.config:484:warning: trying to assign nonexistent symbol IP6_NF_MATCH_PHYSDEV
.config:488:warning: trying to assign nonexistent symbol IP6_NF_TARGET_NFQUEUE
.config:490:warning: trying to assign nonexistent symbol IP6_NF_TARGET_MARK
.config:746:warning: trying to assign nonexistent symbol IEEE80211_SOFTMAC
.config:747:warning: trying to assign nonexistent symbol IEEE80211_SOFTMAC_DEBUG.config:748:warning: trying to assign nonexistent symbol IEEE80211_1_1_13
.config:749:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_WEP
.config:750:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_CCMP
.config:751:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_TKIP
.config:956:warning: trying to assign nonexistent symbol BLK_DEV_CLOOP
.config:967:warning: trying to assign nonexistent symbol BLK_DEV_GNBD
.config:988:warning: trying to assign nonexistent symbol BLK_DEV_IDEACPI
.config:997:warning: symbol value 'm' invalid for BLK_DEV_IDEPNP
.config:1028:warning: trying to assign nonexistent symbol PDC202XX_FORCE
.config:1070:warning: trying to assign nonexistent symbol SCSI_SPI2_ATTRS
.config:1078:warning: trying to assign nonexistent symbol SAS_CLASS
.config:1079:warning: trying to assign nonexistent symbol SAS_DEBUG
.config:1089:warning: trying to assign nonexistent symbol SCSI_AIC94XX
.config:1090:warning: trying to assign nonexistent symbol AIC94XX_DEBUG
.config:1106:warning: trying to assign nonexistent symbol SCSI_ARCMSR
.config:1128:warning: trying to assign nonexistent symbol SCSI_SATA_ACPI
.config:1150:warning: trying to assign nonexistent symbol SCSI_SYM53C8XX_MMIO
.config:1157:warning: trying to assign nonexistent symbol SCSI_QLA2XXX
.config:1237:warning: trying to assign nonexistent symbol IEEE1394_CMP
.config:1348:warning: trying to assign nonexistent symbol R1000
.config:1371:warning: trying to assign nonexistent symbol NET_IPG
.config:1414:warning: trying to assign nonexistent symbol IPW2100_FS_AMILO_M7400.config:1417:warning: trying to assign nonexistent symbol IPW2200_MONITOR
.config:1436:warning: trying to assign nonexistent symbol ADM8211
.config:1447:warning: trying to assign nonexistent symbol WLAN_NG
.config:1448:warning: trying to assign nonexistent symbol PRISM2
.config:1449:warning: trying to assign nonexistent symbol PRISM2_USB
.config:1450:warning: trying to assign nonexistent symbol PRISM2_PCI
.config:1451:warning: trying to assign nonexistent symbol PRISM2_PLX
.config:1452:warning: trying to assign nonexistent symbol PRISM2_CS
.config:1453:warning: trying to assign nonexistent symbol NET_ACX
.config:1454:warning: trying to assign nonexistent symbol NET_ACX_PCI
.config:1455:warning: trying to assign nonexistent symbol NET_ACX_USB
.config:1456:warning: trying to assign nonexistent symbol BCM43XX
.config:1457:warning: trying to assign nonexistent symbol BCM43XX_DEBUG
.config:1458:warning: trying to assign nonexistent symbol BCM43XX_DMA
.config:1459:warning: trying to assign nonexistent symbol BCM43XX_PIO
.config:1460:warning: trying to assign nonexistent symbol BCM43XX_DMA_AND_PIO_MODE
.config:1461:warning: trying to assign nonexistent symbol BCM43XX_DMA_MODE
.config:1462:warning: trying to assign nonexistent symbol BCM43XX_PIO_MODE
.config:1463:warning: trying to assign nonexistent symbol PRISM54_SOFTMAC
.config:1464:warning: trying to assign nonexistent symbol NET_RT2600
.config:1465:warning: trying to assign nonexistent symbol NET_RT2500
.config:1466:warning: trying to assign nonexistent symbol NET_RT2400
.config:1467:warning: trying to assign nonexistent symbol NET_RTL818X
.config:1468:warning: trying to assign nonexistent symbol NET_RTL8187
.config:1469:warning: trying to assign nonexistent symbol IPW3945
.config:1470:warning: trying to assign nonexistent symbol IPW3945_DEBUG
.config:1471:warning: trying to assign nonexistent symbol IPW3945_MONITOR
.config:1472:warning: trying to assign nonexistent symbol NET_MRV8K
.config:1575:warning: trying to assign nonexistent symbol NDISWRAPPER
.config:1712:warning: trying to assign nonexistent symbol MISDN_DRV
.config:1713:warning: trying to assign nonexistent symbol MISDN_MEMDEBUG
.config:1714:warning: trying to assign nonexistent symbol MISDN_AVM_FRITZ
.config:1715:warning: trying to assign nonexistent symbol MISDN_HFCPCI
.config:1716:warning: trying to assign nonexistent symbol MISDN_HFCMULTI
.config:1717:warning: trying to assign nonexistent symbol MISDN_HFCUSB
.config:1718:warning: trying to assign nonexistent symbol MISDN_SPEEDFAX
.config:1719:warning: trying to assign nonexistent symbol MISDN_W6692
.config:1720:warning: trying to assign nonexistent symbol MISDN_DSP
.config:1794:warning: trying to assign nonexistent symbol INPUT_ACERHK
.config:1819:warning: trying to assign nonexistent symbol ECC
.config:2109:warning: trying to assign nonexistent symbol AVERATEC_5100P
.config:2110:warning: trying to assign nonexistent symbol PACKARDBELL_E5
.config:2245:warning: trying to assign nonexistent symbol DVB_TDA80XX
.config:2267:warning: trying to assign nonexistent symbol DVB_ATMEL_AT76C651
.config:2275:warning: trying to assign nonexistent symbol DVB_NXT2002
.config:2288:warning: trying to assign nonexistent symbol DXR3
.config:2289:warning: trying to assign nonexistent symbol EM8300
.config:2290:warning: trying to assign nonexistent symbol EM8300_LOOPBACK
.config:2291:warning: trying to assign nonexistent symbol EM8300_UCODETIMEOUT
.config:2292:warning: trying to assign nonexistent symbol EM8300_DICOMFIX
.config:2293:warning: trying to assign nonexistent symbol EM8300_DICOMCTRL
.config:2294:warning: trying to assign nonexistent symbol EM8300_DICOMPAL
.config:2295:warning: trying to assign nonexistent symbol ADV717X
.config:2296:warning: trying to assign nonexistent symbol ADV717X_SWAP
.config:2297:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT16BIT.config:2298:warning: trying to assign nonexistent symbol ADV717X_PIXELPORTPAL
.config:2299:warning: trying to assign nonexistent symbol BT865
.config:2325:warning: symbol value 'm' invalid for FB_VESA
.config:2350:warning: trying to assign nonexistent symbol FB_ATY_XL_INIT
.config:2369:warning: trying to assign nonexistent symbol FB_IMAC
.config:2418:warning: trying to assign nonexistent symbol SND_GENERIC_DRIVER
.config:2495:warning: trying to assign nonexistent symbol BT_ALSA
.config:2618:warning: trying to assign nonexistent symbol USB_SYNAPTICS
.config:2619:warning: trying to assign nonexistent symbol USB_CPADDEV
.config:2640:warning: trying to assign nonexistent symbol USB_QC
.config:2641:warning: trying to assign nonexistent symbol USB_SPCA5XX
.config:2642:warning: trying to assign nonexistent symbol USB_PODXTPRO
.config:2644:warning: trying to assign nonexistent symbol USB_OV511_DECOMP
.config:2645:warning: trying to assign nonexistent symbol USB_OV518_DECOMP
.config:2669:warning: trying to assign nonexistent symbol USB_EAGLE
.config:2670:warning: trying to assign nonexistent symbol USB_ZD1211
.config:2671:warning: trying to assign nonexistent symbol USB_ATMEL
.config:2672:warning: trying to assign nonexistent symbol USB_RT2570
.config:2783:warning: trying to assign nonexistent symbol MMC_SDHCI
.config:2896:warning: trying to assign nonexistent symbol ASFS_FS
.config:2897:warning: trying to assign nonexistent symbol ASFS_DEFAULT_CODEPAGE
.config:2898:warning: trying to assign nonexistent symbol ASFS_RW
.config:2917:warning: trying to assign nonexistent symbol SQUASHFS
.config:2918:warning: trying to assign nonexistent symbol SQUASHFS_1_0_COMPATIBILITY
.config:2919:warning: trying to assign nonexistent symbol SQUASHFS_2_0_COMPATIBILITY
.config:2927:warning: trying to assign nonexistent symbol UNION_FS
.config:2974:warning: trying to assign nonexistent symbol GFS_FS
.config:2975:warning: trying to assign nonexistent symbol GFS_FS_LOCK_HARNESS
.config:2976:warning: trying to assign nonexistent symbol GFS_FS_LOCK_NOLOCK
.config:2977:warning: trying to assign nonexistent symbol GFS_FS_LOCK_DLM
.config:2978:warning: trying to assign nonexistent symbol GFS_FS_LOCK_GULM
.config:3077:warning: trying to assign nonexistent symbol INIT_DEBUG
.config:3089:warning: trying to assign nonexistent symbol SECURITY_REALTIME
.config:3152:warning: trying to assign nonexistent symbol CLUSTER
[/COLOR]

---

### Post by RavenOfOdin on 2006-05-29
[QUOTE=ravpaul]Tried two more times, got the same message.
[/QUOTE]

Are you trying to compile the ck3 patch without the 2.6.16 base?

---

### Post by extremecarver on 2006-05-29
Well - Could you please add that wifi problems are solved for those where ndiswrapper didn't work - after adding the IPW2200 to lib/firmware. --Ndiswrapper must be installed too!

Either or means no wifi for me.

---

### Post by digiplaya on 2006-06-04
Strangely enough, when I try to make the DEB file as the instructions say to do, I get this error on that step (while compiling the sound drivers for the kernel):

> In file included from sound/pci/ice1712/revo.c:25:
include/asm/io.h: In function `outb_local_p':
include/asm/io.h:382: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make[4]: *** [sound/pci/ice1712/revo.o] Error 1
make[3]: *** [sound/pci/ice1712] Error 2
make[2]: *** [sound/pci] Error 2
make[1]: *** [sound] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16ck3'
make: *** [stamp-build] Error 2


sounds familiar?
ideas?

tom

---

### Post by linuxunil on 2006-06-04
I was wondering if someone could give an example of how to get fglrx to work with this kernel or give a thread that discusses how do to it i have been searching the forums and wiki and cannot find one.

---

### Post by xXx 0wn3d xXx on 2006-06-04
Install fglrx-kernel-source.

> sudo apt-get install fglrx-kernel-source

---

### Post by linuxunil on 2006-06-04
Thanks got it fixed.

---

### Post by digiplaya on 2006-06-05
Mine was fixed too, except for usplash still doesn't work, even after reinstalling it.

I'm using the kernel that the guide instructs to make. (2.6.16-ck3)

---

### Post by hannes_ on 2006-06-06
For all you Ubuntu users with the new Kernel, BUT the working usplash.

Here is the workaround for the problem.
> 
In order to get the usplash working for ubuntu. Apply the following settings to your config.

Graphics support:
CONFIG_FB_VGA16=m
CONFIG_FB_VESA=y

Console display driver support:
CONFIG_VGA_CONSOLE=y
CONFIG_MDA_CONSOLE=m
CONFIG_FRAMEBUFFER_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE_ROTATION=y 



you will need to edit the 
/usr/src/linux/.config 
file yourselfe, but this shouldnt be any hard.

greetings Hannes

---

### Post by digiplaya on 2006-06-06
So, recompile the kernel with your changes to get usplash?

---

### Post by hannes_ on 2006-06-06
[QUOTE=digiplaya]So, recompile the kernel with your changes to get usplash?[/QUOTE]

ya

just edit the file and do the following steps again

[QUOTE=MasterChief1234]
make-kpkg clean
make-kpkg -initrd --revision=ck**XX** kernel_image
[/QUOTE]

I used the ck11 patch and it worked fine for me.

---

### Post by digiplaya on 2006-06-06
Hmm...no usplash yet for me. Tried your steps exactly, too. Is this common on 2.6.16?

---

### Post by hannes_ on 2006-06-06
let me see your .config pls, gonna have a look at it.

also make sure your /boot/grub/menu.lst entry is like this

title           Ubuntu, kernel 2.6.16-ck11
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.16-ck11 root=/dev/hda1 ro quiet splash vga=795
initrd          /boot/initrd.img-2.6.16-ck11
savedefault
boot



greetings

---

### Post by digiplaya on 2006-06-06
Attached is my .config...I noticed that with the new package made, it still says "vmlinuz-2.6.16-ck3" instead of "vmlinuz-2.6.16-ck11" as well as "initrd-2.6.16-ck3" under /boot.

> 
#
# Automatically generated make config: don't edit
# Linux kernel version: 2.6.16-ck3
# Mon Jun  5 23:18:26 2006
#
CONFIG_X86_32=y
CONFIG_SEMAPHORE_SLEEPERS=y
CONFIG_X86=y
CONFIG_MMU=y
CONFIG_GENERIC_ISA_DMA=y
CONFIG_GENERIC_IOMAP=y
CONFIG_ARCH_MAY_HAVE_PC_FDC=y
CONFIG_DMI=y

#
# Code maturity level options
#
CONFIG_EXPERIMENTAL=y
CONFIG_BROKEN_ON_SMP=y
CONFIG_INIT_ENV_ARG_LIMIT=32

#
# General setup
#
CONFIG_LOCALVERSION=""
# CONFIG_LOCALVERSION_AUTO is not set
CONFIG_SWAP=y
CONFIG_SWAP_PREFETCH=y
CONFIG_SYSVIPC=y
CONFIG_POSIX_MQUEUE=y
CONFIG_BSD_PROCESS_ACCT=y
CONFIG_BSD_PROCESS_ACCT_V3=y
CONFIG_SYSCTL=y
CONFIG_AUDIT=y
# CONFIG_AUDITSYSCALL is not set
# CONFIG_IKCONFIG is not set
CONFIG_INITRAMFS_SOURCE=""
CONFIG_UID16=y
CONFIG_VM86=y
# CONFIG_CC_OPTIMIZE_FOR_SIZE is not set
# CONFIG_EMBEDDED is not set
CONFIG_KALLSYMS=y
# CONFIG_KALLSYMS_EXTRA_PASS is not set
CONFIG_HOTPLUG=y
CONFIG_PRINTK=y
CONFIG_BUG=y
CONFIG_ELF_CORE=y
CONFIG_BASE_FULL=y
CONFIG_FUTEX=y
CONFIG_EPOLL=y
CONFIG_SHMEM=y
CONFIG_CC_ALIGN_FUNCTIONS=0
CONFIG_CC_ALIGN_LABELS=0
CONFIG_CC_ALIGN_LOOPS=0
CONFIG_CC_ALIGN_JUMPS=0
CONFIG_SLAB=y
# CONFIG_TINY_SHMEM is not set
CONFIG_BASE_SMALL=0
# CONFIG_SLOB is not set
CONFIG_OBSOLETE_INTERMODULE=m

#
# Loadable module support
#
CONFIG_MODULES=y
CONFIG_MODULE_UNLOAD=y
# CONFIG_MODULE_FORCE_UNLOAD is not set
CONFIG_OBSOLETE_MODPARM=y
CONFIG_MODVERSIONS=y
CONFIG_MODULE_SRCVERSION_ALL=y
CONFIG_KMOD=y

#
# Block layer
#
CONFIG_LBD=y

#
# IO Schedulers
#
CONFIG_IOSCHED_NOOP=y
CONFIG_IOSCHED_AS=y
CONFIG_IOSCHED_DEADLINE=y
CONFIG_IOSCHED_CFQ=y
CONFIG_DEFAULT_AS=y
# CONFIG_DEFAULT_DEADLINE is not set
# CONFIG_DEFAULT_CFQ is not set
# CONFIG_DEFAULT_NOOP is not set
CONFIG_DEFAULT_IOSCHED="anticipatory"

#
# Processor type and features
#
CONFIG_X86_PC=y
# CONFIG_X86_ELAN is not set
# CONFIG_X86_VOYAGER is not set
# CONFIG_X86_NUMAQ is not set
# CONFIG_X86_SUMMIT is not set
# CONFIG_X86_BIGSMP is not set
# CONFIG_X86_VISWS is not set
# CONFIG_X86_GENERICARCH is not set
# CONFIG_X86_ES7000 is not set
# CONFIG_M386 is not set
# CONFIG_M486 is not set
# CONFIG_M586 is not set
# CONFIG_M586TSC is not set
# CONFIG_M586MMX is not set
# CONFIG_M686 is not set
# CONFIG_MPENTIUMII is not set
# CONFIG_MPENTIUMIII is not set
# CONFIG_MPENTIUMM is not set
CONFIG_MPENTIUM4=y
# CONFIG_MK6 is not set
# CONFIG_MK7 is not set
# CONFIG_MK8 is not set
# CONFIG_MCRUSOE is not set
# CONFIG_MEFFICEON is not set
# CONFIG_MWINCHIPC6 is not set
# CONFIG_MWINCHIP2 is not set
# CONFIG_MWINCHIP3D is not set
# CONFIG_MGEODEGX1 is not set
# CONFIG_MGEODE_LX is not set
# CONFIG_MCYRIXIII is not set
# CONFIG_MVIAC3_2 is not set
CONFIG_X86_GENERIC=y
CONFIG_X86_CMPXCHG=y
CONFIG_X86_XADD=y
CONFIG_X86_L1_CACHE_SHIFT=7
CONFIG_RWSEM_XCHGADD_ALGORITHM=y
CONFIG_GENERIC_CALIBRATE_DELAY=y
CONFIG_X86_WP_WORKS_OK=y
CONFIG_X86_INVLPG=y
CONFIG_X86_BSWAP=y
CONFIG_X86_POPAD_OK=y
CONFIG_X86_CMPXCHG64=y
CONFIG_X86_GOOD_APIC=y
CONFIG_X86_INTEL_USERCOPY=y
CONFIG_X86_USE_PPRO_CHECKSUM=y
CONFIG_X86_TSC=y
CONFIG_HPET_TIMER=y
# CONFIG_SMP is not set
# CONFIG_PREEMPT_NONE is not set
CONFIG_PREEMPT_VOLUNTARY=y
# CONFIG_PREEMPT is not set
CONFIG_X86_UP_APIC=y
CONFIG_X86_UP_IOAPIC=y
CONFIG_X86_LOCAL_APIC=y
CONFIG_X86_IO_APIC=y
# CONFIG_X86_MCE is not set
CONFIG_TOSHIBA=m
CONFIG_I8K=m
CONFIG_X86_REBOOTFIXUPS=y
CONFIG_MICROCODE=m
CONFIG_X86_MSR=m
CONFIG_X86_CPUID=m

#
# Firmware Drivers
#
# CONFIG_EDD is not set
CONFIG_EFI_VARS=y
CONFIG_DELL_RBU=m
CONFIG_DCDBAS=m
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set
CONFIG_VMSPLIT_3G=y
# CONFIG_VMSPLIT_3G_OPT is not set
# CONFIG_VMSPLIT_2G is not set
# CONFIG_VMSPLIT_1G is not set
CONFIG_PAGE_OFFSET=0xC0000000
CONFIG_HIGHMEM=y
CONFIG_ARCH_FLATMEM_ENABLE=y
CONFIG_ARCH_SPARSEMEM_ENABLE=y
CONFIG_ARCH_SELECT_MEMORY_MODEL=y
CONFIG_SELECT_MEMORY_MODEL=y
CONFIG_FLATMEM_MANUAL=y
# CONFIG_DISCONTIGMEM_MANUAL is not set
# CONFIG_SPARSEMEM_MANUAL is not set
CONFIG_FLATMEM=y
CONFIG_FLAT_NODE_MEM_MAP=y
CONFIG_SPARSEMEM_STATIC=y
CONFIG_SPLIT_PTLOCK_CPUS=4
# CONFIG_ADAPTIVE_READAHEAD is not set
CONFIG_HIGHPTE=y
CONFIG_MATH_EMULATION=y
CONFIG_MTRR=y
CONFIG_EFI=y
CONFIG_BOOT_IOREMAP=y
# CONFIG_REGPARM is not set
CONFIG_SECCOMP=y
# CONFIG_HZ_100 is not set
# CONFIG_HZ_250_NODEFAULT is not set
CONFIG_HZ_1000=y
CONFIG_HZ=1000
# CONFIG_KEXEC is not set
# CONFIG_CRASH_DUMP is not set
CONFIG_PHYSICAL_START=0x100000
CONFIG_DOUBLEFAULT=y

#
# Power management options (ACPI, APM)
#
CONFIG_PM=y
CONFIG_PM_LEGACY=y
# CONFIG_PM_DEBUG is not set
CONFIG_SOFTWARE_SUSPEND=y
CONFIG_PM_STD_PARTITION=""

#
# ACPI (Advanced Configuration and Power Interface) Support
#
CONFIG_ACPI=y
CONFIG_ACPI_SLEEP=y
CONFIG_ACPI_SLEEP_PROC_FS=y
CONFIG_ACPI_SLEEP_PROC_SLEEP=y
CONFIG_ACPI_AC=m
CONFIG_ACPI_BATTERY=m
CONFIG_ACPI_BUTTON=m
CONFIG_ACPI_VIDEO=m
CONFIG_ACPI_HOTKEY=m
CONFIG_ACPI_FAN=m
CONFIG_ACPI_PROCESSOR=m
CONFIG_ACPI_THERMAL=m
CONFIG_ACPI_ASUS=m
CONFIG_ACPI_IBM=m
CONFIG_ACPI_TOSHIBA=m
CONFIG_ACPI_BLACKLIST_YEAR=2000
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_EC=y
CONFIG_ACPI_POWER=y
CONFIG_ACPI_SYSTEM=y
CONFIG_X86_PM_TIMER=y
CONFIG_ACPI_CONTAINER=m

#
# User Modules And Translation Layers
#
CONFIG_MTD_CHAR=m
CONFIG_MTD_BLOCK=m
CONFIG_MTD_BLOCK_RO=m
CONFIG_FTL=m
CONFIG_NFTL=m
CONFIG_NFTL_RW=y
CONFIG_INFTL=m
CONFIG_RFD_FTL=m

#
# RAM/ROM/Flash chip drivers
#
CONFIG_MTD_CFI=m
CONFIG_MTD_JEDECPROBE=m
CONFIG_MTD_GEN_PROBE=m
# CONFIG_MTD_CFI_ADV_OPTIONS is not set
CONFIG_MTD_MAP_BANK_WIDTH_1=y
CONFIG_MTD_MAP_BANK_WIDTH_2=y
CONFIG_MTD_MAP_BANK_WIDTH_4=y
# CONFIG_MTD_MAP_BANK_WIDTH_8 is not set
# CONFIG_MTD_MAP_BANK_WIDTH_16 is not set
# CONFIG_MTD_MAP_BANK_WIDTH_32 is not set
CONFIG_MTD_CFI_I1=y
CONFIG_MTD_CFI_I2=y
# CONFIG_MTD_CFI_I4 is not set
# CONFIG_MTD_CFI_I8 is not set
CONFIG_MTD_CFI_INTELEXT=m
CONFIG_MTD_CFI_AMDSTD=m
CONFIG_MTD_CFI_AMDSTD_RETRY=0
CONFIG_MTD_CFI_STAA=m
CONFIG_MTD_CFI_UTIL=m
CONFIG_MTD_RAM=m
CONFIG_MTD_ROM=m
CONFIG_MTD_ABSENT=m
# CONFIG_MTD_OBSOLETE_CHIPS is not set

#
# Mapping drivers for chip access
#
CONFIG_MTD_COMPLEX_MAPPINGS=y
CONFIG_MTD_PHYSMAP=m
CONFIG_MTD_PHYSMAP_START=0x8000000
CONFIG_MTD_PHYSMAP_LEN=0x4000000
CONFIG_MTD_PHYSMAP_BANKWIDTH=2
CONFIG_MTD_PNC2000=m
CONFIG_MTD_SC520CDP=m
CONFIG_MTD_NETSC520=m
CONFIG_MTD_TS5500=m
CONFIG_MTD_SBC_GXX=m
CONFIG_MTD_SCx200_DOCFLASH=m
CONFIG_MTD_AMD76XROM=m
CONFIG_MTD_ICHXROM=m
CONFIG_MTD_SCB2_FLASH=m
CONFIG_MTD_NETtel=m
CONFIG_MTD_DILNETPC=m
CONFIG_MTD_DILNETPC_BOOTSIZE=0x80000
CONFIG_MTD_L440GX=m
CONFIG_MTD_PCI=m
CONFIG_MTD_PLATRAM=m

#
# Self-contained MTD device drivers
#
CONFIG_MTD_PMC551=m
# CONFIG_MTD_PMC551_BUGFIX is not set
# CONFIG_MTD_PMC551_DEBUG is not set
CONFIG_MTD_SLRAM=m
CONFIG_MTD_PHRAM=m
CONFIG_MTD_MTDRAM=m
CONFIG_MTDRAM_TOTAL_SIZE=4096
CONFIG_MTDRAM_ERASE_SIZE=128
CONFIG_MTD_BLKMTD=m
CONFIG_MTD_BLOCK2MTD=m

#
# Disk-On-Chip Device Drivers
#
CONFIG_MTD_DOC2000=m
CONFIG_MTD_DOC2001=m
CONFIG_MTD_DOC2001PLUS=m
CONFIG_MTD_DOCPROBE=m
CONFIG_MTD_DOCECC=m
# CONFIG_MTD_DOCPROBE_ADVANCED is not set
CONFIG_MTD_DOCPROBE_ADDRESS=0

#
# NAND Flash Device Drivers
#
CONFIG_MTD_NAND=m
# CONFIG_MTD_NAND_VERIFY_WRITE is not set
CONFIG_MTD_NAND_IDS=m
CONFIG_MTD_NAND_DISKONCHIP=m
# CONFIG_MTD_NAND_DISKONCHIP_PROBE_ADVANCED is not set
CONFIG_MTD_NAND_DISKONCHIP_PROBE_ADDRESS=0
# CONFIG_MTD_NAND_DISKONCHIP_BBTWRITE is not set
CONFIG_MTD_NAND_NANDSIM=y

#
# OneNAND Flash Device Drivers
#
CONFIG_MTD_ONENAND=m
CONFIG_MTD_ONENAND_VERIFY_WRITE=y

#
# Parallel port support
#
CONFIG_PARPORT=m
CONFIG_PARPORT_PC=m
CONFIG_PARPORT_SERIAL=m
CONFIG_PARPORT_PC_FIFO=y
# CONFIG_PARPORT_PC_SUPERIO is not set
CONFIG_PARPORT_PC_PCMCIA=m
CONFIG_PARPORT_NOT_PC=y
# CONFIG_PARPORT_GSC is not set
CONFIG_PARPORT_1284=y

#
# Plug and Play support
#
CONFIG_PNP=y
# CONFIG_PNP_DEBUG is not set

#
# Protocols
#
CONFIG_ISAPNP=y
CONFIG_PNPBIOS=y
CONFIG_PNPBIOS_PROC_FS=y
CONFIG_PNPACPI=y

#
# Block devices
#
CONFIG_BLK_DEV_FD=m
CONFIG_BLK_DEV_XD=m
CONFIG_PARIDE=m
CONFIG_PARIDE_PARPORT=m

#
# Parallel IDE high-level drivers
#
CONFIG_PARIDE_PD=m
CONFIG_PARIDE_PCD=m
CONFIG_PARIDE_PF=m
CONFIG_PARIDE_PT=m
CONFIG_PARIDE_PG=m

#
# Parallel IDE protocol modules
#
CONFIG_PARIDE_ATEN=m
CONFIG_PARIDE_BPCK=m
CONFIG_PARIDE_BPCK6=m
CONFIG_PARIDE_COMM=m
CONFIG_PARIDE_DSTR=m
CONFIG_PARIDE_FIT2=m
CONFIG_PARIDE_FIT3=m
CONFIG_PARIDE_EPAT=m
# CONFIG_PARIDE_EPATC8 is not set
CONFIG_PARIDE_EPIA=m
CONFIG_PARIDE_FRIQ=m
CONFIG_PARIDE_FRPW=m
CONFIG_PARIDE_KBIC=m
CONFIG_PARIDE_KTTI=m
CONFIG_PARIDE_ON20=m
CONFIG_PARIDE_ON26=m
CONFIG_BLK_CPQ_DA=m
CONFIG_BLK_CPQ_CISS_DA=m
CONFIG_CISS_SCSI_TAPE=y
CONFIG_BLK_DEV_DAC960=m
CONFIG_BLK_DEV_UMEM=m
# CONFIG_BLK_DEV_COW_COMMON is not set
CONFIG_BLK_DEV_LOOP=m
CONFIG_BLK_DEV_CRYPTOLOOP=m
CONFIG_BLK_DEV_NBD=m
CONFIG_BLK_DEV_SX8=m
# CONFIG_BLK_DEV_UB is not set
CONFIG_BLK_DEV_RAM=y
CONFIG_BLK_DEV_RAM_COUNT=16
CONFIG_BLK_DEV_RAM_SIZE=65536
CONFIG_BLK_DEV_INITRD=y
CONFIG_CDROM_PKTCDVD=m
CONFIG_CDROM_PKTCDVD_BUFFERS=8
# CONFIG_CDROM_PKTCDVD_WCACHE is not set
CONFIG_ATA_OVER_ETH=m

#
# ATA/ATAPI/MFM/RLL support
#
CONFIG_IDE=y
CONFIG_BLK_DEV_IDE=y

#
# Please see Documentation/ide.txt for help/info on IDE drives
#
# CONFIG_BLK_DEV_IDE_SATA is not set
# CONFIG_BLK_DEV_HD_IDE is not set
CONFIG_BLK_DEV_IDEDISK=m
# CONFIG_IDEDISK_MULTI_MODE is not set
CONFIG_BLK_DEV_IDECS=m
CONFIG_BLK_DEV_IDECD=m
CONFIG_BLK_DEV_IDETAPE=m
CONFIG_BLK_DEV_IDEFLOPPY=m
CONFIG_BLK_DEV_IDESCSI=m
# CONFIG_IDE_TASK_IOCTL is not set

#
# IDE chipset support/bugfixes
#
CONFIG_IDE_GENERIC=m
CONFIG_BLK_DEV_CMD640=y
# CONFIG_BLK_DEV_CMD640_ENHANCED is not set
# CONFIG_BLK_DEV_IDEPNP is not set
CONFIG_BLK_DEV_IDEPCI=y
CONFIG_IDEPCI_SHARE_IRQ=y
# CONFIG_BLK_DEV_OFFBOARD is not set
CONFIG_BLK_DEV_GENERIC=m
CONFIG_BLK_DEV_OPTI621=m
CONFIG_BLK_DEV_RZ1000=m
CONFIG_BLK_DEV_IDEDMA_PCI=y
# CONFIG_BLK_DEV_IDEDMA_FORCED is not set
CONFIG_IDEDMA_PCI_AUTO=y
# CONFIG_IDEDMA_ONLYDISK is not set
CONFIG_BLK_DEV_AEC62XX=m
CONFIG_BLK_DEV_ALI15X3=m
# CONFIG_WDC_ALI15X3 is not set
CONFIG_BLK_DEV_AMD74XX=m
CONFIG_BLK_DEV_ATIIXP=m
CONFIG_BLK_DEV_CMD64X=m
CONFIG_BLK_DEV_TRIFLEX=m
CONFIG_BLK_DEV_CY82C693=m
CONFIG_BLK_DEV_CS5520=m
CONFIG_BLK_DEV_CS5530=m
CONFIG_BLK_DEV_CS5535=m
CONFIG_BLK_DEV_HPT34X=m
# CONFIG_HPT34X_AUTODMA is not set
CONFIG_BLK_DEV_HPT366=m
CONFIG_BLK_DEV_SC1200=m
CONFIG_BLK_DEV_PIIX=m
CONFIG_BLK_DEV_IT821X=m
CONFIG_BLK_DEV_NS87415=m
CONFIG_BLK_DEV_PDC202XX_OLD=m
CONFIG_PDC202XX_BURST=y
CONFIG_BLK_DEV_PDC202XX_NEW=m
CONFIG_BLK_DEV_SVWKS=m
CONFIG_BLK_DEV_SIIMAGE=m
CONFIG_BLK_DEV_SIS5513=m
CONFIG_BLK_DEV_SLC90E66=m
CONFIG_BLK_DEV_TRM290=m
CONFIG_BLK_DEV_VIA82CXXX=m
# CONFIG_IDE_ARM is not set
# CONFIG_IDE_CHIPSETS is not set
CONFIG_BLK_DEV_IDEDMA=y
# CONFIG_IDEDMA_IVB is not set
CONFIG_IDEDMA_AUTO=y
# CONFIG_BLK_DEV_HD is not set

#
# SCSI device support
#
CONFIG_RAID_ATTRS=m
CONFIG_SCSI=m
CONFIG_SCSI_PROC_FS=y

#
# SCSI support type (disk, tape, CD-ROM)
#
CONFIG_BLK_DEV_SD=m
CONFIG_CHR_DEV_ST=m
CONFIG_CHR_DEV_OSST=m
CONFIG_BLK_DEV_SR=m
# CONFIG_BLK_DEV_SR_VENDOR is not set
CONFIG_CHR_DEV_SG=m
CONFIG_CHR_DEV_SCH=m

#
# ARCnet devices
#
CONFIG_ARCNET=m
CONFIG_ARCNET_1201=m
CONFIG_ARCNET_1051=m
CONFIG_ARCNET_RAW=m
CONFIG_ARCNET_CAP=m
CONFIG_ARCNET_COM90xx=m
CONFIG_ARCNET_COM90xxIO=m
CONFIG_ARCNET_RIM_I=m
CONFIG_ARCNET_COM20020=m
CONFIG_ARCNET_COM20020_ISA=m
CONFIG_ARCNET_COM20020_PCI=m

#
# PHY device support
#
CONFIG_PHYLIB=m

#
# MII PHY device drivers
#
CONFIG_MARVELL_PHY=m
CONFIG_DAVICOM_PHY=m
CONFIG_QSEMI_PHY=m
CONFIG_LXT_PHY=m
CONFIG_CICADA_PHY=m

#
# Ethernet (10 or 100Mbit)
#
CONFIG_NET_ETHERNET=y
CONFIG_MII=m
CONFIG_HAPPYMEAL=m
CONFIG_SUNGEM=m
CONFIG_CASSINI=m
CONFIG_NET_VENDOR_3COM=y
CONFIG_EL1=m
CONFIG_EL2=m
CONFIG_ELPLUS=m
CONFIG_EL16=m
CONFIG_EL3=m
CONFIG_3C515=m
CONFIG_ELMC=m
CONFIG_ELMC_II=m
CONFIG_VORTEX=m
CONFIG_TYPHOON=m
CONFIG_LANCE=m
CONFIG_NET_VENDOR_SMC=y
CONFIG_WD80x3=m
CONFIG_ULTRAMCA=m
CONFIG_ULTRA=m
CONFIG_ULTRA32=m
CONFIG_SMC9194=m
CONFIG_NET_VENDOR_RACAL=y
CONFIG_NI5010=m
CONFIG_NI52=m
CONFIG_NI65=m

#
# Tulip family network device support
#
CONFIG_NET_TULIP=y
CONFIG_DE2104X=m
CONFIG_TULIP=m
# CONFIG_TULIP_MWI is not set
# CONFIG_TULIP_MMIO is not set
# CONFIG_TULIP_NAPI is not set
CONFIG_DE4X5=m
CONFIG_WINBOND_840=m
CONFIG_DM9102=m
CONFIG_ULI526X=m
CONFIG_PCMCIA_XIRCOM=m
CONFIG_PCMCIA_XIRTULIP=m
CONFIG_AT1700=m
CONFIG_DEPCA=m
CONFIG_HP100=m
CONFIG_NET_ISA=y
CONFIG_E2100=m
CONFIG_EWRK3=m
CONFIG_EEXPRESS=m
CONFIG_EEXPRESS_PRO=m
CONFIG_HPLAN_PLUS=m
CONFIG_HPLAN=m
CONFIG_LP486E=m
CONFIG_ETH16I=m
CONFIG_NE2000=m
CONFIG_ZNET=m
CONFIG_SEEQ8005=m
CONFIG_NE2_MCA=m
CONFIG_IBMLANA=m
CONFIG_NET_PCI=y
CONFIG_PCNET32=m
CONFIG_AMD8111_ETH=m
# CONFIG_AMD8111E_NAPI is not set
CONFIG_ADAPTEC_STARFIRE=m
# CONFIG_ADAPTEC_STARFIRE_NAPI is not set
CONFIG_AC3200=m
CONFIG_APRICOT=m
CONFIG_B44=m
CONFIG_FORCEDETH=m
CONFIG_CS89x0=m
CONFIG_DGRS=m
CONFIG_EEPRO100=m
CONFIG_E100=m
CONFIG_LNE390=m
CONFIG_FEALNX=m
CONFIG_NATSEMI=m
CONFIG_NE2K_PCI=m
CONFIG_NE3210=m
CONFIG_ES3210=m
CONFIG_8139CP=m
CONFIG_8139TOO=m
# CONFIG_8139TOO_PIO is not set
# CONFIG_8139TOO_TUNE_TWISTER is not set
CONFIG_8139TOO_8129=y
# CONFIG_8139_OLD_RX_RESET is not set
CONFIG_SIS900=m
CONFIG_EPIC100=m
CONFIG_SUNDANCE=m
# CONFIG_SUNDANCE_MMIO is not set
CONFIG_TLAN=m
CONFIG_VIA_RHINE=m
# CONFIG_VIA_RHINE_MMIO is not set
CONFIG_NET_POCKET=y
CONFIG_ATP=m
CONFIG_DE600=m
CONFIG_DE620=m

#
# Ethernet (1000 Mbit)
#
CONFIG_ACENIC=m
# CONFIG_ACENIC_OMIT_TIGON_I is not set
CONFIG_DL2K=m
CONFIG_E1000=m
# CONFIG_E1000_NAPI is not set
# CONFIG_E1000_DISABLE_PACKET_SPLIT is not set
CONFIG_NS83820=m
CONFIG_HAMACHI=m
CONFIG_YELLOWFIN=m
CONFIG_R8169=m
# CONFIG_R8169_NAPI is not set
CONFIG_R8169_VLAN=y
CONFIG_SIS190=m
CONFIG_SKGE=m
CONFIG_SKY2=m
CONFIG_SK98LIN=m
CONFIG_VIA_VELOCITY=m
CONFIG_TIGON3=m
CONFIG_BNX2=m

#
# Ethernet (10000 Mbit)
#
CONFIG_CHELSIO_T1=m
CONFIG_IXGB=m
# CONFIG_IXGB_NAPI is not set
CONFIG_S2IO=m
# CONFIG_S2IO_NAPI is not set

#
# Token Ring devices
#
CONFIG_TR=y
CONFIG_IBMTR=m
CONFIG_IBMOL=m
CONFIG_IBMLS=m
CONFIG_3C359=m
CONFIG_TMS380TR=m
CONFIG_TMSPCI=m
CONFIG_SKISA=m
CONFIG_PROTEON=m
CONFIG_ABYSS=m
CONFIG_MADGEMC=m
CONFIG_SMCTR=m

#
# Wireless LAN (non-hamradio)
#
CONFIG_NET_RADIO=y

#
# Obsolete Wireless cards support (pre-802.11)
#
CONFIG_STRIP=m
CONFIG_ARLAN=m
CONFIG_WAVELAN=m
CONFIG_PCMCIA_WAVELAN=m
CONFIG_PCMCIA_NETWAVE=m

#
# Wireless 802.11 Frequency Hopping cards support
#
CONFIG_PCMCIA_RAYCS=m

#
# Wireless 802.11b ISA/PCI cards support
#
CONFIG_IPW2100=m
CONFIG_IPW2100_MONITOR=y
# CONFIG_IPW2100_DEBUG is not set
CONFIG_IPW2200=m
# CONFIG_IPW2200_DEBUG is not set
CONFIG_AIRO=m
CONFIG_HERMES=m
CONFIG_PLX_HERMES=m
CONFIG_TMD_HERMES=m
CONFIG_NORTEL_HERMES=m
CONFIG_PCI_HERMES=m
CONFIG_ATMEL=m
CONFIG_PCI_ATMEL=m

#
# Wireless 802.11b Pcmcia/Cardbus cards support
#
CONFIG_PCMCIA_HERMES=m
CONFIG_PCMCIA_SPECTRUM=m
CONFIG_AIRO_CS=m
CONFIG_PCMCIA_ATMEL=m
CONFIG_PCMCIA_WL3501=m

#
# Prism GT/Duette 802.11(a/b/g) PCI/Cardbus support
#
CONFIG_PRISM54=m
CONFIG_HOSTAP=m
CONFIG_HOSTAP_FIRMWARE=y
# CONFIG_HOSTAP_FIRMWARE_NVRAM is not set
CONFIG_HOSTAP_PLX=m
CONFIG_HOSTAP_PCI=m
CONFIG_HOSTAP_CS=m
CONFIG_NET_WIRELESS=y

#
# PCMCIA network device support
#
CONFIG_NET_PCMCIA=y
CONFIG_PCMCIA_3C589=m
CONFIG_PCMCIA_3C574=m
CONFIG_PCMCIA_FMVJ18X=m
CONFIG_PCMCIA_PCNET=m
CONFIG_PCMCIA_NMCLAN=m
CONFIG_PCMCIA_SMC91C92=m
CONFIG_PCMCIA_XIRC2PS=m
CONFIG_PCMCIA_AXNET=m
CONFIG_ARCNET_COM20020_CS=m
CONFIG_PCMCIA_IBMTR=m

#
# Wan interfaces
#
CONFIG_WAN=y
CONFIG_HOSTESS_SV11=m
CONFIG_COSA=m
CONFIG_DSCC4=m
CONFIG_DSCC4_PCISYNC=y
CONFIG_DSCC4_PCI_RST=y
CONFIG_LANMEDIA=m
CONFIG_SEALEVEL_4021=m
CONFIG_SYNCLINK_SYNCPPP=m
CONFIG_HDLC=m
CONFIG_HDLC_RAW=y
CONFIG_HDLC_RAW_ETH=y
CONFIG_HDLC_CISCO=y
CONFIG_HDLC_FR=y
CONFIG_HDLC_PPP=y
CONFIG_HDLC_X25=y
CONFIG_PCI200SYN=m
CONFIG_WANXL=m
CONFIG_PC300=m
CONFIG_PC300_MLPPP=y
CONFIG_N2=m
CONFIG_C101=m
CONFIG_FARSYNC=m
CONFIG_DLCI=m
CONFIG_DLCI_COUNT=24
CONFIG_DLCI_MAX=8
CONFIG_SDLA=m
CONFIG_WAN_ROUTER_DRIVERS=y
CONFIG_CYCLADES_SYNC=m
CONFIG_CYCLOMX_X25=y
CONFIG_LAPBETHER=m
CONFIG_X25_ASY=m
CONFIG_SBNI=m
# CONFIG_SBNI_MULTILINE is not set

#
# ATM drivers
#
# CONFIG_ATM_DUMMY is not set
CONFIG_ATM_TCP=m
CONFIG_ATM_LANAI=m
CONFIG_ATM_ENI=m
# CONFIG_ATM_ENI_DEBUG is not set
# CONFIG_ATM_ENI_TUNE_BURST is not set
CONFIG_ATM_FIRESTREAM=m
CONFIG_ATM_ZATM=m
# CONFIG_ATM_ZATM_DEBUG is not set
CONFIG_ATM_NICSTAR=m
# CONFIG_ATM_NICSTAR_USE_SUNI is not set
# CONFIG_ATM_NICSTAR_USE_IDT77105 is not set
CONFIG_ATM_IDT77252=m
# CONFIG_ATM_IDT77252_DEBUG is not set
# CONFIG_ATM_IDT77252_RCV_ALL is not set
CONFIG_ATM_IDT77252_USE_SUNI=y
CONFIG_ATM_AMBASSADOR=m
# CONFIG_ATM_AMBASSADOR_DEBUG is not set
CONFIG_ATM_HORIZON=m
# CONFIG_ATM_HORIZON_DEBUG is not set
CONFIG_ATM_IA=m
# CONFIG_ATM_IA_DEBUG is not set
CONFIG_ATM_FORE200E_MAYBE=m
CONFIG_ATM_FORE200E_PCA=y
CONFIG_ATM_FORE200E_PCA_DEFAULT_FW=y
# CONFIG_ATM_FORE200E_USE_TASKLET is not set
CONFIG_ATM_FORE200E_TX_RETRY=16
CONFIG_ATM_FORE200E_DEBUG=0
CONFIG_ATM_FORE200E=m
CONFIG_ATM_HE=m
CONFIG_ATM_HE_USE_SUNI=y
CONFIG_FDDI=y
CONFIG_DEFXX=m
CONFIG_SKFP=m
CONFIG_HIPPI=y
CONFIG_ROADRUNNER=m
# CONFIG_ROADRUNNER_LARGE_RINGS is not set
CONFIG_PLIP=m
CONFIG_PPP=m
CONFIG_PPP_MULTILINK=y
CONFIG_PPP_FILTER=y
CONFIG_PPP_ASYNC=m
CONFIG_PPP_SYNC_TTY=m
CONFIG_PPP_DEFLATE=m
CONFIG_PPP_BSDCOMP=m
CONFIG_PPP_MPPE=m
CONFIG_PPPOE=m
CONFIG_PPPOATM=m
CONFIG_SLIP=m
CONFIG_SLIP_COMPRESSED=y
CONFIG_SLIP_SMART=y
CONFIG_SLIP_MODE_SLIP6=y
CONFIG_NET_FC=y
CONFIG_SHAPER=m
CONFIG_NETCONSOLE=m
CONFIG_NETPOLL=y
# CONFIG_NETPOLL_RX is not set
# CONFIG_NETPOLL_TRAP is not set
CONFIG_NET_POLL_CONTROLLER=y

#
# ISDN subsystem
#
CONFIG_ISDN=m

#
# Old ISDN4Linux
#
CONFIG_ISDN_I4L=m
CONFIG_ISDN_PPP=y
CONFIG_ISDN_PPP_VJ=y
CONFIG_ISDN_MPP=y
CONFIG_IPPP_FILTER=y
CONFIG_ISDN_PPP_BSDCOMP=m
CONFIG_ISDN_AUDIO=y
CONFIG_ISDN_TTY_FAX=y
CONFIG_ISDN_X25=y

#
# ISDN feature submodules
#
CONFIG_ISDN_DRV_LOOP=m
CONFIG_ISDN_DIVERSION=m

#
# ISDN4Linux hardware drivers
#

#
# Passive cards
#
CONFIG_ISDN_DRV_HISAX=m

#
# D-channel protocol features
#
CONFIG_HISAX_EURO=y
CONFIG_DE_AOC=y
# CONFIG_HISAX_NO_SENDCOMPLETE is not set
# CONFIG_HISAX_NO_LLC is not set
# CONFIG_HISAX_NO_KEYPAD is not set
CONFIG_HISAX_1TR6=y
CONFIG_HISAX_NI1=y
CONFIG_HISAX_MAX_CARDS=8

#
# HiSax supported cards
#
CONFIG_HISAX_16_0=y
CONFIG_HISAX_16_3=y
CONFIG_HISAX_TELESPCI=y
CONFIG_HISAX_S0BOX=y
CONFIG_HISAX_AVM_A1=y
CONFIG_HISAX_FRITZPCI=y
CONFIG_HISAX_AVM_A1_PCMCIA=y
CONFIG_HISAX_ELSA=y
CONFIG_HISAX_IX1MICROR2=y
CONFIG_HISAX_DIEHLDIVA=y
CONFIG_HISAX_ASUSCOM=y
CONFIG_HISAX_TELEINT=y
CONFIG_HISAX_HFCS=y
CONFIG_HISAX_SEDLBAUER=y
CONFIG_HISAX_SPORTSTER=y
CONFIG_HISAX_MIC=y
CONFIG_HISAX_NETJET=y
CONFIG_HISAX_NETJET_U=y
CONFIG_HISAX_NICCY=y
CONFIG_HISAX_ISURF=y
CONFIG_HISAX_HSTSAPHIR=y
CONFIG_HISAX_BKM_A4T=y
CONFIG_HISAX_SCT_QUADRO=y
CONFIG_HISAX_GAZEL=y
CONFIG_HISAX_HFC_PCI=y
CONFIG_HISAX_W6692=y
CONFIG_HISAX_HFC_SX=y
CONFIG_HISAX_ENTERNOW_PCI=y
# CONFIG_HISAX_DEBUG is not set

#
# HiSax PCMCIA card service modules
#
CONFIG_HISAX_SEDLBAUER_CS=m
CONFIG_HISAX_ELSA_CS=m
CONFIG_HISAX_AVM_A1_CS=m
CONFIG_HISAX_TELES_CS=m

#
# HiSax sub driver modules
#
CONFIG_HISAX_ST5481=m
CONFIG_HISAX_HFCUSB=m
CONFIG_HISAX_HFC4S8S=m
CONFIG_HISAX_FRITZ_PCIPNP=m
CONFIG_HISAX_HDLC=y

#
# Active cards
#
CONFIG_ISDN_DRV_ICN=m
CONFIG_ISDN_DRV_PCBIT=m
CONFIG_ISDN_DRV_SC=m
CONFIG_ISDN_DRV_ACT2000=m
CONFIG_HYSDN=m
CONFIG_HYSDN_CAPI=y

#
# CAPI subsystem
#
CONFIG_ISDN_CAPI=m
CONFIG_ISDN_DRV_AVMB1_VERBOSE_REASON=y
CONFIG_ISDN_CAPI_MIDDLEWARE=y
CONFIG_ISDN_CAPI_CAPI20=m
CONFIG_ISDN_CAPI_CAPIFS_BOOL=y
CONFIG_ISDN_CAPI_CAPIFS=m
CONFIG_ISDN_CAPI_CAPIDRV=m

#
# CAPI hardware drivers
#

#
# Active AVM cards
#
CONFIG_CAPI_AVM=y
CONFIG_ISDN_DRV_AVMB1_B1ISA=m
CONFIG_ISDN_DRV_AVMB1_B1PCI=m
CONFIG_ISDN_DRV_AVMB1_B1PCIV4=y
CONFIG_ISDN_DRV_AVMB1_T1ISA=m
CONFIG_ISDN_DRV_AVMB1_B1PCMCIA=m
CONFIG_ISDN_DRV_AVMB1_AVM_CS=m
CONFIG_ISDN_DRV_AVMB1_T1PCI=m
CONFIG_ISDN_DRV_AVMB1_C4=m

#
# Active Eicon DIVA Server cards
#
CONFIG_CAPI_EICON=y
CONFIG_ISDN_DIVAS=m
CONFIG_ISDN_DIVAS_BRIPCI=y
CONFIG_ISDN_DIVAS_PRIPCI=y
CONFIG_ISDN_DIVAS_DIVACAPI=m
CONFIG_ISDN_DIVAS_USERIDI=m
CONFIG_ISDN_DIVAS_MAINT=m

#
# Telephony Support
#
CONFIG_PHONE=m
CONFIG_PHONE_IXJ=m
CONFIG_PHONE_IXJ_PCMCIA=m

#
# Input device support
#
CONFIG_INPUT=y

#
# Userland interfaces
#
CONFIG_INPUT_MOUSEDEV=y
CONFIG_INPUT_MOUSEDEV_PSAUX=y
CONFIG_INPUT_MOUSEDEV_SCREEN_X=1024
CONFIG_INPUT_MOUSEDEV_SCREEN_Y=768
CONFIG_INPUT_JOYDEV=m
CONFIG_INPUT_TSDEV=m
CONFIG_INPUT_TSDEV_SCREEN_X=240
CONFIG_INPUT_TSDEV_SCREEN_Y=320
CONFIG_INPUT_EVDEV=m
CONFIG_INPUT_EVBUG=m

#
# Input Device Drivers
#
CONFIG_INPUT_KEYBOARD=y
CONFIG_KEYBOARD_ATKBD=y
CONFIG_KEYBOARD_SUNKBD=m
CONFIG_KEYBOARD_LKKBD=m
CONFIG_KEYBOARD_XTKBD=m
CONFIG_KEYBOARD_NEWTON=m
CONFIG_INPUT_MOUSE=y
CONFIG_MOUSE_PS2=m
CONFIG_MOUSE_SERIAL=m
CONFIG_MOUSE_INPORT=m
# CONFIG_MOUSE_ATIXL is not set
CONFIG_MOUSE_LOGIBM=m
CONFIG_MOUSE_PC110PAD=m
CONFIG_MOUSE_VSXXXAA=m
CONFIG_INPUT_JOYSTICK=y
CONFIG_JOYSTICK_ANALOG=m
CONFIG_JOYSTICK_A3D=m
CONFIG_JOYSTICK_ADI=m
CONFIG_JOYSTICK_COBRA=m
CONFIG_JOYSTICK_GF2K=m
CONFIG_JOYSTICK_GRIP=m
CONFIG_JOYSTICK_GRIP_MP=m
CONFIG_JOYSTICK_GUILLEMOT=m
CONFIG_JOYSTICK_INTERACT=m
CONFIG_JOYSTICK_SIDEWINDER=m
CONFIG_JOYSTICK_TMDC=m
CONFIG_JOYSTICK_IFORCE=m
CONFIG_JOYSTICK_IFORCE_USB=y
CONFIG_JOYSTICK_IFORCE_232=y
CONFIG_JOYSTICK_WARRIOR=m
CONFIG_JOYSTICK_MAGELLAN=m
CONFIG_JOYSTICK_SPACEORB=m
CONFIG_JOYSTICK_SPACEBALL=m
CONFIG_JOYSTICK_STINGER=m
CONFIG_JOYSTICK_TWIDJOY=m
CONFIG_JOYSTICK_DB9=m
CONFIG_JOYSTICK_GAMECON=m
CONFIG_JOYSTICK_TURBOGRAFX=m
CONFIG_JOYSTICK_JOYDUMP=m
CONFIG_INPUT_TOUCHSCREEN=y
CONFIG_TOUCHSCREEN_GUNZE=m
CONFIG_TOUCHSCREEN_ELO=m
CONFIG_TOUCHSCREEN_MTOUCH=m
CONFIG_TOUCHSCREEN_MK712=m
CONFIG_INPUT_MISC=y
CONFIG_INPUT_PCSPKR=m
CONFIG_INPUT_WISTRON_BTNS=m
CONFIG_INPUT_UINPUT=m

#
# Hardware I/O ports
#
CONFIG_SERIO=y
CONFIG_SERIO_I8042=y
CONFIG_SERIO_SERPORT=m
CONFIG_SERIO_CT82C710=m
CONFIG_SERIO_PARKBD=m
CONFIG_SERIO_PCIPS2=m
CONFIG_SERIO_LIBPS2=y
CONFIG_SERIO_RAW=m
CONFIG_GAMEPORT=m
CONFIG_GAMEPORT_NS558=m
CONFIG_GAMEPORT_L4=m
CONFIG_GAMEPORT_EMU10K1=m
CONFIG_GAMEPORT_FM801=m

#
# Character devices
#
CONFIG_VT=y
CONFIG_VT_CONSOLE=y
CONFIG_HW_CONSOLE=y
CONFIG_SERIAL_NONSTANDARD=y
CONFIG_COMPUTONE=m
CONFIG_ROCKETPORT=m
CONFIG_CYCLADES=m
# CONFIG_CYZ_INTR is not set
CONFIG_DIGIEPCA=m
# CONFIG_ESPSERIAL is not set
CONFIG_MOXA_INTELLIO=m
CONFIG_MOXA_SMARTIO=m
# CONFIG_ISI is not set
CONFIG_SYNCLINK=m
CONFIG_SYNCLINKMP=m
# CONFIG_SYNCLINK_GT is not set
CONFIG_N_HDLC=m
CONFIG_RISCOM8=m
CONFIG_SPECIALIX=m
# CONFIG_SPECIALIX_RTSCTS is not set
CONFIG_SX=m
CONFIG_RIO=m
CONFIG_RIO_OLDPCI=y
CONFIG_STALDRV=y
CONFIG_STALLION=m
CONFIG_ISTALLION=m

#
# Serial drivers
#
CONFIG_SERIAL_8250=y
CONFIG_SERIAL_8250_CONSOLE=y
CONFIG_SERIAL_8250_CS=m
# CONFIG_SERIAL_8250_ACPI is not set
CONFIG_SERIAL_8250_NR_UARTS=48
CONFIG_SERIAL_8250_RUNTIME_UARTS=4
CONFIG_SERIAL_8250_EXTENDED=y
CONFIG_SERIAL_8250_MANY_PORTS=y
CONFIG_SERIAL_8250_SHARE_IRQ=y
# CONFIG_SERIAL_8250_DETECT_IRQ is not set
CONFIG_SERIAL_8250_RSA=y
CONFIG_SERIAL_8250_FOURPORT=m
CONFIG_SERIAL_8250_ACCENT=m
CONFIG_SERIAL_8250_BOCA=m
CONFIG_SERIAL_8250_HUB6=m
CONFIG_SERIAL_8250_MCA=m

#
# Non-8250 serial port support
#
CONFIG_SERIAL_CORE=y
CONFIG_SERIAL_CORE_CONSOLE=y
CONFIG_SERIAL_JSM=m
CONFIG_UNIX98_PTYS=y
CONFIG_LEGACY_PTYS=y
CONFIG_LEGACY_PTY_COUNT=256
CONFIG_PRINTER=m
# CONFIG_LP_CONSOLE is not set
CONFIG_PPDEV=m
CONFIG_TIPAR=m

#
# IPMI
#
CONFIG_IPMI_HANDLER=m
# CONFIG_IPMI_PANIC_EVENT is not set
CONFIG_IPMI_DEVICE_INTERFACE=m
CONFIG_IPMI_SI=m
CONFIG_IPMI_WATCHDOG=m
CONFIG_IPMI_POWEROFF=m

#
# Watchdog Cards
#
CONFIG_WATCHDOG=y
# CONFIG_WATCHDOG_NOWAYOUT is not set

#
# Watchdog Device Drivers
#
CONFIG_SOFT_WATCHDOG=m
CONFIG_ACQUIRE_WDT=m
CONFIG_ADVANTECH_WDT=m
CONFIG_ALIM1535_WDT=m
CONFIG_ALIM7101_WDT=m
CONFIG_SC520_WDT=m
CONFIG_EUROTECH_WDT=m
CONFIG_IB700_WDT=m
CONFIG_IBMASR=m
CONFIG_WAFER_WDT=m
CONFIG_I6300ESB_WDT=m
CONFIG_I8XX_TCO=m
CONFIG_SC1200_WDT=m
CONFIG_SCx200_WDT=m
CONFIG_60XX_WDT=m
CONFIG_SBC8360_WDT=m
CONFIG_CPU5_WDT=m
CONFIG_W83627HF_WDT=m
CONFIG_W83877F_WDT=m
CONFIG_W83977F_WDT=m
CONFIG_MACHZ_WDT=m
# CONFIG_SBC_EPX_C3_WATCHDOG is not set

#
# ISA-based Watchdog Cards
#
CONFIG_PCWATCHDOG=m
CONFIG_MIXCOMWD=m
CONFIG_WDT=m
CONFIG_WDT_501=y

#
# PCI-based Watchdog Cards
#
CONFIG_PCIPCWATCHDOG=m
CONFIG_WDTPCI=m
CONFIG_WDT_501_PCI=y

#
# USB-based Watchdog Cards
#
CONFIG_USBPCWATCHDOG=m
CONFIG_HW_RANDOM=m
CONFIG_NVRAM=m
CONFIG_RTC=m
CONFIG_GEN_RTC=m
CONFIG_GEN_RTC_X=y
CONFIG_DTLK=m
CONFIG_R3964=m
CONFIG_APPLICOM=m
CONFIG_SONYPI=m

#
# Ftape, the floppy tape device driver
#
CONFIG_FTAPE=m
CONFIG_ZFTAPE=m
CONFIG_ZFT_DFLT_BLK_SZ=10240

#
# The compressor will be built as a module only!
#
CONFIG_ZFT_COMPRESSOR=m
CONFIG_FT_NR_BUFFERS=3
CONFIG_FT_PROC_FS=y
CONFIG_FT_NORMAL_DEBUG=y
# CONFIG_FT_FULL_DEBUG is not set
# CONFIG_FT_NO_TRACE is not set
# CONFIG_FT_NO_TRACE_AT_ALL is not set

#
# Hardware configuration
#
CONFIG_FT_STD_FDC=y
# CONFIG_FT_MACH2 is not set
# CONFIG_FT_PROBE_FC10 is not set
# CONFIG_FT_ALT_FDC is not set
CONFIG_FT_FDC_THR=8
CONFIG_FT_FDC_MAX_RATE=2000
CONFIG_FT_ALPHA_CLOCK=0
CONFIG_AGP=m
CONFIG_AGP_ALI=m
CONFIG_AGP_ATI=m
CONFIG_AGP_AMD=m
CONFIG_AGP_AMD64=m
CONFIG_AGP_INTEL=m
CONFIG_AGP_NVIDIA=m
CONFIG_AGP_SIS=m
CONFIG_AGP_SWORKS=m
CONFIG_AGP_VIA=m
CONFIG_AGP_EFFICEON=m
CONFIG_DRM=m
CONFIG_DRM_TDFX=m
CONFIG_DRM_R128=m
CONFIG_DRM_RADEON=m
CONFIG_DRM_I810=m
CONFIG_DRM_I830=m
CONFIG_DRM_I915=m
CONFIG_DRM_MGA=m
CONFIG_DRM_SIS=m
CONFIG_DRM_VIA=m
CONFIG_DRM_SAVAGE=m

#
# Graphics support
#
CONFIG_FB=y
CONFIG_FB_CFB_FILLRECT=y
CONFIG_FB_CFB_COPYAREA=y
CONFIG_FB_CFB_IMAGEBLIT=y
# CONFIG_FB_MACMODES is not set
CONFIG_FB_MODE_HELPERS=y
CONFIG_FB_TILEBLITTING=y
CONFIG_FB_CIRRUS=m
CONFIG_FB_PM2=m
CONFIG_FB_PM2_FIFO_DISCONNECT=y
CONFIG_FB_CYBER2000=m
# CONFIG_FB_ARC is not set
# CONFIG_FB_ASILIANT is not set
# CONFIG_FB_IMSTT is not set
CONFIG_FB_VGA16=m
CONFIG_FB_VESA=y
CONFIG_VIDEO_SELECT=y
CONFIG_FB_HGA=m
# CONFIG_FB_HGA_ACCEL is not set
CONFIG_FB_S1D13XXX=m
CONFIG_FB_NVIDIA=m
CONFIG_FB_NVIDIA_I2C=y
CONFIG_FB_RIVA=m
CONFIG_FB_RIVA_I2C=y
# CONFIG_FB_RIVA_DEBUG is not set
CONFIG_FB_I810=m
# CONFIG_FB_I810_GTF is not set
CONFIG_FB_INTEL=m
# CONFIG_FB_INTEL_DEBUG is not set
CONFIG_FB_MATROX=m
CONFIG_FB_MATROX_MILLENIUM=y
CONFIG_FB_MATROX_MYSTIQUE=y
CONFIG_FB_MATROX_G=y
CONFIG_FB_MATROX_I2C=m
CONFIG_FB_MATROX_MAVEN=m
CONFIG_FB_MATROX_MULTIHEAD=y
# CONFIG_FB_RADEON_OLD is not set
CONFIG_FB_RADEON=m
CONFIG_FB_RADEON_I2C=y
# CONFIG_FB_RADEON_DEBUG is not set
CONFIG_FB_ATY128=m
CONFIG_FB_ATY=m
CONFIG_FB_ATY_CT=y
CONFIG_FB_ATY_GENERIC_LCD=y
CONFIG_FB_ATY_GX=y
CONFIG_FB_SAVAGE=m
CONFIG_FB_SAVAGE_I2C=y
CONFIG_FB_SAVAGE_ACCEL=y
CONFIG_FB_SIS=m
CONFIG_FB_SIS_300=y
CONFIG_FB_SIS_315=y
CONFIG_FB_NEOMAGIC=m
CONFIG_FB_KYRO=m
CONFIG_FB_3DFX=m
# CONFIG_FB_3DFX_ACCEL is not set
CONFIG_FB_VOODOO1=m
CONFIG_FB_CYBLA=m
CONFIG_FB_TRIDENT=m
# CONFIG_FB_TRIDENT_ACCEL is not set
CONFIG_FB_GEODE=y
CONFIG_FB_GEODE_GX1=m
# CONFIG_FB_VIRTUAL is not set

#
# Console display driver support
#
CONFIG_VGA_CONSOLE=y
CONFIG_MDA_CONSOLE=m
CONFIG_DUMMY_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE=m
CONFIG_FRAMEBUFFER_CONSOLE_ROTATION=y
# CONFIG_FONTS is not set
CONFIG_FONT_8x8=y
CONFIG_FONT_8x16=y


---

### Post by hannes_ on 2006-06-06
CONFIG_FRAMEBUFFER_CONSOLE=m
CONFIG_FRAMEBUFFER_CONSOLE_ROTATION=y

pls make sure the first entry is "y" not "m"

and give it a try.

greetings

---

### Post by digiplaya on 2006-06-06
Ooh...didn't notice that. Currently re-doing the kernel as you say.
Will let you know how it goes ASAP.

Plus, is there a way to compile the kernel only with changes you just made to it's .config file instead of recompiling the entire thing?
EDIT: Wait, just found out. I didn't use make clean and it started where I left off.

---

### Post by bartman on 2006-06-06
I've downloaded the latest stable kernel source (2.6.16.20). Which patch is the correct one for this version:
- [ck12/patches/patch-2.6.16.20](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/2.6.16-ck12/patches/patch-2.6.16.20)
- [ck3/patch-2.6.16-ck3.bz2](http://ck.kolivas.org/patches/2.6/2.6.16/2.6.16-ck3/patch-2.6.16-ck3.bz2) from the first post

I have a laptop with ati graphics and fglrx drivers. I've read that substituting them with ati in xorg.conf for first boot is a must. Is this also wise to do as it doesn't stand in the first post?

Thanks a bunch!

---

### Post by xXx 0wn3d xXx on 2006-06-06
No if you are not patching the first release (2.6.16, 2.6.17) you will not be able to patch the kernel with a patch from ck.kolivas.org. If you do, you are looking at a kernel that will never compile.

---

### Post by digiplaya on 2006-06-06
Ok: usplash is functional with 2.6.16. I'm all set now! Will keep 2.6.15 branch kernel just in case I need to revert back.

Danke, hannes.

---

### Post by bartman on 2006-06-06
MasterChief, what about the first patch i linked to?

Or should I just forget about the 2.6.16.20 version and go for 2.6.16 with ck patches for speed?

---

### Post by zarathustra on 2006-06-06
Do you not still have to apply the EVMS patch from the Ubuntu repositories, or is this now fixed?

---

### Post by hannes_ on 2006-06-06
you are welcome :)

---

### Post by xXx 0wn3d xXx on 2006-06-06
[QUOTE=bartman]MasterChief, what about the first patch i linked to?

Or should I just forget about the 2.6.16.20 version and go for 2.6.16 with ck patches for speed?[/QUOTE]
I think that you should forget about the patch. I don't use them because I feel that I if I am custom compiling a kernel, I should do it on my own. Your not missing out on much performance gain by patching your kernel. You can get the same performance by choosing certain options in xconfig.

---

### Post by bartman on 2006-06-07
First of all I got the 2.6.16 kernel from [www.kernel.org](www.kernel.org), to the source of which I applied two patchsets:
- patch-2.6.16-ck12.bz2 (speed optimizations)
- linux-phc-0.2.4.tar.gz (undervolting support for Centrino/Sonoma laptops)

I then modified the voltage table of my Pentium M 770 in /usr/src/linux/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.c to stable undervolted values, which I got from my undervolting experience in Windows but the knowledge from [Gentoo forums](http://forums.gentoo.org/viewtopic-t-341298-start-75-postdays-0-postorder-asc-highlight-.html).

After disabling unneeded parts (SCSI, RAID) and enabling VESA VGA support of the kernel I compiled it, which took 22m27.981s ! A 4 minute increase from my previous attempt, but that one didn't boot. :P

So after a reboot the machine booted faster, usplash isn't there, only my wireless card didn't completely work. I noticed that in dmesg there were complaints about missing firmware files so I quickly copied them over to a new folder in /lib/firmware:
```
$ cd /lib/firmware/
$ sudo mkdir `uname -r`
$ sudo cp ./2.6.<version-of-previous-kernel-i-was-using>/ipw2200* ./`uname -r`/
```

After that a simple module removal/insertion:
```
$ sudo modprobe -r ipw2200
$ sudo modprobe ipw2200
```
And to check if the wireless interface started:
```
$ dmesg | grep ipw
```

The device starts, scanning works, however it will not associate with any access point, even though i command it to with
```
$ sudo iwconfig eth0 essid <name> ap <MAC-address>
```

EDIT: Nevermind, it works like a charm.
There is, however, no console output, e.g. when i change to console with ctrl+alt+f8 there is just a blank screen! I didn't notice it before because the new ubuntu splash screen was over it. I thought I had followed the tips from the first page of this thread but apparently I missed some kenrel options. But now at least I know what is wrong! :D


**Thank you MasterChief1234** for this wonderful and easy to follow guide!

---

### Post by talz13 on 2006-06-07
Is this kernel ever going to be included in an update to breezy or are you forced to upgrade to dapper to get an updatable kernel?  (as far as the update manager / synaptic is concerned)

---

### Post by xXx 0wn3d xXx on 2006-06-07
[QUOTE=talz13]Is this kernel ever going to be included in an update to breezy or are you forced to upgrade to dapper to get an updatable kernel?  (as far as the update manager / synaptic is concerned)[/QUOTE]
No, this kernel will never be included in Breezy or Dapper. About halfway through the development process of a new Ubuntu version, a kernel freeze happens. This means that the current kernel will remain the default kernel included and supported by Ubuntu. I believe Breezy uses the 2.6.12 kernel (I think that it is updated due to a security problem) and Dapper uses the 2.6.15 kernel with patches from 2.6.16 (stable) and 2.6.17. (still in development)

---

### Post by massivevoid on 2006-06-07
How do you apply the 2.6.17 patch?

---

### Post by xXx 0wn3d xXx on 2006-06-07
Please note that it is unstable but I have used release canidates and they were fine. Download the 2.6.17-rc6 patch from kernel.org and then follow my tutorial up to the part where you patch the kernel. Change the command to the path of the file.

It would look something like this:
> bzcat /home/$USER/patch-2.6.17-rc6.bz2| patch -p1

---

### Post by OPaul on 2006-06-07
[QUOTE=MasterChief1234].... and Dapper uses the 2.6.15 kernel with patches from 2.6.16 (stable) and 2.6.17. (still in development)[/QUOTE]
How much of .16 is in Dapper? Is there a list of what patches are included?

Also, is a .deb possible to streamline the installation through the Synaptic Package Manager?

---

### Post by massivevoid on 2006-06-07
[QUOTE=MasterChief1234]Please note that it is unstable but I have used release canidates and they were fine. Download the 2.6.17-rc6 patch from kernel.org and then follow my tutorial up to the part where you patch the kernel. Change the command to the path of the file.

It would look something like this:[/QUOTE]

I know. 

Still, I want to try it, because I have a broadcom card in my laptop.

What should I do on this part?

```
william@crafford:~$ bzcat /home/william/patch-2.6.17-rc6.bz2| patch -p1
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/.gitignore b/.gitignore
|index 3f8fb68..27fd376 100644
|--- a/.gitignore
|+++ b/.gitignore
--------------------------
File to patch:

```

---

### Post by xXx 0wn3d xXx on 2006-06-07
[QUOTE=OPaul]How much of .16 is in Dapper? Is there a list of what patches are included?

I really can't say, sorry...

Also, is a .deb possible to streamline the installation through the Synaptic Package Manager?

What exactly do you mean ? Take a new kernel and put it in the repositories or already have a .deb file. This tutorial allows you to build a debian file so you can install it.
[/QUOTE]
I answered in the quotes.

---

### Post by OPaul on 2006-06-07
[QUOTE=MasterChief1234]What exactly do you mean ? Take a new kernel and put it in the repositories or already have a .deb file. This tutorial allows you to build a debian file so you can install it.[/QUOTE]
Put it in the universe repository (sorry, I assumed the repositories were .deb files). I may not understand how the kernel is compiled, so it may just be a stupid question. But whenever a new patch for .15 comes out, it's available in the repositories, so is it possible to have .16 in there?

---

### Post by xXx 0wn3d xXx on 2006-06-07
[QUOTE=OPaul]Put it in the universe repository (sorry, I assumed the repositories were .deb files). I may not understand how the kernel is compiled, so it may just be a stupid question. But whenever a new patch for .25 comes out, it's available in the repositories, so is it possible to have .16 in there?[/QUOTE]
No, there will never be an updated kernel in the repositories unless a major security vulnerability is uncovered or you are dist-upgrading because a new kernel will be in the next Ubuntu release. There are no updated kernels because of the "kernel freeze" as I stated earlier.

---

### Post by OPaul on 2006-06-07
[QUOTE=MasterChief1234]No, there will never be an updated kernel in the repositories unless a major security vulnerability is uncovered or you are dist-upgrading because a new kernel will be in the next Ubuntu release. There are no updated kernels because of the "kernel freeze" as I stated earlier.[/QUOTE]
I guess I thought that's what the Universe repository was for then, unsupported software.

---

### Post by OPaul on 2006-06-07
I'm compiling ck3 now, but does this mean I won't have the latest version. Is ck3 a numbering scheme that is used before real numbers? For instance, on kernel.org the latest version is 2.6.16.20... doesn't say anything about ck anything.

Or is ck something that someone has modified themself?....

---

### Post by keithjr on 2006-06-07
[QUOTE=MasterChief1234]Install fglrx-kernel-source.[/QUOTE]

Thanks for the guide, but once again I find myself to be a cryptic exception to everybody else's experiences...

I'm having the EXACT same problem, after installing and booting into the new 2.6.16 kernel fglrxinfo now tells me I'm using a mesa driver.  I issued the above command and... nothing much happened...  

What is the next step?  I thought I searched high and low xconfig for something that must have installed, but couldn't see it.  Also, would it work if I built it in or should I stick with modular?

---

### Post by Slicedbread on 2006-06-08
Does any one know how I can install the newest linux-headers, they are not available in synaptic.

---

### Post by OPaul on 2006-06-08
[QUOTE=Slicedbread]Does any one know how I can install the newest linux-headers, they are not available in synaptic.[/QUOTE]
I think the headers are included in the /usr/src/linux-whatever_version_you_installed directory, if you followed this guide.

---

### Post by Slicedbread on 2006-06-08
Yeah, I guess it was, but I'm still having problems with ndswrapper-- I can't get to join wpa encrypted lans (mine) but it works with wep and open Wlan's - I reinstalled wpasupplicant throug synaptic but I still cant access it- I could before with the default   dapper kernel.

---

### Post by xXx 0wn3d xXx on 2006-06-08
I have made some changes to the main thread by:

Merging step 1 & 2
Making the last step build a kernel image, modules, and headers
Making the letters of the steps bold
Adding to the troubleshooting guide
Removed custom compilied kernels
Linked to ck12 patch for 2.6.16

What I'm planning to do:
Add more performance tips

Are their any suggestions for the thread to make it easier to read/more useful ?

I have also been thinking of making a kernel install script where you would specify your kernel directory and then it would try to install it, asking you a few questions along the way. Does anyone think it is a good idea and would anyone be interesting in helping. My script skillz are almost nill but you would just need to use the commands listed on the origional post. Thank you.

---

### Post by ehula on 2006-06-08
MasterChief1234,

You need to edit two more items on the front page: steps 5 & 7 should both refer to ck12, not ck3.

Now, when I follow your steps, I get the following results:

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
#
# using defaults found in .config
#
.config:19:warning: trying to assign nonexistent symbol CLEAN_COMPILE

followed by about 150 other "trying to assign nonexistent symbol" lines like the one above. I am running Dapper. Can I ignore these warnings?

---

### Post by xXx 0wn3d xXx on 2006-06-08
[QUOTE=ehula]MasterChief1234,

You need to edit two more items on the front page: steps 5 & 7 should both refer to ck12, not ck3.

Now, when I follow your steps, I get the following results:

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
#
# using defaults found in .config
#
.config:19:warning: trying to assign nonexistent symbol CLEAN_COMPILE

followed by about 150 other "trying to assign nonexistent symbol" lines like the one above. I am running Dapper. Can I ignore these warnings?[/QUOTE]
Thank you for telling me about the steps, and yes, you can ignore those errors.

---

### Post by ehula on 2006-06-08
[QUOTE=MasterChief1234]Thank you for telling me about the steps, and yes, you can ignore those errors.[/QUOTE]

Oh, you will also need to change step 14 from ck3 to ck12.

One more question related to the ubuntu fglrx driver. Do I need to uninstall anything related to the fglrx driver before upgrading the kernel, or change xorg.conf to refer to the "ati" driver?

And, when I install the fglrx-kernel-source, can I uninstall all the other fglrx packages first, or are they still needed?

---

### Post by xXx 0wn3d xXx on 2006-06-08
[QUOTE=ehula]Oh, you will also need to change step 14 from ck3 to ck12.

One more question related to the ubuntu fglrx driver. Do I need to uninstall anything related to the fglrx driver before upgrading the kernel, or change xorg.conf to refer to the "ati" driver?

And, when I install the fglrx-kernel-source, can I uninstall all the other fglrx packages first, or are they still needed?[/QUOTE]
No, you do not need to uninstall anything. Just make sure it says fglrx in your xorg.conf. I wouldn't recommend uninstalling the other fglrx packages though.

---

### Post by OPaul on 2006-06-08
[QUOTE=OPaul]I'm compiling ck3 now, but does this mean I won't have the latest version. Is ck3 a numbering scheme that is used before real numbers? For instance, on kernel.org the latest version is 2.6.16.20... doesn't say anything about ck anything.

Or is ck something that someone has modified themself?....[/QUOTE]
?

---

### Post by xXx 0wn3d xXx on 2006-06-08
No, ck's refer to performance enhancing kernel patches. So yes, ck patches are modification patches that are applied to the kernel.

---

### Post by OPaul on 2006-06-08
[QUOTE=MasterChief1234]No, ck's refer to performance enhancing kernel patches. So yes, ck patches are modification patches that are applied to the kernel.[/QUOTE]
So instead of taking the 2.6.16 from the link you provided, could I take the 2.6.16.20 from kernel.org and then apply the latest ck patch to that? 

Do the ck patches have a homepage that lists some of the performance changes that have been made?

---

### Post by xXx 0wn3d xXx on 2006-06-08
[QUOTE=OPaul]So instead of taking the 2.6.16 from the link you provided, could I take the 2.6.16.20 from kernel.org and then apply the latest ck patch to that? 

Do the ck patches have a homepage that lists some of the performance changes that have been made?[/QUOTE]
No you can only apply the patch to the first kernel of the release cycle (ex: 2.6.16, or 2.6.17) NOT 2.6.16.20. And yes, you can look at the changes in the ck1-12 folder [ here. ](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16) Browse to a ck patch folder and look at the changes. I personally don't use the patches but for anyone learning to build a kernel, it is worth it.

---

### Post by OPaul on 2006-06-08
[QUOTE=MasterChief1234]No you can only apply the patch to the first kernel of the release cycle (ex: 2.6.16, or 2.6.17) NOT 2.6.16.20. And yes, you can look at the changes in the ck1-12 folder [ here. ](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16) Browse to a ck patch folder and look at the changes. I personally don't use the patches but for anyone learning to build a kernel, it is worth it.[/QUOTE]
Ah, ck12 includes the patches from 2.6.16.20. 
[http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)

Cool, thanks.

---

### Post by ehula on 2006-06-09
[QUOTE=MasterChief1234]No, you do not need to uninstall anything. Just make sure it says fglrx in your xorg.conf. I wouldn't recommend uninstalling the other fglrx packages though.[/QUOTE]
OK. After compiling, I have three new .debs:
  kernel-image
  kernel-headers
  fglrx-kernel

Which do I install? Do I install the fglrx-kernel? Remember, I had previously installed the ubuntu fglrx packages: linux-restricted-modules and xorg-driver-fglrx. I have still not yet installed fglrx-kernel-source.

---

### Post by xXx 0wn3d xXx on 2006-06-09
[QUOTE=ehula]OK. After compiling, I have three new .debs:
  kernel-image
  kernel-headers
  fglrx-kernel

Which do I install? Do I install the fglrx-kernel? Remember, I had previously installed the ubuntu fglrx packages: linux-restricted-modules and xorg-driver-fglrx. I have still not yet installed fglrx-kernel-source.[/QUOTE]
You would install your kernel_image first, then your kernel-headers, and finally fglrx-kernel.

---

### Post by ehula on 2006-06-09
[QUOTE=MasterChief1234]You would install your kernel_image first, then your kernel-headers, and finally fglrx-kernel.[/QUOTE]
I'm not completely sure I understand how to set up the fglrx driver to work under the new kernel. So far, I have followed what you have said...left the restricted modules and the xorg-driver-fglrx as is from the original Dapper install. I have compiled the kernel and installed kernel-image and kernel-headers, but when I try to install fglrx-kernel, this is what I get:

$ sudo dpkg -i fglrx-kernel-2.6.16-ck12_8.25.18-1+ck12_i386.deb
(Reading database ... 173821 files and directories currently installed.)
Preparing to replace fglrx-kernel-2.6.16-ck12 8.25.18-1+ck12 (using fglrx-kernel-2.6.16-ck12_8.25.18-1+ck12_i386.deb) ...
Unpacking replacement fglrx-kernel-2.6.16-ck12 ...
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.16-ck12:
 fglrx-kernel-2.6.16-ck12 depends on xorg-driver-fglrx (= 8.25.18-1); however:
  Version of xorg-driver-fglrx on system is 7.0.0-8.25.18+2.6.15.11-1.
dpkg: error processing fglrx-kernel-2.6.16-ck12 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-kernel-2.6.16-ck12

---

### Post by xXx 0wn3d xXx on 2006-06-09
[QUOTE=ehula]I'm not completely sure I understand how to set up the fglrx driver to work under the new kernel. So far, I have followed what you have said...left the restricted modules and the xorg-driver-fglrx as is from the original Dapper install. I have compiled the kernel and installed kernel-image and kernel-headers, but when I try to install fglrx-kernel, this is what I get:

$ sudo dpkg -i fglrx-kernel-2.6.16-ck12_8.25.18-1+ck12_i386.deb
(Reading database ... 173821 files and directories currently installed.)
Preparing to replace fglrx-kernel-2.6.16-ck12 8.25.18-1+ck12 (using fglrx-kernel-2.6.16-ck12_8.25.18-1+ck12_i386.deb) ...
Unpacking replacement fglrx-kernel-2.6.16-ck12 ...
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.16-ck12:
 fglrx-kernel-2.6.16-ck12 depends on xorg-driver-fglrx (= 8.25.18-1); however:
  Version of xorg-driver-fglrx on system is 7.0.0-8.25.18+2.6.15.11-1.
dpkg: error processing fglrx-kernel-2.6.16-ck12 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-kernel-2.6.16-ck12[/QUOTE]
That's strange...could you just install your kernel image + the headers and then install fglrx-kernel-source and see if fglrx works ? It might work after just installing the fglrx source. 

Sorry, to bring up the script idea but who thinks it is a good idea ? And does anyone have a suggestion on how to make the origional post easier to read or follow ? Thanks.

---

### Post by bignickel on 2006-06-09
[QUOTE=garijon]When I try to manually mount the second one, I get a message saying that it is either mounted or busy. If I try to unmount it, it says it was not mounted at all. [/QUOTE]

I ran into the same problem, and if I made a small change to my fstab to make it work.  Instead of (for example):
/dev/hdb1
use
/dev/evms/hdb1

I think that should take care of it.

---

### Post by 23meg on 2006-06-09
I compiled 2.6.16.20 from kernel org and lost the ability to mount CDs with the SATA CD drive of my laptop.  I get the following error when trying to mount:

```
mount: special device /dev/scd1 does not exist
```

---

### Post by keithjr on 2006-06-10
[QUOTE=xXx 0wn3d xXx]That's strange...could you just install your kernel image + the headers and then install fglrx-kernel-source and see if fglrx works ? It might work after just installing the fglrx source. 

Sorry, to bring up the script idea but who thinks it is a good idea ? And does anyone have a suggestion on how to make the origional post easier to read or follow ? Thanks.[/QUOTE]


I just solved it for myself, I don't know if I was having the same issues though... I explicitly removed the packages I had used to install fglrx the first time around (before the upgrade), then re-installed them.  Of course, the linux-restricted-modules has to be replaced with the fglrx kernel source you provided... but I think that's the issue people are running into: unclean installation

---

### Post by ravpaul on 2006-06-10
Still trying to compile the kernel and still getting the same output when applying the patch.
```
patching file include/linux/sched.h
patching file kernel/sched.c
patching file fs/proc/array.c
patching file include/linux/sysctl.h
patching file kernel/exit.c
patching file kernel/sysctl.c
patching file include/linux/init_task.h
patching file block/Kconfig.iosched
patching file include/linux/ioprio.h
patching file mm/page-writeback.c
patching file arch/ia64/configs/tiger_defconfig
patching file arch/ia64/configs/zx1_defconfig
patching file arch/ppc/configs/common_defconfig
patching file arch/ppc/configs/pmac_defconfig
patching file kernel/Kconfig.hz
patching file Documentation/sysctl/vm.txt
patching file include/linux/swap.h
patching file init/Kconfig
patching file mm/Makefile
patching file mm/swap.c
patching file mm/swap_prefetch.c
patching file mm/swap_state.c
patching file mm/vmscan.c
patching file include/linux/mm_inline.h
patching file include/linux/swap-prefetch.h
patching file include/linux/mmzone.h
patching file mm/page_alloc.c
patching file fs/buffer.c
patching file kernel/power/disk.c
patching file drivers/block/loop.c
patching file fs/mpage.c
patching file fs/nfsd/vfs.c
patching file include/linux/fs.h
patching file include/linux/mm.h
patching file include/linux/page-flags.h
patching file include/linux/radix-tree.h
patching file include/linux/writeback.h
patching file lib/radix-tree.c
patching file mm/Kconfig
patching file mm/filemap.c
patching file mm/memory.c
patching file mm/readahead.c
patching file Documentation/DocBook/Makefile
patching file Makefile
patching file arch/arm/Makefile
patching file arch/arm/boot/Makefile
patching file arch/arm/boot/bootp/Makefile
patching file arch/arm26/Makefile
patching file arch/arm26/boot/Makefile
patching file arch/i386/Makefile
patching file arch/ia64/Makefile
patching file arch/m32r/Makefile
patching file arch/powerpc/Makefile
patching file arch/ppc/Makefile
patching file arch/ppc/boot/Makefile
patching file arch/ppc/boot/openfirmware/Makefile
patching file arch/sh/Makefile
patching file arch/um/Makefile
patching file arch/x86_64/Makefile
patching file scripts/Kbuild.include
patching file scripts/Makefile.build
patching file scripts/Makefile.clean
patching file scripts/Makefile.modinst
patching file scripts/Makefile.modpost
patching file scripts/kconfig/Makefile
patching file scripts/kconfig/lxdialog/Makefile
patching file scripts/package/Makefile
Hunk #1 FAILED at 32.
Hunk #2 FAILED at 54.
Hunk #3 FAILED at 72.
Hunk #4 FAILED at 82.
4 out of 4 hunks FAILED -- saving rejects to file scripts/package/Makefile.rej
patching file arch/i386/kernel/cpu/cpufreq/speedstep-smi.c
patching file arch/i386/kernel/dmi_scan.c
patching file drivers/base/cpu.c
patching file drivers/base/firmware_class.c
patching file drivers/block/cciss.c
patching file drivers/md/dm.c
patching file drivers/media/video/Kconfig
patching file drivers/media/video/tuner-types.c
patching file drivers/scsi/sata_mv.c
patching file drivers/video/i810/i810_main.c
patching file fs/9p/vfs_inode.c
patching file fs/proc/proc_misc.c
patching file fs/sysfs/dir.c
patching file fs/sysfs/inode.c
patching file fs/sysfs/symlink.c
patching file fs/xfs/linux-2.6/xfs_aops.c
patching file include/linux/cpu.h
patching file include/linux/raid/raid1.h
patching file include/linux/rtc.h
patching file net/core/sock.c
patching file net/ipv4/ip_output.c
root@bedroom:/usr/src/linux# uname -r
2.6.15-23-amd64-generic
root@bedroom:/usr/src/linux# sudo cp /boot/config-2.6.15-23-amd64-generic .config
root@bedroom:/usr/src/linux# sudo make xconfig
CHECK qt
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
HOSTCC scripts/kconfig/kconfig_load.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
HOSTCXX scripts/kconfig/qconf.o
HOSTLD scripts/kconfig/qconf
scripts/kconfig/qconf arch/x86_64/Kconfig
X Error: BadDevice, invalid or uninitialized input device 166
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
#
# using defaults found in .config
#
.config:23:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:43:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:101:warning: trying to assign nonexistent symbol X86_64_NOLONG_MSG
.config:115:warning: trying to assign nonexistent symbol ENABLE_ALT_SMP
.config:178:warning: trying to assign nonexistent symbol ACPI_SBS
.config:190:warning: trying to assign nonexistent symbol ACPI_PCC
.config:191:warning: trying to assign nonexistent symbol ACPI_SONY
.config:198:warning: trying to assign nonexistent symbol ACPI_TC1100
.config:199:warning: trying to assign nonexistent symbol ACPI_INITRD
.config:200:warning: trying to assign nonexistent symbol ACPI_DEV
.config:263:warning: trying to assign nonexistent symbol PCMCIA_PROBE_MEM
.config:405:warning: trying to assign nonexistent symbol IP_NF_MATCH_LIMIT
.config:407:warning: trying to assign nonexistent symbol IP_NF_MATCH_MAC
.config:408:warning: trying to assign nonexistent symbol IP_NF_MATCH_PKTTYPE
.config:409:warning: trying to assign nonexistent symbol IP_NF_MATCH_MARK
.config:416:warning: trying to assign nonexistent symbol IP_NF_MATCH_LENGTH
.config:418:warning: trying to assign nonexistent symbol IP_NF_MATCH_TCPMSS
.config:419:warning: trying to assign nonexistent symbol IP_NF_MATCH_HELPER
.config:420:warning: trying to assign nonexistent symbol IP_NF_MATCH_STATE
.config:421:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNTRACK
.config:423:warning: trying to assign nonexistent symbol IP_NF_MATCH_PHYSDEV
.config:425:warning: trying to assign nonexistent symbol IP_NF_MATCH_REALM
.config:426:warning: trying to assign nonexistent symbol IP_NF_MATCH_SCTP
.config:427:warning: trying to assign nonexistent symbol IP_NF_MATCH_DCCP
.config:428:warning: trying to assign nonexistent symbol IP_NF_MATCH_COMMENT
.config:429:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNMARK
.config:430:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNBYTES
.config:432:warning: trying to assign nonexistent symbol IP_NF_MATCH_STRING
.config:438:warning: trying to assign nonexistent symbol IP_NF_TARGET_NFQUEUE
.config:455:warning: trying to assign nonexistent symbol IP_NF_TARGET_MARK
.config:456:warning: trying to assign nonexistent symbol IP_NF_TARGET_CLASSIFY
.config:458:warning: trying to assign nonexistent symbol IP_NF_TARGET_CONNMARK
.config:461:warning: trying to assign nonexistent symbol IP_NF_TARGET_NOTRACK
.config:471:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LIMIT
.config:472:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MAC
.config:479:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MARK
.config:482:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LENGTH
.config:484:warning: trying to assign nonexistent symbol IP6_NF_MATCH_PHYSDEV
.config:488:warning: trying to assign nonexistent symbol IP6_NF_TARGET_NFQUEUE
.config:490:warning: trying to assign nonexistent symbol IP6_NF_TARGET_MARK
.config:746:warning: trying to assign nonexistent symbol IEEE80211_SOFTMAC
.config:747:warning: trying to assign nonexistent symbol IEEE80211_SOFTMAC_DEBUG.config:748:warning: trying to assign nonexistent symbol IEEE80211_1_1_13
.config:749:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_WEP
.config:750:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_CCMP
.config:751:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_TKIP
.config:956:warning: trying to assign nonexistent symbol BLK_DEV_CLOOP
.config:967:warning: trying to assign nonexistent symbol BLK_DEV_GNBD
.config:988:warning: trying to assign nonexistent symbol BLK_DEV_IDEACPI
.config:997:warning: symbol value 'm' invalid for BLK_DEV_IDEPNP
.config:1028:warning: trying to assign nonexistent symbol PDC202XX_FORCE
.config:1070:warning: trying to assign nonexistent symbol SCSI_SPI2_ATTRS
.config:1078:warning: trying to assign nonexistent symbol SAS_CLASS
.config:1079:warning: trying to assign nonexistent symbol SAS_DEBUG
.config:1089:warning: trying to assign nonexistent symbol SCSI_AIC94XX
.config:1090:warning: trying to assign nonexistent symbol AIC94XX_DEBUG
.config:1106:warning: trying to assign nonexistent symbol SCSI_ARCMSR
.config:1128:warning: trying to assign nonexistent symbol SCSI_SATA_ACPI
.config:1150:warning: trying to assign nonexistent symbol SCSI_SYM53C8XX_MMIO
.config:1157:warning: trying to assign nonexistent symbol SCSI_QLA2XXX
.config:1237:warning: trying to assign nonexistent symbol IEEE1394_CMP
.config:1348:warning: trying to assign nonexistent symbol R1000
.config:1371:warning: trying to assign nonexistent symbol NET_IPG
.config:1414:warning: trying to assign nonexistent symbol IPW2100_FS_AMILO_M7400.config:1417:warning: trying to assign nonexistent symbol IPW2200_MONITOR
.config:1436:warning: trying to assign nonexistent symbol ADM8211
.config:1447:warning: trying to assign nonexistent symbol WLAN_NG
.config:1448:warning: trying to assign nonexistent symbol PRISM2
.config:1449:warning: trying to assign nonexistent symbol PRISM2_USB
.config:1450:warning: trying to assign nonexistent symbol PRISM2_PCI
.config:1451:warning: trying to assign nonexistent symbol PRISM2_PLX
.config:1452:warning: trying to assign nonexistent symbol PRISM2_CS
.config:1453:warning: trying to assign nonexistent symbol NET_ACX
.config:1454:warning: trying to assign nonexistent symbol NET_ACX_PCI
.config:1455:warning: trying to assign nonexistent symbol NET_ACX_USB
.config:1456:warning: trying to assign nonexistent symbol BCM43XX
.config:1457:warning: trying to assign nonexistent symbol BCM43XX_DEBUG
.config:1458:warning: trying to assign nonexistent symbol BCM43XX_DMA
.config:1459:warning: trying to assign nonexistent symbol BCM43XX_PIO
.config:1460:warning: trying to assign nonexistent symbol BCM43XX_DMA_AND_PIO_MODE
.config:1461:warning: trying to assign nonexistent symbol BCM43XX_DMA_MODE
.config:1462:warning: trying to assign nonexistent symbol BCM43XX_PIO_MODE
.config:1463:warning: trying to assign nonexistent symbol PRISM54_SOFTMAC
.config:1464:warning: trying to assign nonexistent symbol NET_RT2600
.config:1465:warning: trying to assign nonexistent symbol NET_RT2500
.config:1466:warning: trying to assign nonexistent symbol NET_RT2400
.config:1467:warning: trying to assign nonexistent symbol NET_RTL818X
.config:1468:warning: trying to assign nonexistent symbol NET_RTL8187
.config:1469:warning: trying to assign nonexistent symbol IPW3945
.config:1470:warning: trying to assign nonexistent symbol IPW3945_DEBUG
.config:1471:warning: trying to assign nonexistent symbol IPW3945_MONITOR
.config:1472:warning: trying to assign nonexistent symbol NET_MRV8K
.config:1575:warning: trying to assign nonexistent symbol NDISWRAPPER
.config:1712:warning: trying to assign nonexistent symbol MISDN_DRV
.config:1713:warning: trying to assign nonexistent symbol MISDN_MEMDEBUG
.config:1714:warning: trying to assign nonexistent symbol MISDN_AVM_FRITZ
.config:1715:warning: trying to assign nonexistent symbol MISDN_HFCPCI
.config:1716:warning: trying to assign nonexistent symbol MISDN_HFCMULTI
.config:1717:warning: trying to assign nonexistent symbol MISDN_HFCUSB
.config:1718:warning: trying to assign nonexistent symbol MISDN_SPEEDFAX
.config:1719:warning: trying to assign nonexistent symbol MISDN_W6692
.config:1720:warning: trying to assign nonexistent symbol MISDN_DSP
.config:1794:warning: trying to assign nonexistent symbol INPUT_ACERHK
.config:1819:warning: trying to assign nonexistent symbol ECC
.config:2109:warning: trying to assign nonexistent symbol AVERATEC_5100P
.config:2110:warning: trying to assign nonexistent symbol PACKARDBELL_E5
.config:2245:warning: trying to assign nonexistent symbol DVB_TDA80XX
.config:2267:warning: trying to assign nonexistent symbol DVB_ATMEL_AT76C651
.config:2275:warning: trying to assign nonexistent symbol DVB_NXT2002
.config:2288:warning: trying to assign nonexistent symbol DXR3
.config:2289:warning: trying to assign nonexistent symbol EM8300
.config:2290:warning: trying to assign nonexistent symbol EM8300_LOOPBACK
.config:2291:warning: trying to assign nonexistent symbol EM8300_UCODETIMEOUT
.config:2292:warning: trying to assign nonexistent symbol EM8300_DICOMFIX
.config:2293:warning: trying to assign nonexistent symbol EM8300_DICOMCTRL
.config:2294:warning: trying to assign nonexistent symbol EM8300_DICOMPAL
.config:2295:warning: trying to assign nonexistent symbol ADV717X
.config:2296:warning: trying to assign nonexistent symbol ADV717X_SWAP
.config:2297:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT16BIT.config:2298:warning: trying to assign nonexistent symbol ADV717X_PIXELPORTPAL
.config:2299:warning: trying to assign nonexistent symbol BT865
.config:2325:warning: symbol value 'm' invalid for FB_VESA
.config:2350:warning: trying to assign nonexistent symbol FB_ATY_XL_INIT
.config:2369:warning: trying to assign nonexistent symbol FB_IMAC
.config:2418:warning: trying to assign nonexistent symbol SND_GENERIC_DRIVER
.config:2495:warning: trying to assign nonexistent symbol BT_ALSA
.config:2618:warning: trying to assign nonexistent symbol USB_SYNAPTICS
.config:2619:warning: trying to assign nonexistent symbol USB_CPADDEV
.config:2640:warning: trying to assign nonexistent symbol USB_QC
.config:2641:warning: trying to assign nonexistent symbol USB_SPCA5XX
.config:2642:warning: trying to assign nonexistent symbol USB_PODXTPRO
.config:2644:warning: trying to assign nonexistent symbol USB_OV511_DECOMP
.config:2645:warning: trying to assign nonexistent symbol USB_OV518_DECOMP
.config:2669:warning: trying to assign nonexistent symbol USB_EAGLE
.config:2670:warning: trying to assign nonexistent symbol USB_ZD1211
.config:2671:warning: trying to assign nonexistent symbol USB_ATMEL
.config:2672:warning: trying to assign nonexistent symbol USB_RT2570
.config:2783:warning: trying to assign nonexistent symbol MMC_SDHCI
.config:2896:warning: trying to assign nonexistent symbol ASFS_FS
.config:2897:warning: trying to assign nonexistent symbol ASFS_DEFAULT_CODEPAGE
.config:2898:warning: trying to assign nonexistent symbol ASFS_RW
.config:2917:warning: trying to assign nonexistent symbol SQUASHFS
.config:2918:warning: trying to assign nonexistent symbol SQUASHFS_1_0_COMPATIBILITY
.config:2919:warning: trying to assign nonexistent symbol SQUASHFS_2_0_COMPATIBILITY
.config:2927:warning: trying to assign nonexistent symbol UNION_FS
.config:2974:warning: trying to assign nonexistent symbol GFS_FS
.config:2975:warning: trying to assign nonexistent symbol GFS_FS_LOCK_HARNESS
.config:2976:warning: trying to assign nonexistent symbol GFS_FS_LOCK_NOLOCK
.config:2977:warning: trying to assign nonexistent symbol GFS_FS_LOCK_DLM
.config:2978:warning: trying to assign nonexistent symbol GFS_FS_LOCK_GULM
.config:3077:warning: trying to assign nonexistent symbol INIT_DEBUG
.config:3089:warning: trying to assign nonexistent symbol SECURITY_REALTIME
.config:3152:warning: trying to assign nonexistent symbol CLUSTER
```

I'm copying and pasting the instructions but still get the same results!!!

Is there a particular directory that I run the patch from or a file that I run it on?

---

### Post by neoaddict on 2006-06-10
Is there an speed improvement for the 2.6.16ck12 kernel over the built-in kernel for Dapper?

---

### Post by Mourner on 2006-06-11
Thank you for such a comprehensive guide, **xXx 0wn3d xXx**, I wouldn't cope with compiling and deploying a customized kernel without it. 

I have a question though. According to the guide, the default Dapper kernel configuration is imported before any changes. So, if I haven't touched any graphic and console devices settings in xconfig at all, why does the new kernel behave so differently (in my case, framebuffer for usplash is not working - I have a blank screen instead of it while loading)?

Thanks in advance.

---

### Post by ravpaul on 2006-06-11
Actaully I just noticed that my compile may be failing at make xconfig as there are many errors occurring.

```

 HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  CHECK   qt
  HOSTCC  scripts/kconfig/conf.o
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/x86_64/Kconfig
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
#
# using defaults found in .config
#
.config:23:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:43:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:101:warning: trying to assign nonexistent symbol X86_64_NOLONG_MSG
.config:115:warning: trying to assign nonexistent symbol ENABLE_ALT_SMP
.config:178:warning: trying to assign nonexistent symbol ACPI_SBS
.config:190:warning: trying to assign nonexistent symbol ACPI_PCC
.config:191:warning: trying to assign nonexistent symbol ACPI_SONY
.config:198:warning: trying to assign nonexistent symbol ACPI_TC1100
.config:199:warning: trying to assign nonexistent symbol ACPI_INITRD
.config:200:warning: trying to assign nonexistent symbol ACPI_DEV
.config:263:warning: trying to assign nonexistent symbol PCMCIA_PROBE_MEM
.config:405:warning: trying to assign nonexistent symbol IP_NF_MATCH_LIMIT
.config:407:warning: trying to assign nonexistent symbol IP_NF_MATCH_MAC
.config:408:warning: trying to assign nonexistent symbol IP_NF_MATCH_PKTTYPE
.config:409:warning: trying to assign nonexistent symbol IP_NF_MATCH_MARK
.config:416:warning: trying to assign nonexistent symbol IP_NF_MATCH_LENGTH
.config:418:warning: trying to assign nonexistent symbol IP_NF_MATCH_TCPMSS
.config:419:warning: trying to assign nonexistent symbol IP_NF_MATCH_HELPER
.config:420:warning: trying to assign nonexistent symbol IP_NF_MATCH_STATE
.config:421:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNTRACK
.config:423:warning: trying to assign nonexistent symbol IP_NF_MATCH_PHYSDEV
.config:425:warning: trying to assign nonexistent symbol IP_NF_MATCH_REALM
.config:426:warning: trying to assign nonexistent symbol IP_NF_MATCH_SCTP
.config:427:warning: trying to assign nonexistent symbol IP_NF_MATCH_DCCP
.config:428:warning: trying to assign nonexistent symbol IP_NF_MATCH_COMMENT
.config:429:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNMARK
.config:430:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNBYTES
.config:432:warning: trying to assign nonexistent symbol IP_NF_MATCH_STRING
.config:438:warning: trying to assign nonexistent symbol IP_NF_TARGET_NFQUEUE
.config:455:warning: trying to assign nonexistent symbol IP_NF_TARGET_MARK
.config:456:warning: trying to assign nonexistent symbol IP_NF_TARGET_CLASSIFY
.config:458:warning: trying to assign nonexistent symbol IP_NF_TARGET_CONNMARK
.config:461:warning: trying to assign nonexistent symbol IP_NF_TARGET_NOTRACK
.config:471:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LIMIT
.config:472:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MAC
.config:479:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MARK
.config:482:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LENGTH
.config:484:warning: trying to assign nonexistent symbol IP6_NF_MATCH_PHYSDEV
.config:488:warning: trying to assign nonexistent symbol IP6_NF_TARGET_NFQUEUE
.config:490:warning: trying to assign nonexistent symbol IP6_NF_TARGET_MARK
.config:746:warning: trying to assign nonexistent symbol IEEE80211_SOFTMAC
.config:747:warning: trying to assign nonexistent symbol IEEE80211_SOFTMAC_DEBUG.config:748:warning: trying to assign nonexistent symbol IEEE80211_1_1_13
.config:749:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_WEP
.config:750:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_CCMP
.config:751:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_TKIP
.config:956:warning: trying to assign nonexistent symbol BLK_DEV_CLOOP
.config:967:warning: trying to assign nonexistent symbol BLK_DEV_GNBD
.config:988:warning: trying to assign nonexistent symbol BLK_DEV_IDEACPI
.config:997:warning: symbol value 'm' invalid for BLK_DEV_IDEPNP
.config:1028:warning: trying to assign nonexistent symbol PDC202XX_FORCE
.config:1070:warning: trying to assign nonexistent symbol SCSI_SPI2_ATTRS
.config:1078:warning: trying to assign nonexistent symbol SAS_CLASS
.config:1079:warning: trying to assign nonexistent symbol SAS_DEBUG
.config:1089:warning: trying to assign nonexistent symbol SCSI_AIC94XX
.config:1090:warning: trying to assign nonexistent symbol AIC94XX_DEBUG
.config:1106:warning: trying to assign nonexistent symbol SCSI_ARCMSR
.config:1128:warning: trying to assign nonexistent symbol SCSI_SATA_ACPI
.config:1150:warning: trying to assign nonexistent symbol SCSI_SYM53C8XX_MMIO
.config:1157:warning: trying to assign nonexistent symbol SCSI_QLA2XXX
.config:1237:warning: trying to assign nonexistent symbol IEEE1394_CMP
.config:1348:warning: trying to assign nonexistent symbol R1000
.config:1371:warning: trying to assign nonexistent symbol NET_IPG
.config:1414:warning: trying to assign nonexistent symbol IPW2100_FS_AMILO_M7400.config:1417:warning: trying to assign nonexistent symbol IPW2200_MONITOR
.config:1436:warning: trying to assign nonexistent symbol ADM8211
.config:1447:warning: trying to assign nonexistent symbol WLAN_NG
.config:1448:warning: trying to assign nonexistent symbol PRISM2
.config:1449:warning: trying to assign nonexistent symbol PRISM2_USB
.config:1450:warning: trying to assign nonexistent symbol PRISM2_PCI
.config:1451:warning: trying to assign nonexistent symbol PRISM2_PLX
.config:1452:warning: trying to assign nonexistent symbol PRISM2_CS
.config:1453:warning: trying to assign nonexistent symbol NET_ACX
.config:1454:warning: trying to assign nonexistent symbol NET_ACX_PCI
.config:1455:warning: trying to assign nonexistent symbol NET_ACX_USB
.config:1456:warning: trying to assign nonexistent symbol BCM43XX
.config:1457:warning: trying to assign nonexistent symbol BCM43XX_DEBUG
.config:1458:warning: trying to assign nonexistent symbol BCM43XX_DMA
.config:1459:warning: trying to assign nonexistent symbol BCM43XX_PIO
.config:1460:warning: trying to assign nonexistent symbol BCM43XX_DMA_AND_PIO_MODE
.config:1461:warning: trying to assign nonexistent symbol BCM43XX_DMA_MODE
.config:1462:warning: trying to assign nonexistent symbol BCM43XX_PIO_MODE
.config:1463:warning: trying to assign nonexistent symbol PRISM54_SOFTMAC
.config:1464:warning: trying to assign nonexistent symbol NET_RT2600
.config:1465:warning: trying to assign nonexistent symbol NET_RT2500
.config:1466:warning: trying to assign nonexistent symbol NET_RT2400
.config:1467:warning: trying to assign nonexistent symbol NET_RTL818X
.config:1468:warning: trying to assign nonexistent symbol NET_RTL8187
.config:1469:warning: trying to assign nonexistent symbol IPW3945
.config:1470:warning: trying to assign nonexistent symbol IPW3945_DEBUG
.config:1471:warning: trying to assign nonexistent symbol IPW3945_MONITOR
.config:1472:warning: trying to assign nonexistent symbol NET_MRV8K
.config:1575:warning: trying to assign nonexistent symbol NDISWRAPPER
.config:1712:warning: trying to assign nonexistent symbol MISDN_DRV
.config:1713:warning: trying to assign nonexistent symbol MISDN_MEMDEBUG
.config:1714:warning: trying to assign nonexistent symbol MISDN_AVM_FRITZ
.config:1715:warning: trying to assign nonexistent symbol MISDN_HFCPCI
.config:1716:warning: trying to assign nonexistent symbol MISDN_HFCMULTI
.config:1717:warning: trying to assign nonexistent symbol MISDN_HFCUSB
.config:1718:warning: trying to assign nonexistent symbol MISDN_SPEEDFAX
.config:1719:warning: trying to assign nonexistent symbol MISDN_W6692
.config:1720:warning: trying to assign nonexistent symbol MISDN_DSP
.config:1794:warning: trying to assign nonexistent symbol INPUT_ACERHK
.config:1819:warning: trying to assign nonexistent symbol ECC
.config:2109:warning: trying to assign nonexistent symbol AVERATEC_5100P
.config:2110:warning: trying to assign nonexistent symbol PACKARDBELL_E5
.config:2245:warning: trying to assign nonexistent symbol DVB_TDA80XX
.config:2267:warning: trying to assign nonexistent symbol DVB_ATMEL_AT76C651
.config:2275:warning: trying to assign nonexistent symbol DVB_NXT2002
.config:2288:warning: trying to assign nonexistent symbol DXR3
.config:2289:warning: trying to assign nonexistent symbol EM8300
.config:2290:warning: trying to assign nonexistent symbol EM8300_LOOPBACK
.config:2291:warning: trying to assign nonexistent symbol EM8300_UCODETIMEOUT
.config:2292:warning: trying to assign nonexistent symbol EM8300_DICOMFIX
.config:2293:warning: trying to assign nonexistent symbol EM8300_DICOMCTRL
.config:2294:warning: trying to assign nonexistent symbol EM8300_DICOMPAL
.config:2295:warning: trying to assign nonexistent symbol ADV717X
.config:2296:warning: trying to assign nonexistent symbol ADV717X_SWAP
.config:2297:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT16BIT.config:2298:warning: trying to assign nonexistent symbol ADV717X_PIXELPORTPAL
.config:2299:warning: trying to assign nonexistent symbol BT865
.config:2325:warning: symbol value 'm' invalid for FB_VESA
.config:2350:warning: trying to assign nonexistent symbol FB_ATY_XL_INIT
.config:2369:warning: trying to assign nonexistent symbol FB_IMAC
.config:2418:warning: trying to assign nonexistent symbol SND_GENERIC_DRIVER
.config:2495:warning: trying to assign nonexistent symbol BT_ALSA
.config:2618:warning: trying to assign nonexistent symbol USB_SYNAPTICS
.config:2619:warning: trying to assign nonexistent symbol USB_CPADDEV
.config:2640:warning: trying to assign nonexistent symbol USB_QC
.config:2641:warning: trying to assign nonexistent symbol USB_SPCA5XX
.config:2642:warning: trying to assign nonexistent symbol USB_PODXTPRO
.config:2644:warning: trying to assign nonexistent symbol USB_OV511_DECOMP
.config:2645:warning: trying to assign nonexistent symbol USB_OV518_DECOMP
.config:2669:warning: trying to assign nonexistent symbol USB_EAGLE
.config:2670:warning: trying to assign nonexistent symbol USB_ZD1211
.config:2671:warning: trying to assign nonexistent symbol USB_ATMEL
.config:2672:warning: trying to assign nonexistent symbol USB_RT2570
.config:2783:warning: trying to assign nonexistent symbol MMC_SDHCI
.config:2896:warning: trying to assign nonexistent symbol ASFS_FS
.config:2897:warning: trying to assign nonexistent symbol ASFS_DEFAULT_CODEPAGE
.config:2898:warning: trying to assign nonexistent symbol ASFS_RW
.config:2917:warning: trying to assign nonexistent symbol SQUASHFS
.config:2918:warning: trying to assign nonexistent symbol SQUASHFS_1_0_COMPATIBILITY
.config:2919:warning: trying to assign nonexistent symbol SQUASHFS_2_0_COMPATIBILITY
.config:2927:warning: trying to assign nonexistent symbol UNION_FS
.config:2974:warning: trying to assign nonexistent symbol GFS_FS
.config:2975:warning: trying to assign nonexistent symbol GFS_FS_LOCK_HARNESS
.config:2976:warning: trying to assign nonexistent symbol GFS_FS_LOCK_NOLOCK
.config:2977:warning: trying to assign nonexistent symbol GFS_FS_LOCK_DLM
.config:2978:warning: trying to assign nonexistent symbol GFS_FS_LOCK_GULM
.config:3077:warning: trying to assign nonexistent symbol INIT_DEBUG
.config:3089:warning: trying to assign nonexistent symbol SECURITY_REALTIME
.config:3152:warning: trying to assign nonexistent symbol CLUSTER

```

Any idea why this is happening? I'm copying and pasting the code exactly. Stumped by this:???::confused:

---

### Post by xXx 0wn3d xXx on 2006-06-11
[QUOTE=Mourner]Thank you for such a comprehensive guide, **xXx 0wn3d xXx**, I wouldn't cope with compiling and deploying a customized kernel without it. 

I have a question though. According to the guide, the default Dapper kernel configuration is imported before any changes. So, if I haven't touched any graphic and console devices settings in xconfig at all, why does the new kernel behave so differently (in my case, framebuffer for usplash is not working - I have a blank screen instead of it while loading)?

Thanks in advance.[/QUOTE]
To get usplash to work, re-install it and then try adding vga=789 or another vga number to your splash line in grub:
> quiet splash 

Then add vga=789 to it:
> quiet splash vga=789 

---

### Post by jeremytaylor on 2006-06-11
Wow, it's really quick, thanks for the guide!

Having problems with my wireless card though. It's the standard intel 2200 hing so I kindof expected the kernel to support it. 

I've tried linking the firmware from a previous kernel as suggested somewhere in this thread but I still get the following in dmesg

[4294680.398000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, git-1.0.8
[4294680.398000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[4294680.399000] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 17 (level, low) -> IRQ 177
[4294680.399000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294680.427000] Linux agpgart interface v0.101 (c) Dave Jones
[4294680.453000] agpgart: Detected an Intel 915GM Chipset.
[4294680.471000] ipw2200: ipw-2.4-boot.fw load failed: Reason -2
[4294680.471000] ipw2200: Unable to load firmware: -2
[4294680.471000] ipw2200: failed to register network device
[4294680.471000] ACPI: PCI interrupt for device 0000:03:02.0 disabled
[4294680.471000] ipw2200: probe of 0000:03:02.0 failed with error -5


Any suggestions? 
Jeremy

---

### Post by neoaddict on 2006-06-11
As I mentioned in my post above, any improvement from the 2.6.16ck12 kernel over the built-in kernel in Dapper?

---

### Post by jeremytaylor on 2006-06-12
No idea, never got that kernel to boot!

Any wirelss suggestions? I don't understand why I should need to recompile ndiswrapper when there are linux drivers for the intel card?
Jeremy

---

### Post by jeremytaylor on 2006-06-12
Ahh fixed it. Needed newer ipw2200 drivers and firmware. 
Thanks again for the how to... very pleased with my new dapper install. 
jeremy

---

### Post by dan4444 on 2006-06-12
step #15 says: 
sudo dpkg -i <name of the file>

Name of what file excactly?

---

### Post by RavenOfOdin on 2006-06-12
[QUOTE=dan4444]step #15 says: 
sudo dpkg -i <name of the file>

Name of what file excactly?[/QUOTE]

The .deb file produced by kernel_image. :rolleyes:

---

### Post by xinix on 2006-06-13
I followed the directions with no problems and have a kernel that I can boot from.  My SATA partitions aren't mounting though.  I left the settings the same as what was in the stock kernel config.  How do I go about solving this problem?

---

### Post by sswords on 2006-06-13
For anyone who wants to use the nvidia legacy driver with the 2.6.16 kernel, I found that I needed an unofficial patch (available from the nvidia linux forum [here]("http://www.nvnews.net/vbulletin/showthread.php?t=67068")) for it to compile.  There are other some other patches available [here]("http://www.nvnews.net/vbulletin/showthread.php?t=50150") which I didn't use but might be important for some people.

---

### Post by echo $USER on 2006-06-13
I get this message when i run the last command to build the .dpkg file:

> /usr/src/linux-2.6.16ck12/scripts/gen_initramfs_list.sh: Cannot open 'y'
make[2]: *** [usr/initramfs_list] Error 1
make[1]: *** [usr] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16ck12'
make: *** [stamp-build] Error 2

---

### Post by echo $USER on 2006-06-14
[QUOTE=echo $USER]I get this message when i run the last command to build the .dpkg file:[/QUOTE]

I started over, but i excluded adding the patch.  It worked, but now i cant load X with the new kernel.  Said something about can't load nvidia module.  Nvidia driver works on stock kernel; should i reinstall the nvidia driver for the new kernel?

---

### Post by anodizer on 2006-06-14
[QUOTE=echo $USER]I started over, but i excluded adding the patch.  It worked, but now i cant load X with the new kernel.  Said something about can't load nvidia module.  Nvidia driver works on stock kernel; should i reinstall the nvidia driver for the new kernel?[/QUOTE]

Yes of course, you must always reinstall vga driver after installing a new kernel.

---

### Post by echo $USER on 2006-06-14
[QUOTE=anodizer]Yes of course, you must always reinstall vga driver after installing a new kernel.[/QUOTE]

Will it screw up the nvidia driver i installed for kernel 2.6.15?

---

### Post by bartman on 2006-06-14
I don't think so.

The only thing you might want to backup is your xorg.conf!

---

### Post by echo $USER on 2006-06-14
[QUOTE=bartman]I don't think so.

The only thing you might want to backup is your xorg.conf![/QUOTE]

Thanks! Will do.

---

### Post by abbot on 2006-06-14
Got the same error as Ravpaul did.  Kept going and got this error durring the compiling step.

 CC      fs/proc/root.o
  CC      fs/proc/base.o
  CC      fs/proc/generic.o
fs/proc/generic.c: In function ‘remove_proc_entry’:
fs/proc/generic.c:688: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[3]: *** [fs/proc/generic.o] Error 1
make[2]: *** [fs/proc] Error 2
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16ck12'
make: *** [stamp-build] Error 2

---

### Post by echo $USER on 2006-06-14
I had the same error.  Start over and skip the part about adding the kernel patch.  Then it will work.

---

### Post by abbot on 2006-06-14
ok.  i'm trying that, but i still get that errors durring step 13.

```
root@adam-ubuntu:/usr/src/linux# make xconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  CHECK   qt
  HOSTCC  scripts/kconfig/conf.o
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
#
# using defaults found in .config
#
.config:19:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:39:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:144:warning: trying to assign nonexistent symbol X86_UP_APIC_DEFAULT_OFF.config:166:warning: trying to assign nonexistent symbol 05GB
.config:167:warning: trying to assign nonexistent symbol 1GB
.config:168:warning: trying to assign nonexistent symbol 2GB
.config:169:warning: trying to assign nonexistent symbol 3GB
.config:210:warning: trying to assign nonexistent symbol ACPI_SBS
.config:220:warning: trying to assign nonexistent symbol ACPI_PCC
.config:221:warning: trying to assign nonexistent symbol ACPI_SONY
.config:229:warning: trying to assign nonexistent symbol ACPI_TC1100
.config:230:warning: trying to assign nonexistent symbol ACPI_INITRD
.config:231:warning: trying to assign nonexistent symbol ACPI_DEV
.config:336:warning: trying to assign nonexistent symbol PCMCIA_PROBE_MEM
.config:477:warning: trying to assign nonexistent symbol IP_NF_MATCH_LIMIT
.config:479:warning: trying to assign nonexistent symbol IP_NF_MATCH_MAC
.config:480:warning: trying to assign nonexistent symbol IP_NF_MATCH_PKTTYPE
.config:481:warning: trying to assign nonexistent symbol IP_NF_MATCH_MARK
.config:488:warning: trying to assign nonexistent symbol IP_NF_MATCH_LENGTH
.config:490:warning: trying to assign nonexistent symbol IP_NF_MATCH_TCPMSS
.config:491:warning: trying to assign nonexistent symbol IP_NF_MATCH_HELPER
.config:492:warning: trying to assign nonexistent symbol IP_NF_MATCH_STATE
.config:493:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNTRACK
.config:495:warning: trying to assign nonexistent symbol IP_NF_MATCH_PHYSDEV
.config:497:warning: trying to assign nonexistent symbol IP_NF_MATCH_REALM
.config:498:warning: trying to assign nonexistent symbol IP_NF_MATCH_SCTP
.config:499:warning: trying to assign nonexistent symbol IP_NF_MATCH_DCCP
.config:500:warning: trying to assign nonexistent symbol IP_NF_MATCH_COMMENT
.config:501:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNMARK
.config:502:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNBYTES
.config:504:warning: trying to assign nonexistent symbol IP_NF_MATCH_STRING
.config:510:warning: trying to assign nonexistent symbol IP_NF_TARGET_NFQUEUE
.config:527:warning: trying to assign nonexistent symbol IP_NF_TARGET_MARK
.config:528:warning: trying to assign nonexistent symbol IP_NF_TARGET_CLASSIFY
.config:530:warning: trying to assign nonexistent symbol IP_NF_TARGET_CONNMARK
.config:533:warning: trying to assign nonexistent symbol IP_NF_TARGET_NOTRACK
.config:543:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LIMIT
.config:544:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MAC
.config:551:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MARK
.config:554:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LENGTH
.config:556:warning: trying to assign nonexistent symbol IP6_NF_MATCH_PHYSDEV
.config:560:warning: trying to assign nonexistent symbol IP6_NF_TARGET_NFQUEUE
.config:562:warning: trying to assign nonexistent symbol IP6_NF_TARGET_MARK
.config:828:warning: trying to assign nonexistent symbol IEEE80211_SOFTMAC
.config:829:warning: trying to assign nonexistent symbol IEEE80211_SOFTMAC_DEBUG.config:830:warning: trying to assign nonexistent symbol IEEE80211_1_1_13
.config:831:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_WEP
.config:832:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_CCMP
.config:833:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_TKIP
.config:1045:warning: trying to assign nonexistent symbol BLK_DEV_CLOOP
.config:1056:warning: trying to assign nonexistent symbol BLK_DEV_GNBD
.config:1077:warning: trying to assign nonexistent symbol BLK_DEV_IDEACPI
.config:1086:warning: symbol value 'm' invalid for BLK_DEV_IDEPNP
.config:1118:warning: trying to assign nonexistent symbol PDC202XX_FORCE
.config:1161:warning: trying to assign nonexistent symbol SCSI_SPI2_ATTRS
.config:1169:warning: trying to assign nonexistent symbol SAS_CLASS
.config:1170:warning: trying to assign nonexistent symbol SAS_DEBUG
.config:1184:warning: trying to assign nonexistent symbol SCSI_AIC94XX
.config:1185:warning: trying to assign nonexistent symbol AIC94XX_DEBUG
.config:1204:warning: trying to assign nonexistent symbol SCSI_ARCMSR
.config:1226:warning: trying to assign nonexistent symbol SCSI_SATA_ACPI
.config:1258:warning: trying to assign nonexistent symbol SCSI_SYM53C8XX_MMIO
.config:1274:warning: trying to assign nonexistent symbol SCSI_QLA2XXX
.config:1382:warning: trying to assign nonexistent symbol IEEE1394_CMP
.config:1536:warning: trying to assign nonexistent symbol R1000
.config:1559:warning: trying to assign nonexistent symbol NET_IPG
.config:1610:warning: trying to assign nonexistent symbol IPW2100_FS_AMILO_M7400.config:1613:warning: trying to assign nonexistent symbol IPW2200_MONITOR
.config:1632:warning: trying to assign nonexistent symbol ADM8211
.config:1643:warning: trying to assign nonexistent symbol WLAN_NG
.config:1644:warning: trying to assign nonexistent symbol PRISM2
.config:1645:warning: trying to assign nonexistent symbol PRISM2_USB
.config:1646:warning: trying to assign nonexistent symbol PRISM2_PCI
.config:1647:warning: trying to assign nonexistent symbol PRISM2_PLX
.config:1648:warning: trying to assign nonexistent symbol PRISM2_CS
.config:1649:warning: trying to assign nonexistent symbol NET_ACX
.config:1650:warning: trying to assign nonexistent symbol NET_ACX_PCI
.config:1651:warning: trying to assign nonexistent symbol NET_ACX_USB
.config:1652:warning: trying to assign nonexistent symbol BCM43XX
.config:1653:warning: trying to assign nonexistent symbol BCM43XX_DEBUG
.config:1654:warning: trying to assign nonexistent symbol BCM43XX_DMA
.config:1655:warning: trying to assign nonexistent symbol BCM43XX_PIO
.config:1656:warning: trying to assign nonexistent symbol BCM43XX_DMA_AND_PIO_MODE
.config:1657:warning: trying to assign nonexistent symbol BCM43XX_DMA_MODE
.config:1658:warning: trying to assign nonexistent symbol BCM43XX_PIO_MODE
.config:1659:warning: trying to assign nonexistent symbol PRISM54_SOFTMAC
.config:1660:warning: trying to assign nonexistent symbol NET_RT2600
.config:1661:warning: trying to assign nonexistent symbol NET_RT2500
.config:1662:warning: trying to assign nonexistent symbol NET_RT2400
.config:1663:warning: trying to assign nonexistent symbol NET_RTL818X
.config:1664:warning: trying to assign nonexistent symbol NET_RTL8187
.config:1665:warning: trying to assign nonexistent symbol IPW3945
.config:1666:warning: trying to assign nonexistent symbol IPW3945_DEBUG
.config:1667:warning: trying to assign nonexistent symbol IPW3945_MONITOR
.config:1668:warning: trying to assign nonexistent symbol NET_MRV8K
.config:1783:warning: trying to assign nonexistent symbol NDISWRAPPER
.config:1936:warning: trying to assign nonexistent symbol MISDN_DRV
.config:1937:warning: trying to assign nonexistent symbol MISDN_MEMDEBUG
.config:1938:warning: trying to assign nonexistent symbol MISDN_AVM_FRITZ
.config:1939:warning: trying to assign nonexistent symbol MISDN_HFCPCI
.config:1940:warning: trying to assign nonexistent symbol MISDN_HFCMULTI
.config:1941:warning: trying to assign nonexistent symbol MISDN_HFCUSB
.config:1942:warning: trying to assign nonexistent symbol MISDN_SPEEDFAX
.config:1943:warning: trying to assign nonexistent symbol MISDN_W6692
.config:1944:warning: trying to assign nonexistent symbol MISDN_DSP
.config:2023:warning: trying to assign nonexistent symbol INPUT_ACERHK
.config:2048:warning: trying to assign nonexistent symbol ECC
.config:2370:warning: trying to assign nonexistent symbol AVERATEC_5100P
.config:2371:warning: trying to assign nonexistent symbol PACKARDBELL_E5
.config:2522:warning: trying to assign nonexistent symbol DVB_TDA80XX
.config:2544:warning: trying to assign nonexistent symbol DVB_ATMEL_AT76C651
.config:2552:warning: trying to assign nonexistent symbol DVB_NXT2002
.config:2565:warning: trying to assign nonexistent symbol DXR3
.config:2566:warning: trying to assign nonexistent symbol EM8300
.config:2567:warning: trying to assign nonexistent symbol EM8300_LOOPBACK
.config:2568:warning: trying to assign nonexistent symbol EM8300_UCODETIMEOUT
.config:2569:warning: trying to assign nonexistent symbol EM8300_DICOMFIX
.config:2570:warning: trying to assign nonexistent symbol EM8300_DICOMCTRL
.config:2571:warning: trying to assign nonexistent symbol EM8300_DICOMPAL
.config:2572:warning: trying to assign nonexistent symbol ADV717X
.config:2573:warning: trying to assign nonexistent symbol ADV717X_SWAP
.config:2574:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT16BIT.config:2575:warning: trying to assign nonexistent symbol ADV717X_PIXELPORTPAL
.config:2576:warning: trying to assign nonexistent symbol BT865
.config:2602:warning: symbol value 'm' invalid for FB_VESA
.config:2631:warning: trying to assign nonexistent symbol FB_ATY_XL_INIT
.config:2650:warning: trying to assign nonexistent symbol FB_IMAC
.config:2700:warning: trying to assign nonexistent symbol SND_GENERIC_DRIVER
.config:2813:warning: trying to assign nonexistent symbol BT_ALSA
.config:2936:warning: trying to assign nonexistent symbol USB_SYNAPTICS
.config:2937:warning: trying to assign nonexistent symbol USB_CPADDEV
.config:2958:warning: trying to assign nonexistent symbol USB_QC
.config:2959:warning: trying to assign nonexistent symbol USB_SPCA5XX
.config:2960:warning: trying to assign nonexistent symbol USB_PODXTPRO
.config:2962:warning: trying to assign nonexistent symbol USB_OV511_DECOMP
.config:2963:warning: trying to assign nonexistent symbol USB_OV518_DECOMP
.config:2987:warning: trying to assign nonexistent symbol USB_EAGLE
.config:2988:warning: trying to assign nonexistent symbol USB_ZD1211
.config:2989:warning: trying to assign nonexistent symbol USB_ATMEL
.config:2990:warning: trying to assign nonexistent symbol USB_RT2570
.config:3101:warning: trying to assign nonexistent symbol MMC_SDHCI
.config:3207:warning: trying to assign nonexistent symbol ASFS_FS
.config:3208:warning: trying to assign nonexistent symbol ASFS_DEFAULT_CODEPAGE
.config:3209:warning: trying to assign nonexistent symbol ASFS_RW
.config:3228:warning: trying to assign nonexistent symbol SQUASHFS
.config:3229:warning: trying to assign nonexistent symbol SQUASHFS_1_0_COMPATIBILITY
.config:3230:warning: trying to assign nonexistent symbol SQUASHFS_2_0_COMPATIBILITY
.config:3238:warning: trying to assign nonexistent symbol UNION_FS
.config:3285:warning: trying to assign nonexistent symbol GFS_FS
.config:3286:warning: trying to assign nonexistent symbol GFS_FS_LOCK_HARNESS
.config:3407:warning: trying to assign nonexistent symbol SECURITY_REALTIME
.config:3472:warning: trying to assign nonexistent symbol CLUSTER

```

---edit---

well, it still gave me an error at close to the same spot even though i didn't apply the kernal patch.

```
 CC      fs/exec.o
  CC      fs/pipe.o
  CC      fs/namei.o
  CC      fs/fcntl.o
  CC      fs/ioctl.o
  CC      fs/readdir.o
fs/readdir.c: In function &#8216;sys_getdents&#8217;:
fs/readdir.c:177: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[2]: *** [fs/readdir.o] Error 1
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16'
make: *** [stamp-build] Error 2
root@adam-ubuntu:/usr/src/linux#

```

---

### Post by lime4x4 on 2006-06-14
if i deselect stuff that i don't need will that help make the system faster???
I c alot of stuff checked marked that doesn't apply to my system like compaq raid array dell and toshiba laptop support just to name a few

---

### Post by lime4x4 on 2006-06-14
well it worked...lol my system is faster then before...the only problem i have is when i rebooted with the new kernel i had alot of software updates i have one left that won't update here is the error

E: /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1sarge1_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a

Is this related to the kernel upgrade??

---

### Post by bittdude on 2006-06-15
I compiled my new kernel with no problems and it works just fine even with the splash.  My only problem is the ATI drivers.  I can't seem to get them to work at all.  I installed fgrlx-kernel-source from apt command you said but unfortunately I'm still getting nothing.   The drivers worked perfectly in the default kernel provided with Drapper.  Is there something I'm missing or neglecting to do?

---

### Post by mfaridi on 2006-06-15
I installed ubuntu 6.06 
I want install firestarter and another program  for install this program it s need kernel source

I download kernel source with this command
apt-get install -d
I just download it 
can I install it with this command

dpkg -i kernel*.deb

---

### Post by ltrinh on 2006-06-15
Thanks for the guide xXx 0wn3d xXx.

I'm using dapper drake final on a dual core amd processor.

I need your help.  I was able to compile the 2.6.16 kernel cleanly with the ck12 patch without any problems.  However, after rebooting I am not able to get past the login screen.  The first time I logged in I got that message that my home directory is /home/loc but that it does not exist.  So to check, I booted into failsafe mode and it turned out that it was gone.  In fact the home directory was empty.  I then reverted back to the old kernel and rebooted into my system just fine.  I then copied the home directory /home/loc to a backup directory.  Next, I edited menu.lst with gedit and uncommented the the compiled ck12 kernel and rebooted.  

This time when I logged in I got this message:

"Users's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users."

Do I need to copy the directory with some kind of special permission other than just using Sudo?  I have compiled 3 to 4 times now both with and without the patch and each time I have not been able to get past the login screen.

Any help would be greatly appreciated.  I'd love to get this working.

---

### Post by ltrinh on 2006-06-15
Also here is some more info on my issue:

~/.xsession-errors file

/etc/gdm/PreSession/Default:  Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default:  running:  /usr/bin/sessreg -a -w /var/log/wtmp -x "/var/lib/gdm/:0.xservers" -h "" -l ":0" "loc"

/etc/gdm/Xsession:  Beginning session setup...

could not set mode 0700 on private per-user gnome configuration directory '/home/loc/.gnome2_private/': Operation not permitted

------------------------------------------------------------------------

Here is my menu.lst printout from /boot/grub:

title             Ubuntu, kernel 2.6.16-ck12
root             (hd0,0)
kernel           /boot/vmlinuz-2.6.16-ck12 root=/dev/sda1 ro quiet splash
initrd            /boot/initrd.img-2.6.16-ck12
savedefault
boot

title             Ubuntu, kernel 2.6.16-ck12 (recovery mode)
root             (hd0,0)
kernel           /boot/vmlinuz-2.6.16-ck12 root=/dev/sda1 ro quiet splash
initrd            /boot/initrd.img-2.6.16-ck12
boot

---

### Post by ehula on 2006-06-15
[QUOTE=keithjr]I just solved it for myself, I don't know if I was having the same issues though... I explicitly removed the packages I had used to install fglrx the first time around (before the upgrade), then re-installed them.  Of course, the linux-restricted-modules has to be replaced with the fglrx kernel source you provided... but I think that's the issue people are running into: unclean installation[/QUOTE]
Can you be more specific about the packages you removed. Which ones did you remove and when? After compiling the kernel? And which ones did you reinstall?

---

### Post by lime4x4 on 2006-06-16
ok need to get my ati card drivers back up now..lol I tried what u said and this is what i get

john@ubuntu:~$ sudo apt-get install fglrx-kernel-source
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fglrx-kernel-source


Any ideas

---

### Post by xXx 0wn3d xXx on 2006-06-16
[QUOTE=lime4x4]ok need to get my ati card drivers back up now..lol I tried what u said and this is what i get

john@ubuntu:~$ sudo apt-get install fglrx-kernel-source
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fglrx-kernel-source


Any ideas[/QUOTE]
[ Make sure that you have the universe and multiverse repositories enabled. ](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by shuttleworthwannabe on 2006-06-17
Thanks for the very good HOWTO. I a busy doing this with the latest kernel 2.6.16.20 for my laptop and preferred the 386 arch when following the instructions. Questions:

1. I do not need the patch for this kernel, right? I did not patch, just that you know.
2. How long does it take to get done: I am doing step #14 right now and it is taking forever; CPU is at 100% and fan is blarring and the tempt are at 199'F. I am worried I have this running for the last 35 minutes (I know because I have laundry doing on the timer..hehehe).

Let me know if I am not on the right track. No errors so far. 

Wating for the .deb file to pop-up....

---

### Post by xXx 0wn3d xXx on 2006-06-17
No you don't need to patch, and it can take anywhere to 10-2 hours depending on your cpu and stuff.

---

### Post by berserker on 2006-06-18
My new 2.6.17-cks1 kernel seems to be a lot snappier than the 2.6.16-cks12 kernel.  Desktop is more responsive and apps open noticeably quicker.

Cheers!

---

### Post by xXx 0wn3d xXx on 2006-06-18
I have just compilied a new k7 kernel and optimized it. I went to a few other places (gentoo forums and etc.) and found tons of optimizations. I have not had a chance to test the kernel but if you would like to try it out, the file can be downloaded [ here. ](http://files.filefront.com/261620_k7_tarbz2/;5164649;;/fileinfo.html) My page is ubuntu.filefront.com.

---

### Post by nameiwantistaken on 2006-06-18
I got everything fine until the end uwhen the second last step spit out "undefined reference to 'register_hdlc_device'" and then it just went back to the command line.  It gives some build error.  Anyone know of a graphical way to do this?

---

### Post by norman_h on 2006-06-19
Anyone tried the new 2.6.17 kernel yet?

---

### Post by Jayzilla on 2006-06-19
I want to because of the Broadcom 43xx wireless driver support, but I don't know how.  I'm John Q. Linuxn00b.

---

### Post by tseliot on 2006-06-19
[QUOTE=norman_h]Anyone tried the new 2.6.17 kernel yet?[/QUOTE]
Yes, I did yesterday. Unfortunately the kernel didn't allow me to mount the partitions of my 2nd hard disk (the ones of my 1st hard disk were mounted). I admit that I didn't spend much time configuring the kernel. I'll try it again.

The rest worked fine.

---

### Post by Jayzilla on 2006-06-19
[QUOTE=tseliot]Yes, I did yesterday. Unfortunately the kernel didn't allow me to mount the partitions of my 2nd hard disk (the ones of my 1st hard disk were mounted). I admit that I didn't spend much time configuring the kernel. I'll try it again.

The rest worked fine.[/QUOTE]

Can you explain how you upgraded?  I'd like to give it a go, but I'm not entirely sure how.

---

### Post by jakeee on 2006-06-19
I usually compile the full version of the kernel using my old config maybe changing a thing or two. Just follow this guide.

Btw. I used this guide on the 2.6.17 kernel and I couldn't find the I/O scheduler part. I then tried menuconfig and found it :)

---

### Post by tseliot on 2006-06-19
[QUOTE=Jayzilla]Can you explain how you upgraded?  I'd like to give it a go, but I'm not entirely sure how.[/QUOTE]
Just recompile it (follow this guide).

---

### Post by ultima on 2006-06-19
I have successfully compiled and am now running on kernel 2.6.17 using this guide. No probs so far. My mounts are fine. I also got rid of a whole lot of crap from the kernel I didn't need so it didn't take as long to compile.

---

### Post by unique on 2006-06-19
Ok I also am running the latest 2.6.17 kernel... Fast!  And now i don't need the apci=off in my boot grub menu.lst! No more kernel panic!

One question though.... Do I also need to use the 2.6.17 patch?  or just the kernel...  I compiled it with out the patch and everything seems to be working fine not sure if i need the patch or not?  

P.S. For anyone wanting to try the latest intel ipw200 driver... the 2.6.17 has the latest driver loaded! All you have to do is copy the latest firmware to your /lib/firmware dir!


Thanks in advanced....

---

### Post by xXx 0wn3d xXx on 2006-06-19
You do not need to patch your kernels. It is completly optional.

---

### Post by ultima on 2006-06-19
That patch was only for the 2.6.16 kernel so you were right not to use it.

---

### Post by unique on 2006-06-19
[QUOTE=ultima]That patch was only for the 2.6.16 kernel so you were right not to use it.[/QUOTE]

Well I new not to use the 2.6.16 patch for the 2.6.17 kernel that i used...  but I did see a 2.6.17 patch in the ftp dir where i downloaded the kernel.  Just not sure what it does and if i need it.

**xXx 0wn3d xXx** Thanks for this thread! Has help me so much!

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=unique]Well I new not to use the 2.6.16 patch for the 2.6.17 kernel that i used...  but I did see a 2.6.17 patch in the ftp dir where i downloaded the kernel.  Just not sure what it does and if i need it.

**xXx 0wn3d xXx** Thanks for this thread! Has help me so much![/QUOTE]
The patches on kernel.org (not ck patches) allow you to upgrade an old kernel. You can do the following methods to upgrade your kernel with the patch.

1. Download the patch and apply it to an old kernel directoy (2.6.16.20, etc.)

2. If you have an old kernel that it still zipped, you can uncompress it and then apply the patch. bringing it to the latest version. Very useful for dial-up users.

---

### Post by unique on 2006-06-19
[QUOTE=xXx 0wn3d xXx]The patches on kernel.org (not ck patches) allow you to upgrade an old kernel. You can do the following methods to upgrade your kernel with the patch.

1. Download the patch and apply it to an old kernel directoy (2.6.16.20, etc.)

2. If you have an old kernel that it still zipped, you can uncompress it and then apply the patch. bringing it to the latest version. Very useful for dial-up users.[/QUOTE]

Awwww ok!  that makes sence, thanks for clearing that up!

---

### Post by Jayzilla on 2006-06-19
My laptop powers down in the middle of building the kernel.  I may scream.

Any idea why this is occurring?

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=Jayzilla]My laptop powers down in the middle of building the kernel.  I may scream.

Any idea why this is occurring?[/QUOTE]
Is it over heating ? Check that your fans are properly functioning. Another reason is that it may have been idle for too long making is shutdown.

---

### Post by nameiwantistaken on 2006-06-19
Step 1 on the post doesn't work for me (using latest Ubuntu Live CD install).  Does anyone know how I can get that to work?

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=nameiwantistaken]Step 1 on the post doesn't work for me (using latest Ubuntu Live CD install).  Does anyone know how I can get that to work?[/QUOTE]
You can't install things on the Ubuntu live cd. You will need to install for that. Even if those things were installed you could not boot into the kernel. The live cd is read from the cd drive.

---

### Post by OPaul on 2006-06-19
Because kernels created this way don't appear in the Synaptic Package Manager, what is the correct way to remove them?

---

### Post by Jayzilla on 2006-06-19
Success!  Everything's running smoothly.  

Now I just have to get my wifi working :)

---

### Post by OPaul on 2006-06-19
[QUOTE=OPaul]Because kernels created this way don't appear in the Synaptic Package Manager, what is the correct way to remove them?[/QUOTE]
Oh nm, they do appear in the Package Manager. My mistake.

---

### Post by neuropsychguy on 2006-06-20
I was on step 13 or so (can't remember which one now but it is below) and I got this huge error message. What's wrong? I'm fairly new to Linux so I don't know too mcuh. :confused: 

root@*******:/usr/src/linux# make xconfig
  [PHP]HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  CHECK   qt
  HOSTCC  scripts/kconfig/conf.o
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
#
# using defaults found in .config
#
.config:19:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:39:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:54:warning: trying to assign nonexistent symbol CC_ALIGN_FUNCTIONS
.config:55:warning: trying to assign nonexistent symbol CC_ALIGN_LABELS
.config:56:warning: trying to assign nonexistent symbol CC_ALIGN_LOOPS
.config:57:warning: trying to assign nonexistent symbol CC_ALIGN_JUMPS
.config:67:warning: trying to assign nonexistent symbol OBSOLETE_MODPARM
.config:144:warning: trying to assign nonexistent symbol ENABLE_ALT_SMP
.config:170:warning: trying to assign nonexistent symbol 05GB
.config:171:warning: trying to assign nonexistent symbol 1GB
.config:172:warning: trying to assign nonexistent symbol 2GB
.config:173:warning: trying to assign nonexistent symbol 3GB
.config:216:warning: trying to assign nonexistent symbol ACPI_SBS
.config:227:warning: trying to assign nonexistent symbol ACPI_PCC
.config:228:warning: trying to assign nonexistent symbol ACPI_SONY
.config:236:warning: trying to assign nonexistent symbol ACPI_TC1100
.config:237:warning: trying to assign nonexistent symbol ACPI_INITRD
.config:238:warning: trying to assign nonexistent symbol ACPI_DEV
.config:310:warning: trying to assign nonexistent symbol PCI_LEGACY_PROC
.config:344:warning: trying to assign nonexistent symbol PCMCIA_PROBE_MEM
.config:485:warning: trying to assign nonexistent symbol IP_NF_MATCH_LIMIT
.config:487:warning: trying to assign nonexistent symbol IP_NF_MATCH_MAC
.config:488:warning: trying to assign nonexistent symbol IP_NF_MATCH_PKTTYPE
.config:489:warning: trying to assign nonexistent symbol IP_NF_MATCH_MARK
.config:490:warning: trying to assign nonexistent symbol IP_NF_MATCH_MULTIPORT
.config:495:warning: trying to assign nonexistent symbol IP_NF_MATCH_AH_ESP
.config:496:warning: trying to assign nonexistent symbol IP_NF_MATCH_LENGTH
.config:498:warning: trying to assign nonexistent symbol IP_NF_MATCH_TCPMSS
.config:499:warning: trying to assign nonexistent symbol IP_NF_MATCH_HELPER
.config:500:warning: trying to assign nonexistent symbol IP_NF_MATCH_STATE
.config:501:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNTRACK
.config:503:warning: trying to assign nonexistent symbol IP_NF_MATCH_PHYSDEV
.config:505:warning: trying to assign nonexistent symbol IP_NF_MATCH_REALM
.config:506:warning: trying to assign nonexistent symbol IP_NF_MATCH_SCTP
.config:507:warning: trying to assign nonexistent symbol IP_NF_MATCH_DCCP
.config:508:warning: trying to assign nonexistent symbol IP_NF_MATCH_COMMENT
.config:509:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNMARK
.config:510:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNBYTES
.config:512:warning: trying to assign nonexistent symbol IP_NF_MATCH_STRING
.config:518:warning: trying to assign nonexistent symbol IP_NF_TARGET_NFQUEUE
.config:535:warning: trying to assign nonexistent symbol IP_NF_TARGET_MARK
.config:536:warning: trying to assign nonexistent symbol IP_NF_TARGET_CLASSIFY
.config:538:warning: trying to assign nonexistent symbol IP_NF_TARGET_CONNMARK
.config:541:warning: trying to assign nonexistent symbol IP_NF_TARGET_NOTRACK
.config:551:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LIMIT
.config:552:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MAC
.config:557:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MULTIPORT
.config:559:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MARK
.config:561:warning: trying to assign nonexistent symbol IP6_NF_MATCH_AHESP
.config:562:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LENGTH
.config:564:warning: trying to assign nonexistent symbol IP6_NF_MATCH_PHYSDEV
.config:568:warning: trying to assign nonexistent symbol IP6_NF_TARGET_NFQUEUE
.config:570:warning: trying to assign nonexistent symbol IP6_NF_TARGET_MARK
.config:619:warning: trying to assign nonexistent symbol IP_DCCP_UNLOAD_HACK
.config:838:warning: trying to assign nonexistent symbol IEEE80211_1_1_13
.config:839:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_WEP
.config:840:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_CCMP
.config:841:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_CRYPT_TKIP
.config:904:warning: trying to assign nonexistent symbol MTD_CFI_AMDSTD_RETRY
.config:949:warning: trying to assign nonexistent symbol MTD_BLKMTD
.config:1053:warning: trying to assign nonexistent symbol BLK_DEV_CLOOP
.config:1064:warning: trying to assign nonexistent symbol BLK_DEV_GNBD
.config:1085:warning: trying to assign nonexistent symbol BLK_DEV_IDEACPI
.config:1094:warning: symbol value 'm' invalid for BLK_DEV_IDEPNP
.config:1126:warning: trying to assign nonexistent symbol PDC202XX_FORCE
.config:1169:warning: trying to assign nonexistent symbol SCSI_SPI2_ATTRS
.config:1177:warning: trying to assign nonexistent symbol SAS_CLASS
.config:1178:warning: trying to assign nonexistent symbol SAS_DEBUG
.config:1192:warning: trying to assign nonexistent symbol SCSI_AIC94XX
.config:1193:warning: trying to assign nonexistent symbol AIC94XX_DEBUG
.config:1212:warning: trying to assign nonexistent symbol SCSI_ARCMSR
.config:1234:warning: trying to assign nonexistent symbol SCSI_SATA_ACPI
.config:1282:warning: trying to assign nonexistent symbol SCSI_QLA2XXX
.config:1287:warning: trying to assign nonexistent symbol SCSI_QLA6312
.config:1390:warning: trying to assign nonexistent symbol IEEE1394_CMP
.config:1544:warning: trying to assign nonexistent symbol R1000
.config:1567:warning: trying to assign nonexistent symbol NET_IPG
.config:1618:warning: trying to assign nonexistent symbol IPW2100_FS_AMILO_M7400.config:1640:warning: trying to assign nonexistent symbol ADM8211
.config:1651:warning: trying to assign nonexistent symbol WLAN_NG
.config:1652:warning: trying to assign nonexistent symbol PRISM2
.config:1653:warning: trying to assign nonexistent symbol PRISM2_USB
.config:1654:warning: trying to assign nonexistent symbol PRISM2_PCI
.config:1655:warning: trying to assign nonexistent symbol PRISM2_PLX
.config:1656:warning: trying to assign nonexistent symbol PRISM2_CS
.config:1657:warning: trying to assign nonexistent symbol NET_ACX
.config:1658:warning: trying to assign nonexistent symbol NET_ACX_PCI
.config:1659:warning: trying to assign nonexistent symbol NET_ACX_USB
.config:1667:warning: trying to assign nonexistent symbol PRISM54_SOFTMAC
.config:1668:warning: trying to assign nonexistent symbol NET_RT2600
.config:1669:warning: trying to assign nonexistent symbol NET_RT2500
.config:1670:warning: trying to assign nonexistent symbol NET_RT2400
.config:1671:warning: trying to assign nonexistent symbol NET_RTL818X
.config:1672:warning: trying to assign nonexistent symbol NET_RTL8187
.config:1673:warning: trying to assign nonexistent symbol IPW3945
.config:1674:warning: trying to assign nonexistent symbol IPW3945_DEBUG
.config:1675:warning: trying to assign nonexistent symbol IPW3945_MONITOR
.config:1676:warning: trying to assign nonexistent symbol NET_MRV8K
.config:1725:warning: trying to assign nonexistent symbol VENDOR_SANGOMA
.config:1791:warning: trying to assign nonexistent symbol NDISWRAPPER
.config:1943:warning: trying to assign nonexistent symbol MISDN_DRV
.config:1944:warning: trying to assign nonexistent symbol MISDN_MEMDEBUG
.config:1945:warning: trying to assign nonexistent symbol MISDN_AVM_FRITZ
.config:1946:warning: trying to assign nonexistent symbol MISDN_HFCPCI
.config:1947:warning: trying to assign nonexistent symbol MISDN_HFCMULTI
.config:1948:warning: trying to assign nonexistent symbol MISDN_HFCUSB
.config:1949:warning: trying to assign nonexistent symbol MISDN_SPEEDFAX
.config:1950:warning: trying to assign nonexistent symbol MISDN_W6692
.config:1951:warning: trying to assign nonexistent symbol MISDN_DSP
.config:2030:warning: trying to assign nonexistent symbol INPUT_ACERHK
.config:2055:warning: trying to assign nonexistent symbol ECC
.config:2084:warning: trying to assign nonexistent symbol SERIAL_8250_ACPI
.config:2284:warning: trying to assign nonexistent symbol SENSORS_RTC8564
.config:2286:warning: trying to assign nonexistent symbol RTC_X1205_I2C
.config:2296:warning: trying to assign nonexistent symbol W1_MATROX
.config:2297:warning: trying to assign nonexistent symbol W1_DS9490
.config:2298:warning: trying to assign nonexistent symbol W1_DS9490_BRIDGE
.config:2299:warning: trying to assign nonexistent symbol W1_THERM
.config:2300:warning: trying to assign nonexistent symbol W1_SMEM
.config:2302:warning: trying to assign nonexistent symbol W1_DS2433_CRC
.config:2350:warning: trying to assign nonexistent symbol AVERATEC_5100P
.config:2351:warning: trying to assign nonexistent symbol PACKARDBELL_E5
.config:2405:warning: trying to assign nonexistent symbol VIDEO_AUDIO_DECODER
.config:2406:warning: trying to assign nonexistent symbol VIDEO_DECODER
.config:2502:warning: trying to assign nonexistent symbol DVB_TDA80XX
.config:2524:warning: trying to assign nonexistent symbol DVB_ATMEL_AT76C651
.config:2532:warning: trying to assign nonexistent symbol DVB_NXT2002
.config:2545:warning: trying to assign nonexistent symbol DXR3
.config:2546:warning: trying to assign nonexistent symbol EM8300
.config:2547:warning: trying to assign nonexistent symbol EM8300_LOOPBACK
.config:2548:warning: trying to assign nonexistent symbol EM8300_UCODETIMEOUT
.config:2549:warning: trying to assign nonexistent symbol EM8300_DICOMFIX
.config:2550:warning: trying to assign nonexistent symbol EM8300_DICOMCTRL
.config:2551:warning: trying to assign nonexistent symbol EM8300_DICOMPAL
.config:2552:warning: trying to assign nonexistent symbol ADV717X
.config:2553:warning: trying to assign nonexistent symbol ADV717X_SWAP
.config:2554:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT16BIT.config:2555:warning: trying to assign nonexistent symbol ADV717X_PIXELPORTPAL
.config:2556:warning: trying to assign nonexistent symbol BT865
.config:2582:warning: symbol value 'm' invalid for FB_VESA
.config:2603:warning: trying to assign nonexistent symbol FB_RADEON_OLD
.config:2611:warning: trying to assign nonexistent symbol FB_ATY_XL_INIT
.config:2630:warning: trying to assign nonexistent symbol FB_IMAC
.config:2680:warning: trying to assign nonexistent symbol SND_GENERIC_DRIVER
.config:2793:warning: trying to assign nonexistent symbol BT_ALSA
.config:2799:warning: trying to assign nonexistent symbol OBSOLETE_OSS_DRIVER
.config:2867:warning: trying to assign nonexistent symbol OBSOLETE_OSS_USB_DRIVER
.config:2908:warning: trying to assign nonexistent symbol USB_MTOUCH
.config:2909:warning: trying to assign nonexistent symbol USB_ITMTOUCH
.config:2910:warning: trying to assign nonexistent symbol USB_EGALAX
.config:2917:warning: trying to assign nonexistent symbol USB_SYNAPTICS
.config:2918:warning: trying to assign nonexistent symbol USB_CPADDEV
.config:2939:warning: trying to assign nonexistent symbol USB_QC
.config:2940:warning: trying to assign nonexistent symbol USB_SPCA5XX
.config:2941:warning: trying to assign nonexistent symbol USB_PODXTPRO
.config:2943:warning: trying to assign nonexistent symbol USB_OV511_DECOMP
.config:2944:warning: trying to assign nonexistent symbol USB_OV518_DECOMP
.config:2968:warning: trying to assign nonexistent symbol USB_EAGLE
.config:2969:warning: trying to assign nonexistent symbol USB_ZD1211
.config:2970:warning: trying to assign nonexistent symbol USB_ATMEL
.config:2971:warning: trying to assign nonexistent symbol USB_RT2570
.config:3179:warning: trying to assign nonexistent symbol RELAYFS_FS
.config:3188:warning: trying to assign nonexistent symbol ASFS_FS
.config:3189:warning: trying to assign nonexistent symbol ASFS_DEFAULT_CODEPAGE
.config:3190:warning: trying to assign nonexistent symbol ASFS_RW
.config:3209:warning: trying to assign nonexistent symbol SQUASHFS
.config:3210:warning: trying to assign nonexistent symbol SQUASHFS_1_0_COMPATIBILITY
.config:3211:warning: trying to assign nonexistent symbol SQUASHFS_2_0_COMPATIBILITY
.config:3219:warning: trying to assign nonexistent symbol UNION_FS
.config:3266:warning: trying to assign nonexistent symbol GFS_FS
.config:3267:warning: trying to assign nonexistent symbol GFS_FS_LOCK_HARNESS
.config:3388:warning: trying to assign nonexistent symbol SECURITY_REALTIME
.config:3453:warning: trying to assign nonexistent symbol CLUSTER
.config:3459:warning: trying to assign nonexistent symbol X86_HT_DISABLE
make[1]: *** wait: No child processes.  Stop.
make[1]: *** Waiting for unfinished jobs....
make[1]: *** wait: No child processes.  Stop.
make: *** wait: No child processes.  Stop.
make: *** Waiting for unfinished jobs....
make: *** wait: No child processes.  Stop.[/PHP]

---

### Post by ravpaul on 2006-06-20
> 1. Download the patch and apply it to an old kernel directoy (2.6.16.20, etc.


What is the command to do this? As I am still unable to compile the kernel from scratch. Where do I download the ck patches from?

---

### Post by xXx 0wn3d xXx on 2006-06-20
[QUOTE=ravpaul]What is the command to do this? As I am still unable to compile the kernel from scratch. Where do I download the ck patches from?[/QUOTE]
Ck, performance patches, can be found [ here. ](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/) Patches for upgrading your kernel can be found on the kernel.org homepage.

---

### Post by mibadt on 2006-06-20
Hi,
I tried to follow the outline procedure to upgrade my Kubuntu 6.0.6 (fully updated) from (current) kernel 2.6.15-25-386 to 2.6.17.1 (full kernel, no patches).
The first 12 stages were OK. Entering stage 13 (make xconfig) it erred stating it can't connect to the X server (output follows). Please advise !:( 

TIA

====last stage output========
root@Atlantis:/usr/src/linux# pwd
/usr/src/linux
root@Atlantis:/usr/src/linux# uname -r
2.6.15-25-386
root@Atlantis:/usr/src/linux# cp /boot/config-2.6.15-25-386 .config
root@Atlantis:/usr/src/linux# make xconfig
  CHECK   qt
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

qconf: cannot connect to X server :0.0
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2
=========end of output=========

---

### Post by jamuir on 2006-06-20
don't do "make xconfig" as root.  root does not have permission to use the xserver (i.e. the display).

from your normal account, do this:

sudo make xconfig

-James

---

### Post by OPaul on 2006-06-20
Whenever I use this method to install a new kernel I loose the use of my Toshiba hotkeys, like display brightness. I copied the .config file over like it says  to do, so shouldn't whatever option it is that corresponds to them get checked?

---

### Post by haani on 2006-06-20
has anyone got Graphics Card and Wireless working on Acer Aspire 5672 after u install kernel 2.6.17??

---

### Post by jeremytaylor on 2006-06-20
I can't seem to get the fglrx module to compile. I've installed the source with 
sudo apt-get install fglrx-kernel-source
as suggested in the guide but when i make the kernel package i get
IGNORE_CC_MISMATCH=1 CC="gcc-4.0"  /usr/bin/make -C /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x -f Makefile SYSSRC=/usr/src/linux   KBUILD_PARAMS="-C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x"
make[3]: Entering directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[3]: Makefile: No such file or directory
make[3]: *** No rule to make target `Makefile'.  Stop.
make[3]: Leaving directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[2]: *** [build-stamp] Error 2
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue

Any suggestions?
Jeremy

---

### Post by unique on 2006-06-20
[QUOTE=xXx 0wn3d xXx]Ck, performance patches, can be found [ here. ](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/) Patches for upgrading your kernel can be found on the kernel.org homepage.[/QUOTE]
[B]
xXx 0wn3d xXx[/B] So do you always need to use the Ck patch with the same version of the kernel?  Like 2.6.17 kernel you would want to use the patch-2.6.17-ck1.bz2?

Cause I am running the 2.6.17 without the patch-2.6.17-ck1.bz2  and all seems very well.

---

### Post by mibadt on 2006-06-20
Thanks James,
I followed your suggestion and got the follwing message:
"make: *** No rule to make target `xconfig'.  Stop."
To clarify, here is the contents of my /usr/src at this stage.

Any Idea?
TIA :) 

------------my /usr/src------------
miki@Atlantis:/usr/src$ pwd
/usr/src
miki@Atlantis:/usr/src$ ls -l
total 40360
lrwxrwxrwx  1 root src        23 2006-06-21 05:31 linux -> /usr/src/linux-2.6.17.1
drwxrwxrwx 19 root root     4096 2006-06-20 17:55 linux-2.6.17.1
-rw-r--r--  1 root src  41276465 2006-06-20 17:33 linux-2.6.17.1.tar.bz2
---------------end-----------------------

---------contents of my /usr/src/linux----------------------
miki@Atlantis:/usr/src/linux$ ls -a
.     block    CREDITS        drivers     include  Kbuild  MAINTAINERS  net             scripts   usr
..    .config  crypto         fs          init     kernel  Makefile     README          security
arch  COPYING  Documentation  .gitignore  ipc      lib     mm           REPORTING-BUGS  sound
---------end-----------------------------------------------


[QUOTE=jamuir]don't do "make xconfig" as root.  root does not have permission to use the xserver (i.e. the display).

from your normal account, do this:

sudo make xconfig

-James[/QUOTE]

---

### Post by ravpaul on 2006-06-21
```
Ck, performance patches, can be found  here.  Patches for upgrading your kernel can be found on the kernel.org homepage.

```

Thanks for that. But what is the command to upgrade your kernel from an upgrade patch?

---

### Post by dcstar on 2006-06-21
[QUOTE=ravpaul]```
Ck, performance patches, can be found  here.  Patches for upgrading your kernel can be found on the kernel.org homepage.

```

Thanks for that. But what is the command to upgrade your kernel from an upgrade patch?[/QUOTE]
Refer to the "patch" command on the first post of this thread.

---

### Post by OPaul on 2006-06-22
[QUOTE=OPaul]Whenever I use this method to install a new kernel I loose the use of my Toshiba hotkeys, like display brightness. I copied the .config file over like it says  to do, so shouldn't whatever option it is that corresponds to them get checked?[/QUOTE]
Anyone? If I copy the .config file doesn't that mean all my settings from the previous kernel should be copied over?

---

### Post by tseliot on 2006-06-22
[QUOTE=OPaul]Anyone? If I copy the .config file doesn't that mean all my settings from the previous kernel should be copied over?[/QUOTE]
You also have to get to the folder with the kernel source and type:
```
sudo make oldconfig
```

just to be sure

---

### Post by OPaul on 2006-06-22
[QUOTE=tseliot]You also have to get to the folder with the kernel source and type:
```
sudo make oldconfig
```

just to be sure[/QUOTE]
Is that the old kernel source or the new one?

Also, what does a dot mean in the xconfig program? I understand a checkmark and an empty box, but I don't get the dot.

---

### Post by ashrack on 2006-06-22
[QUOTE=jeremytaylor]I can't seem to get the fglrx module to compile. I've installed the source with 
sudo apt-get install fglrx-kernel-source
as suggested in the guide but when i make the kernel package i get
IGNORE_CC_MISMATCH=1 CC="gcc-4.0"  /usr/bin/make -C /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x -f Makefile SYSSRC=/usr/src/linux   KBUILD_PARAMS="-C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x"
make[3]: Entering directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[3]: Makefile: No such file or directory
make[3]: *** No rule to make target `Makefile'.  Stop.
make[3]: Leaving directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[2]: *** [build-stamp] Error 2
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue

Any suggestions?
Jeremy[/QUOTE]
theres a bug in the FGLRX, check out this bug report and also report your bug. Hopefully the DEV will fix this error since its more than 2month old now.
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/45563](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/45563)

---

### Post by ashrack on 2006-06-22
[QUOTE=OPaul]Whenever I use this method to install a new kernel I loose the use of my Toshiba hotkeys, like display brightness. I copied the .config file over like it says  to do, so shouldn't whatever option it is that corresponds to them get checked?[/QUOTE]
Well it does. But in the UBUNTU kernels there are also a lot of custom patchs applied which are not in the VANILA kernel U are trying to compile. And its just possible that the support for TOSHIBA isnt in the default VANILA kernel.
U could verify this with the 'make oldconfig' command.

---

### Post by ashrack on 2006-06-22
[QUOTE=OPaul]Also, what does a dot mean in the xconfig program? I understand a checkmark and an empty box, but I don't get the dot.[/QUOTE]
The dot means that it will compile as a module.

---

### Post by PoisoN2003 on 2006-06-22
which one do i install sincei get 2 deb files 1 image the other header?

well iget things like these from time to time while i compile is it bad?

```
fs/isofs/namei.c: In function &#8216;isofs_lookup&#8217;:
fs/isofs/namei.c:162: warning: &#8216;offset&#8217; may be used uninitialized in this function
fs/isofs/namei.c:162: warning: &#8216;block&#8217; may be used uninitialized in this function

```

---

### Post by tseliot on 2006-06-22
[QUOTE=OPaul]Is that the old kernel source or the new one?[/QUOTE]
You need to copy the .config file to the folder containing the new source. From there you need to use the command I suggested

---

### Post by haani on 2006-06-22
does anyone know how to install drivers for intel ipw 3945 wireless in the new compiled kernel 2.6.17??

---

### Post by PoisoN2003 on 2006-06-22
Is this supposed to be or something is wrong 

```
find . -path './scripts/*' -prune -o -path './Documentation/*' -prune -o       \                -path './debian/*'  -prune -o -type f                          \                \( -name Makefile -o -name 'Kconfig*' \) -print |              \                  cpio -pd --preserve-modification-time debian/tmp-headers/usr/src/kernel-headers-2.6.16-ck12;
cpio: debian/tmp-headers/usr/src/kernel-headers-2.6.16-ck12/./Makefile not created: newer or same age version exists
cpio: debian/tmp-headers/usr/src/kernel-headers-2.6.16-ck12/./arch/i386/Makefile not created: newer or same age version exists
cpio: debian/tmp-headers/usr/src/kernel-headers-2.6.16-ck12/./include/asm-cris/arch-v32/hwregs/Makefile not created: newer or same age version exists
cpio: debian/tmp-headers/usr/src/kernel-headers-2.6.16-ck12/./include/asm-cris/arch-v32/hwregs/iop/Makefile not created: newer or same age version exists
5097 blocks
test ! -e arch/i386/kernel/asm-offsets.s ||             \
          install -p    -o root -g root -m 644 arch/i386/kernel/asm-offsets.s  \                debian/tmp-headers/usr/src/kernel-headers-2.6.16-ck12/arch/i386/kernel/asm-offsets.s
install -p    -o root -g root -m 644 .config            debian/tmp-headers/usr/src/kernel-headers-2.6.16-ck12/.config
echo k7                    > debian/tmp-headers/usr/src/kernel-headers-2.6.16-ck12/kernel-headers.revision
dpkg-gencontrol -DArchitecture=i386 -isp \
                        -pkernel-headers-2.6.16-ck12 -Pdebian/tmp-headers/
chown -R root:root debian/tmp-headers
chmod -R og=rX debian/tmp-headers
dpkg --build debian/tmp-headers ..
dpkg-deb: building package `kernel-headers-2.6.16-ck12' in `../kernel-headers-2.6.16-ck12_k7_i386.deb'.
rm -rf debian/tmp-headers
echo done >  stamp-headers
make[1]: Leaving directory `/usr/src/linux-2.6.16ck12'
for module in  ; do                       \
          if test -d  $module; then                                \
            (cd $module;                                          \
              if ./debian/rules KVERS="2.6.16-ck12" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="i386"                  \
                             KDREV="k7" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \                      echo "in fact being built as root, please file a bug ";  \                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
                 read ans;                                        \
              fi;                                                   \
             );                                                    \
          else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
          fi;                                                       \
        done
root@ubuntu:/usr/src/linux#


```

---

### Post by ashrack on 2006-06-22
[QUOTE=PoisoN2003]which one do i install sincei get 2 deb files 1 image the other header?[/QUOTE]
Both of them!

> well iget things like these from time to time while i compile is it bad?

```
fs/isofs/namei.c: In function ‘isofs_lookup’:
fs/isofs/namei.c:162: warning: ‘offset’ may be used uninitialized in this function
fs/isofs/namei.c:162: warning: ‘block’ may be used uninitialized in this function

```

its perfectly normal.

---

### Post by xXx 0wn3d xXx on 2006-06-22
[QUOTE=ashrack]Both of them!


its perfectly normal.[/QUOTE]
Yes, install both of them. It would be best to install the kernel_image first and then the kernel_headers second.

---

### Post by PoisoN2003 on 2006-06-22
[QUOTE=xXx 0wn3d xXx]Yes, install both of them. It would be best to install the kernel_image first and then the kernel_headers second.[/QUOTE]

my last question i installed only 1 of them and when i launched the kernel teh xserver crashed so i reconfigured it but now when i try to reinstall the nvidia the next time i start the xserver crashes or sometimes it says its already installed
then when i do this 
poison@ubuntu:~$ cat /proc/driver/nvidia/agp/status
cat: /proc/driver/nvidia/agp/status: No such file or directory

as u can see it hasnt found it
so any help i got nvidia 5600 fx ultra

oh and can i still install the header while im in teh kernel? or do i have to go back to my old one and install from there?

---

### Post by OPaul on 2006-06-22
[QUOTE=ashrack]Well it does. But in the UBUNTU kernels there are also a lot of custom patchs applied which are not in the VANILA kernel U are trying to compile. And its just possible that the support for TOSHIBA isnt in the default VANILA kernel.
U could verify this with the 'make oldconfig' command.[/QUOTE]

[QUOTE=tseliot]You need to copy the .config file to the folder containing the new source. From there you need to use the command I suggested[/QUOTE]

Well I don't understand, it's still not working for some reason. Now, ACPI_TOSHBIA, which handles the hotkeys, has a dot by it (being loaded as a module), so do I need to do something special perhaps to make the module load with the new kernel?

Also, I notice this when I run dmesg. On the original Ubuntu kernel, 2.6.15-25-686,  (where the hotkeys work) I have the following.
```
[17179597.040000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[17179597.040000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[17179597.044000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[17179597.044000] toshiba_acpi: ktoshkeyd will check 2 times per second
[17179597.044000] toshiba_acpi: Dropped 0 keys from the queue on startup
```
But in 2.6.17.1 I only have this```
[4294671.487000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.18
[4294671.487000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
```

Also, the version numbers of acpi_toshiba are different. The older kernel has the newer copy.

---

### Post by kakashi on 2006-06-23
[QUOTE=R3linquish3r]K well that completely drove me away from kernal compilation....

I dont know what I messed up but when I booted into the kernel it started in Failsafe. I logged in and when I went to start X it panicked. I booted my old kernel (2.6.12 ancient!) and THAT started in failsafe but X started at least. I uninstalled the package and now everything is back to normal. Think I'll wait till Dapper is released then do a fresh install of that so I have the latest kernel.[/QUOTE]


i suggest to everyone that you first try compiling the kernels a few times on a computer thats not your main one OR like i do in a vmwar. now that vmware server is freely available it is really easy to setup a nice test environment. once your comfortable with the process do it on your main system.

---

### Post by tseliot on 2006-06-23
[QUOTE=OPaul]Also, the version numbers of acpi_toshiba are different. The older kernel has the newer copy.[/QUOTE]
Ubuntu's kernels are heavily patched and I can't help you with that.

I have backported Edgy's 32bit kernels to Dapper (I haven't uploaded them anywhere yet). The only problem is making the restricted modules. After that problem is solved maybe I can upload everything.

---

### Post by xpmaniac4ever on 2006-06-23
Kernel 2.6.17 is out. Does this howto apply to this new version as well ? Or could someone please modify it to reflect the changes in the new version ?

---

### Post by cfp999 on 2006-06-23
I was wondering about that too. My plan is to try and compile 2.6.17 + Con Kolivas' patch-2.6.17-ck1.bz2 although I have no idea what the latter does compared to Ubuntu's "native" patching. Will it be safe to assume, that I can boot a previous kernel in GRUB if something goes completely wrong?

---

### Post by xpmaniac4ever on 2006-06-23
Got this while trying to compile 2.6.17 kernel. Any ideas ?

> root@hackedbox:/usr/src/linux-2.6.17# make xconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  CHECK   qt
  HOSTCC  scripts/kconfig/conf.o
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig
qconf: cannot connect to X server
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2
root@hackedbox:/usr/src/linux-2.6.17#  

---

### Post by OPaul on 2006-06-23
[QUOTE=xpmaniac4ever]Kernel 2.6.17 is out. Does this howto apply to this new version as well ? Or could someone please modify it to reflect the changes in the new version ?[/QUOTE]
Yea, you can use this guide for 2.6.17 to. Just make sure you get the ck1 for 2.6.17, and not 2.6.16.

[QUOTE=cfp999]I was wondering about that too. My plan is to try and compile 2.6.17 + Con Kolivas' patch-2.6.17-ck1.bz2 although I have no idea what the latter does compared to Ubuntu's "native" patching. Will it be safe to assume, that I can boot a previous kernel in GRUB if something goes completely wrong?[/QUOTE]
A list of ck changes can be found on his website here, [http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/) , under Description.

---

### Post by cfp999 on 2006-06-23
A list of ck changes can be found on his website here, [http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/) , under Description.[/QUOTE]

Thanks. Dont know how I could have missed that..

I have another question even though it is not intirely related to the guide in this thread: Does the original Ubuntu kernel use a "monolithic" or "modular" design? (hope I spelled that correct).

---

### Post by kurisutofaa on 2006-06-23
Thanks for the how-to. I just installed the new 2.6.17-kernel with your instructions. This seems to work just fine.

---

### Post by cfp999 on 2006-06-23
When configuring the kernel: Is it generally a good idea to set hardware specific kernel support to "Y" rather than leave them as modules if you are sure about your own hardware?

---

### Post by jeremytaylor on 2006-06-23
Hi,
just wanted to let people know that 2.6.17 fixes problems with the cd drive not being able to mount. 
jeremy

---

### Post by xXx 0wn3d xXx on 2006-06-23
**Kernel Useful/Performance Tips:**
Warning: Some of these tips may cause your kernel to not compile properly. Use them at you _own_ risk.

**S=Select**
**U=Unselect**

A "/" means that it is under the directory above.
-------------------------------------------------------------------
**General Setup:**

S:  Support for paging of anonymous memory. (swap)
-------------------------------------------------------------------
**Loadable Module Support:**

U: Module Versioning Support
U: Source checksum for all modules
--------------------------------------------------------------------
**Block Layer:**

U: Large Block Devices (Uncheck all if possible)
--------------------------------------------------------------------
**/IO Schedulers:**

U: Anticipatory I/O Schedulers
U: Deadline I/O Schedulers
---------------------------------------------------------------------
**Processor type and features:**

U: Symmetric processing support (Unless your processor(s) support(s) it)
U: Generic x86 support
S: HPET Timer Support
S: Voluntary Kernel Preemption (Desktop) (Under Preemption Model)
S: Local APCI support on uniprocessors
S: IO-APCI support on uniprocessors (Under Local APCI support)
S: Off (Under High Memory support if you have under 1 gig of ram)
S: Sparse Memory (Under Memory Model, some computers will not have this option)
S: MTRR support
S: Use register arguements
S: Enable seccomp to compute untrusted bytecode
S: 1000hz (Under Timer Frequency)
--------------------------------------------------------------------
**/Firmware Drivers:**

U: Anything that you don't need.
--------------------------------------------------------------------
**Bus Options:**

S: Message Signaled Interrupts (MSI and MSI-X) (PCI_MSI) 
--------------------------------------------------------------------
**Network:**

U: Anything/Everything in Amateur Radio, IrDA, and Bluetooth if you don't need it.
--------------------------------------------------------------------
**/Network Options:**

S: Packet socket:mmapped IO 
--------------------------------------------------------------------
**Device Drivers/ ATA/ATAP/MFR/RLL support:**

S: Use PCI DMA by Default
U: IDE Taskfile Acess
--------------------------------------------------------------------
**/Raid and LVM**

U: Unselect if you do not need it.
--------------------------------------------------------------------
**/I2O support:**

U: Unselect if you do not need it. Most people do not.
--------------------------------------------------------------------
**Network Device support:** (Note: Most people do not require these options. Do not unselect them if you do)

U: EQL support
U: Universial TUN/TAP device driver support
U: FDDI Driver support
U: HIPPI driver support
U: SLIP (serial line) support
U: Traffic Support
U: Network console loggin support
---------------------------------------------------------------------
**/ARCnet support:**

U: Unselect if you do not require/need it.
---------------------------------------------------------------------
**/Ethernet Support (1000 MB):**

U: Uselect the cards that you don't have. 
---------------------------------------------------------------------
**/Ethernet Support (10000 MB):**

U: Unselect what you do not need.
---------------------------------------------------------------------
**/Token Ring Devices:**

U: Unselect if you are not connected to a Token ring network.
---------------------------------------------------------------------
**/WAN interfaces support:**
 
U: Unselect the some cards/the whole thing if you do not need it.
---------------------------------------------------------------------
**ISDN subsystem:**

U: ISDN support (If you do not require it)
---------------------------------------------------------------------
**Input device support:**

U: Touchscreen interface
U Touchscreens (Under the TouchScreens subcatergory)
---------------------------------------------------------------------
**Character Devices:**

U: Any video cards that you do not need.
---------------------------------------------------------------------
**/Watchdog cards:**

U: Watch Dog Timer support
---------------------------------------------------------------------
**Misc Devices:**

U: Device driver for IBM/RSA service drivers
---------------------------------------------------------------------
**Video Capture Adapters:**

U: Unselect anything that you don't need.
---------------------------------------------------------------------
**/Radio Adapters:**

U: Unselect anything that you don't need.
---------------------------------------------------------------------
**/Digital Video Broadcasting Devices:**

U: DVB for Linux
---------------------------------------------------------------------
**Graphics support:**

U: Unselect any graphics cards that you don't have.
---------------------------------------------------------------------
**/Logo Configuration:**

S: Bootup Logo (and anything under it)
---------------------------------------------------------------------
**File systems:**

U: Unselect any file systems that you are NOT going to use. (Minix, ROM, Quota, etc.)
----------------------------------------------------------------------
**/DOS/FAT/NT Filesystems:**

S: NTFS write support
----------------------------------------------------------------------
**/Network File Systems:**

U: NFS file system support
U: NFS server support
U: NCP file system support
U: Coda file system support
U: Andrew file system support
U: Plan 9 resource sharing support
-----------------------------------------------------------------------
**/Partition Types:**

U: Advanced partition selection
-----------------------------------------------------------------------
**/Native Language Support:**

U: Unselect all but your native language:
S: Codepage 437 (United States. Canada), ACII (United States), NLS UTF-8 (select these for the us language)
-----------------------------------------------------------------------
**Instrumentation Support:**

U: Profiling Support
U: Kprobes
------------------------------------------------------------------------
**Kernel Hacking:**

U: Show timing information on printks
U: Magic SysRq Key
U: Kernel Hacking
U: Debug Filesustem
U: Compile the kernel with frame unwind information
-------------------------------------------------------------------------
 That is it :D Hope that helps. Can I have some feedback on this ? And starting tomarrow, I will be gone for 2 weeks, so I can't update the thread.

---

### Post by Centaur5 on 2006-06-24
Did you try compiling the driver from [http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net) and if so did you get an error?  I successfully compiled and installed the ieee80211 package but when I tried to build the newest driver 1.0.5 it resulted in the following:

make -C /lib/modules/2.6.17/build M=/home/fishman/wireless/ipw3945-1.0.5 modulesmake[1]: Entering directory `/usr/src/linux-2.6.17'
  CC [M]  /home/fishman/wireless/ipw3945-1.0.5/ipw3945.o
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c: In function ‘ipw_send_associate’:
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c:4292: error: too few arguments to function ‘ieee80211_tx_frame’
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c: In function ‘ipw_bg_daemon_cmd’:/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c:4765: error: too few arguments to function ‘ieee80211_tx_frame’
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c: In function ‘ipw_auth_work’:
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c:9381: error: too few arguments to function ‘ieee80211_tx_frame’
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c:9426: error: too few arguments to function ‘ieee80211_tx_frame’
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c: In function ‘ipw_handle_probe_request’:
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c:9496: error: too few arguments to function ‘ieee80211_tx_frame’
make[2]: *** [/home/fishman/wireless/ipw3945-1.0.5/ipw3945.o] Error 1
make[1]: *** [_module_/home/fishman/wireless/ipw3945-1.0.5] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17'
make: *** [modules] Error 2

Let me know if you get the same result when trying to compile that driver.

---

### Post by haani on 2006-06-24
[QUOTE=Centaur5]Did you try compiling the driver from [http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net) and if so did you get an error?  I successfully compiled and installed the ieee80211 package but when I tried to build the newest driver 1.0.5 it resulted in the following:

make -C /lib/modules/2.6.17/build M=/home/fishman/wireless/ipw3945-1.0.5 modulesmake[1]: Entering directory `/usr/src/linux-2.6.17'
  CC [M]  /home/fishman/wireless/ipw3945-1.0.5/ipw3945.o
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c: In function ‘ipw_send_associate’:
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c:4292: error: too few arguments to function ‘ieee80211_tx_frame’
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c: In function ‘ipw_bg_daemon_cmd’:/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c:4765: error: too few arguments to function ‘ieee80211_tx_frame’
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c: In function ‘ipw_auth_work’:
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c:9381: error: too few arguments to function ‘ieee80211_tx_frame’
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c:9426: error: too few arguments to function ‘ieee80211_tx_frame’
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c: In function ‘ipw_handle_probe_request’:
/home/fishman/wireless/ipw3945-1.0.5/ipw3945.c:9496: error: too few arguments to function ‘ieee80211_tx_frame’
make[2]: *** [/home/fishman/wireless/ipw3945-1.0.5/ipw3945.o] Error 1
make[1]: *** [_module_/home/fishman/wireless/ipw3945-1.0.5] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17'
make: *** [modules] Error 2

Let me know if you get the same result when trying to compile that driver.[/QUOTE]

same error for me aswell but when i try it with ndiswrapper using windows drivers the kernel crashes

---

### Post by dcstar on 2006-06-25
[QUOTE=cfp999]
.......
Will it be safe to assume, that I can boot a previous kernel in GRUB if something goes completely wrong?[/QUOTE]
Yes, you can boot from as many kernels that you leave installed on your system.

It would be good policy to always have the latest "official" Ubuntu kernel installed, and then you may also want to have one previous (working) version of the CK kernel installed as well as the latest one you are currently playing with.

If things go bad with a current kernel, simply reboot and select one of the known good ones you have in your list - and when you are satisfied that a kernel is stable (and performs as you require) then you can remove the previous version(s).

---

### Post by Centaur5 on 2006-06-25
[QUOTE=haani]same error for me aswell but when i try it with ndiswrapper using windows drivers the kernel crashes[/QUOTE]

That's good to know, I'm not going to try ndiswrapper then.  I was wondering what sound card you have on your laptop?  The reason I wanted 2.6.17 was to get the headphone jack working (which it did) but I might just have to boot 2 different kernels depending on whether I need wireless or headphones.  :)  I haven't had any luck finding anything else on our problem with that kernel and our wireless but I will keep looking.

---

### Post by haani on 2006-06-25
[QUOTE=Centaur5]That's good to know, I'm not going to try ndiswrapper then.  I was wondering what sound card you have on your laptop?  The reason I wanted 2.6.17 was to get the headphone jack working (which it did) but I might just have to boot 2 different kernels depending on whether I need wireless or headphones.  :)  I haven't had any luck finding anything else on our problem with that kernel and our wireless but I will keep looking.[/QUOTE]

i have realtek ALC883 HD soundcard which works fine in the new kernel.

---

### Post by mlind on 2006-06-25
nice guide! I'm not sure if this has been discussed before, but you should add your
useraccount to group called "src", which allows r/w access to /usr/src folder.
This way no sudoing is required, which is better.

User must relogin, so that new settings work. This can be done just by using **su** on current terminal session.
```

su $USER

```

And maybe include "make oldconfig" before making xconfig.

---

### Post by isotonic on 2006-06-26
I followed this howto for the 2.6.17 kernel, stripped off the unwanted options, compiled and rebooted...

...Not only did it boot up much quicker, the whole OS is faster, particularly internet browsing!

I got rid of a ton of network and peripheral options and the new, smaller kernel is doing the business (only faster).

Probably the most useful howto i've read on this forum so far. Thanks OP!!!

Should be part of any firefox speed up howto!!! :p

---

### Post by lodp on 2006-06-26
[QUOTE=haani]i have realtek ALC883 HD soundcard which works fine in the new kernel.[/QUOTE]

Do you mean the 2.6.16 or the 2.6.17 one? I've got an Intel-HDA ALC883 and it didn't work with the 2.6.17 kernel (and the 2.6.15-25 one). Never tried 2.6.16 though.

I started a thread on my nasty ALC883 sound problem here: [No sound w/ HDA-Intel Realtek ALC883 - tried *everything* ]("http://ubuntuforums.org/showthread.php?t=202555")

Also, wireless (ip2200) didn't work with the new kernel. didn't care to do any tinkering  to get it to work, though. might have been able to.

---

### Post by haani on 2006-06-26
[QUOTE=lodp]Do you mean the 2.6.16 or the 2.6.17 one? I've got an Intel-HDA ALC883 and it didn't work with the 2.6.17 kernel (and the 2.6.15-25 one). Never tried 2.6.16 though.

I started a thread on my nasty ALC883 sound problem here: [No sound w/ HDA-Intel Realtek ALC883 - tried *everything* ]("http://ubuntuforums.org/showthread.php?t=202555")

Also, wireless (ip2200) didn't work with the new kernel. didn't care to do any tinkering  to get it to work, though. might have been able to.[/QUOTE]

i mean the new kernel 2.6.17 it does work with it!!

---

### Post by lodp on 2006-06-26
[QUOTE=haani]i mean the new kernel 2.6.17 it does work with it!![/QUOTE]

that's strange. i compiled the thing and it didn't change anything with regards to my sound problem -- would you care to look at the thread i pointed out above, and tell me what you think?

2.6.17 has alsa 1.0.11rc4 built into it, which supposedly supports the ALC883 chipset, so it's really strange it doesn't work.

---

### Post by vseehua on 2006-06-26
hmm... i had compiled my third kernel and all three times the wireless card stops working... any ideas? mine is a ipw2200...

tried compiling from the source gotten from sourceforge.net but that also failed... the wireless modules was working just fine in the ubuntu kernel...

---

### Post by kcallis on 2006-06-27
[QUOTE=xXx 0wn3d xXx]I just finished compiling the newest 2.6.16 kernel from kernel.org and I am getting much better performance. In what follows, I will show you how to compile and configure the latest kernel. You do not need to use the 2.6.16 kernel but it is the first kernel of the release kernel and performance patches are only made for these releases. (**ex**: 2.6.16, 2.6.17 _NOT_ 2.6.16.20) Feel free to compile a kernel besides the first release cycle kernel. You do _not_ need the patch and you can configure the kernel for maxium speed in xconfig. A tutorial to optimize the kernel you are building can be found [ **here**. ](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507)
 
Before you begin, you will need to get a kernel
Download the 2.6.16 kernel and it's performance patch:[ The 2.6.16 kernel ](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.tar.bz2)
[ Latest Kernel Patch ](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.16/2.6.16-ck12/patch-2.6.16-ck12.bz2) Don't apply the patch if you are compiling a kernel other then 2.6.16 otherwise the kernel will _not_ compile.

Check out kernel.org for the latest stable/release canidate kernel.

**1.** [COLOR="Blue"] Install needed utilities to configure the kernel[/COLOR]



**2.**[COLOR="BLUE"] Now we are going to move the kernel and unpack it.[/COLOR]



**3.**[COLOR="Blue"] Now we are going to move to /usr/src[/COLOR]



**4.**[COLOR="Blue"] Now unpack it:[/COLOR]



**5.**[COLOR="Blue"] Rename the folder:[/COLOR] ONLY needed for 2.6.16 kernel ! You don't need to do this.



**6.**[COLOR="Blue"] Now we are going to remove the link to the linux directory:[/COLOR]



**7.**[COLOR="Blue"] Make a new link to the new kernel:[/COLOR]



**8.**[COLOR="Blue"] Move to the Linux directory:[/COLOR]



**9.**[COLOR="Blue"] Make yourself root:[/COLOR]



**10.**[COLOR="Blue"] Apply the performance patch: [/COLOR] **Don't use if you are not patching the 2.6.16 kernel !**



**11.**[COLOR="Blue"] Now we are going to import your current kernel configuration:[/COLOR]



**12.**[COLOR="Blue"] Now import it: Make sure to replace the kernel version in this following command from the one from uname -r.[/COLOR]



**13.**[COLOR="Blue"]Configure the kernel:[/COLOR]



Here are some performance tips from [ this thread. ](http://ubuntuforums.org/showthread.php?t=84174&highlight=compile+kernels)



**Note**: Not all the options will be the same in newer kernels.

**14.**[COLOR="Blue"] Let's build the kernel: Make sure that you are in /usr/src/linux with full root access. Make sure that you are. This will build a debian file that you can install.[/COLOR]

Now, in terminal do the following:


**Note:** You can replace "ck12" with anything you want. Like "k7" or "686."
**15.**[COLOR="Blue"] Install the .deb fine in /usr/src. In terminal do[/COLOR] 



[COLOR="Blue"] Now reboot and you will have a much faster system ![/COLOR]
-------------------------------------------------------------------------

How I learned to do this:
[ 2.6.14 Vanilla Kernel ](http://ubuntuforums.org/showthread.php?t=84174&highlight=compile+kernels) I based my tutorial on this thread. Thank you for writing this tutorial RubenGonc !

And I also learned some stuff from [ this thread ](http://ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel)
-------------------------------------------------------------------------
[COLOR="Red"]_**Troubleshooting:**_[/COLOR]

**Q**: My Wifi Doesn't work !

**A**:To get wifi working, compile the new ndiswrapper from source. Follow the [ tutorial. ](http://ubuntuforums.org/showthread.php?t=104539&highlight=compile+ndiswrapper+source)

**Q**: When I reboot I get Grub Error 22 ! WTF ???

**A**: You may have missed a step or messed something up. When it says Grub Loading..... press esc and you will be able to boot  with another kernel. Then you should go into synaptic and uninstall the broken kernel and then reompile it.
**--------------------------------------------------------------------------------**
**Q**: How can I get fglrx and DRI working on my new kernel ? 

**A**: Type this in terminal:



Reboot and if that does not work, make sure fglrx is in the Driver section.
**---------------------------------------------------------------------------------**
**Q**: I need kernel headers for my custom kernel.

**A**: I updated the howto and edited the last step to build a kernel image, kernel module image, and kernel headers. Thank you to tseliot for his kernel thread because I found the command there. You can view the thread [ here. ](http://ubuntuforums.org/showthread.php?t=85064&highlight=custom+compile)
**------------------------------------------------------------------------------------**
**Q**: I want to optimize my kernel ! What do I select ???

**A**: I just wrote [ this tutorial ](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507) on how to configure your kernel for enhanced performance. I hope [ it ](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507) helps.
**----------------------------------------------------------------------------------------**
**Q**: Why did you write this tutorial ?
**A**: I wrote this tutorial to help give back to the Ubuntu community. I've had such a good expericence with ubuntu that I want to help others. This community is great :)[/QUOTE]
That was a great tutorial! I do have a question about the booting process. I am using grub to boot my various generic kernels along with booting Windows XP. Using the method above, will that impair my ability to boot in XP when necessary? If so, what can I do to make a image that will interface will interface with grub so that I can get to all of my images, including Windows XP.

---

### Post by bocmaxima on 2006-06-27
I tried this, but when I put in the first command to install the stuff I got
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
  libqt3-mt-dev: Depends: xlibs-static-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxext-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxrandr-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: x-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libsm-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxmu-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libice-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libx11-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxt-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxrender-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxinerama-dev but it is not going to be installed
                 Depends: libxi-dev but it is not going to be installed
                 Depends: libmng-dev (>= 1.0.3) but it is not going to be installed
                 Depends: libpng12-0-dev
                 Depends: libjpeg62-dev but it is not going to be installed
                 Depends: zlib1g-dev but it is not going to be installed
                 Depends: libfreetype6-dev but it is not going to be installed
                 Depends: libc6-dev but it is not going to be installed
                 Depends: libqt3-mt (= 3:3.3.4-8ubuntu5) but 3:3.3.6-1ubuntu6 is to be installed
                 Depends: libgl1-mesa-dev but it is not going to be installed or                          libgl-dev
                 Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
                 Depends: libxft-dev but it is not going to be installed
E: Broken packages

```

Somethiing wrong on my end perhaps?

---

### Post by zolero on 2006-06-27
Yeah, bocmaxima... we have some dependencies problems there.

Go in Synaptic Package Manager/Settings/Repositories and check in all the repos, then press OK --> Refresh.

Now, open a terminal and paste in this command:

```
$ sudo apt-get install ***<put here all dependancies separated by space>***
```

After this recompile the kernel. Now it must executing well.

That's all. Cheers.

---

### Post by bocmaxima on 2006-06-27
[QUOTE=zolero]Yeah, bocmaxima... we have some dependencies problems there.

Go in Synaptic Package Manager/Settings/Repositories and check in all the repos, then press OK --> Refresh.

Now, open a terminal and paste in this command:

```
$ sudo apt-get install ***<put here all dependancies separated by space>***
```

After this recompile the kernel. Now it must executing well.

That's all. Cheers.[/QUOTE]

I already had all the repos checked. :( When I tried doing it one by one, it basically gave the same error.


I typed in: sudo apt-get install gcc

and got:
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gcc: Depends: cpp (>= 4:4.0.1-3) but it is not going to be installed
       Depends: gcc-4.0 (>= 4.0.1-2) but it is not going to be installed
E: Broken packages

```

---

### Post by Blade1357 on 2006-06-27
well i have did all an well the boot screen or kernnel looks the same as be4 but in my grub i boot with ht enew kernnel but it looks the same as the old one. why?

---

### Post by Centaur5 on 2006-06-27
[QUOTE=haani]does anyone know how to install drivers for intel ipw 3945 wireless in the new compiled kernel 2.6.17??[/QUOTE]

Just wanted to let you know that they added an updated driver yesterday on ipw3945.sourceforge.net which worked fine for me.  I installed the newest ieee80211 and afterwards I was able to compile the newest driver so now my wireless is up and running again.  In order to compile the driver though I did have to type "make IEEE80211_IGNORE_DUPLICATE=y" but it still went well if it tells you to do that as well.

---

### Post by MrSmith on 2006-06-27
This is my first post here so I hope I'm in the right place and all.

I have been following this thread and decided to give installing a new kernel a try. I am attempting the 2.6.17.1 kernel. So far it has been a lesson in frustration ](*,)  but I am hanging in there.

The first time I tried the install all seemed to go well but it didn't work. So I deleted all the source and started over. Now when I get to the point of installing the .deb packages I get the following:

Setting up kernel-image-2.6.17.1 (k7) ...
/initrd.img does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
/vmlinuz does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17.1
Found kernel: /boot/vmlinuz-2.6.15-25-k7
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

I don't remember these messages the first time I did the install. Are these normal or is there something I have missed or messed up?

The last attempt by the way was sort of successful. I was able to boot into the new kernel and gnome came up. Sound worked but my network connection and internet was dead. I think I must have unchecked something wrong when i was configuring the kernel.

I am going to give it one more try and only make the changes in the guide found elsewhere in the forums.

Anyway, thanks for any and all replies.

MrSmith

---

### Post by bittdude on 2006-06-28
I wanted to let everyone know that I solved my ATI driver problem and got the module to compile successfully with the vanilla kernel :) Took me a while but everything works great now.  

The problem with me was there was a file missing from the kernel headers which caused the module compile to fail.  The file missing is Makefile.cpu and it's supposed to be in 

```
/usr/src/*YOUR KERNEL HEADERS*/arch/i386
```

For me the headers directory was "/usr/src/kernel-headers-2.6.16-ck12" so it should be something similar for you.

The fix is quite simple just go to that directory and type

```
sudo touch Makefile.cpu
```

Then compile the module and it should work now.  I hope this helps for anyone who is having difficulty with installing the ATI Drivers.

Also thanks xXx 0wn3d xXx for the great HowTo, my system is quite a bit faster now with the new kernel :D .

---

### Post by bocmaxima on 2006-06-28
[QUOTE=zolero]Yeah, bocmaxima... we have some dependencies problems there.

Go in Synaptic Package Manager/Settings/Repositories and check in all the repos, then press OK --> Refresh.

Now, open a terminal and paste in this command:

```
$ sudo apt-get install ***<put here all dependancies separated by space>***
```
[/QUOTE]

After trying a bunch of different things I got everything but libqt3-mt-dev to install.

I get this

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: xlibs-static-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxext-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxrandr-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: x-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libsm-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxmu-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libice-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libx11-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxt-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
                 Depends: libxrender-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxinerama-dev but it is not going to be installed
                 Depends: libxi-dev but it is not going to be installed
                 Depends: libmng-dev (>= 1.0.3) but it is not going to be installed
                 Depends: libpng12-0-dev
                 Depends: libjpeg62-dev but it is not going to be installed
                 Depends: zlib1g-dev but it is not going to be installed
                 Depends: libfreetype6-dev but it is not going to be installed
                 Depends: libqt3-mt (= 3:3.3.4-8ubuntu5) but 3:3.3.6-1ubuntu6 is to be installed
                 Depends: libgl1-mesa-dev but it is not going to be installed or                          libgl-dev
                 Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
                 Depends: libxft-dev but it is not going to be installed
E: Broken packages

```

Any suggestions? I trued installing off the Dapper CD as well as enabled everything.

No kernel for me :(

---

### Post by haani on 2006-06-28
my ATI x1400 doesnt doesnt work with new compiled kernel 2.6.17 aswell anyone able to get ATI X Series card to work with new kernel!!!

---

### Post by MrSmith on 2006-06-28
Ok, I have the 2.6.17.1 kernel installed now and it seems to be working. I managed to get the Nvidia drivers working but I'm not sure how I did it. I installed the package from the Nvidia website but that didn't work. It did however patch the kernel I believe and then I installed the nvidia-glx from the repositories and it is working. Anyway I think this is what happened.

My question now is how do I get the bootup splash screen to work again. After installing the new kernel the boot screen goes to black until the login screen comes up. For now I have "nosplash" in grub and see the text bootup. I would like to get the graphical boot splash back if possible.

I have searched the forums but haven't found anything that tells me this information.

Thanks,
MrSmith

---

### Post by DDM on 2006-06-28
For some reason, doing a "sudo apt-get install fglrx-kernel-source" doesn't work for me. I get a gzip file in /usr/src, and that's about it it seems. I tried to install them with this HOWTO: [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910) which fails during "sudo module-assistant build,install fglrx"

Has anybody else had this problem?

---

### Post by nismohasan on 2006-07-03
just a question about patches like (archck, ck, beyond) 

is it ok to use the patch against 2.6.17.3 or do i have to patch it against 2.6.17 only?

and to be more specific is it ok to use 2.6.17-beyond1.1 ([http://iphitus.loudas.com/archck.php](http://iphitus.loudas.com/archck.php)) to patch a 2.6.17.3 kernel or should i wait for them to update it again?

also, after i complile a kernal i dont see my hard disks on my desktop, if i boot into an older kernel its there, there ntfs partitions and i have enabled ntfs support. any idea why? cheers

---

### Post by l0c0dantes on 2006-07-03
Hi there, whenever I complie a kernel by follwing this guide, It will not let me mount my Second harddrive, is there something I need to do to get that to work?

---

### Post by [Yatta] on 2006-07-04
[QUOTE=l0c0dantes]Hi there, whenever I complie a kernel by follwing this guide, It will not let me mount my Second harddrive, is there something I need to do to get that to work?[/QUOTE]
What kind of drive is ur 2nd  HD?? IDE SATA what??

---

### Post by AliBi on 2006-07-04
[QUOTE=MrSmith]Ok, I have the 2.6.17.1 kernel installed now and it seems to be working. I managed to get the Nvidia drivers working but I'm not sure how I did it. I installed the package from the Nvidia website but that didn't work. It did however patch the kernel I believe and then I installed the nvidia-glx from the repositories and it is working. Anyway I think this is what happened.

My question now is how do I get the bootup splash screen to work again. After installing the new kernel the boot screen goes to black until the login screen comes up. For now I have "nosplash" in grub and see the text bootup. I would like to get the graphical boot splash back if possible.

I have searched the forums but haven't found anything that tells me this information.

Thanks,
MrSmith[/QUOTE]
i have the exact same problem with the 2.6.16 kernel. first i did the tutorial and deselected in the config some stuff more what i was fairly sure i dont need. when the kernel started booting in black i tought i had made some mistakes in deselecting all that other stuff. BUT!
i recompiled the 2.6.16 kernel with the standard kernel config of my running 2.6.15-25-686 (ubuntu repository) and i ran in the same problem again. black screen till login.
one other annoying thing is, that i have to reinstall nvidia drivers and from what i have read in this theard seems to me that this wouldnt be a pleasure to do.
i think i stop here trying to get the latest kernel, i just want to get rid of some modules which i will never be using and maybe i can get some increase in perfomance there too. will see ^^

[COLOR="Red"]EDIT:[/COLOR] i finished now "testing" the 2.6.15-7 kernel sources available over the repository (with ubuntu patches). same problem there black screen.
btw i see now, that i have to reinstall the nvidia drivers with every new kernel. is it possible to compile new drivers with the kernel? i can vaguely remember that it was possible with ubuntu 5.04 and 5.10.

i hope someone can help me/us with this problem. the problem with the black boot up is in every kernel i m trying to compile and still with a standard config from a perfectly runnig kernel.
some ideas what can i try next?

---

### Post by [Yatta] on 2006-07-04
I had the same problem wiht he black screen during boot up.. BUT then a few post later in this same thread.... i saw: 
> Originally Posted by dpicker
To get usplash you need to make sure you enable this in the config:

Graphics support:
-VGA 16-color graphics support - module (m)
-VESA VGA graphics support - build in kernel (y)

Console display driver support:
-VGA text console and Video mode selection support- build in kernel (y)
-MDA text console-module (m)
-Framebuffer Console and Framebuffer Console Rotation support-build in kernel (y)

Not sure how to change from "m" to "y" and vice versa in xconfig so I opened the .config file in gedit and checked it manually.
And it worked.....
Look through ALLL your config I removed ALOT of modules I know I would never use on this machine.

---

### Post by nix4me on 2006-07-04
I have successfully compiled the 2.6.17-3 kernel and I have one question.

What is the difference between patching the 2.6.17 and just installing the 2.6.17-3.

nix4me

---

### Post by Cris987 on 2006-07-05
I followed the guide to install kernel 2.6.17, but when I boot it the following message is displayed:

"Failed to start the X server...xconf...module nvidia not found...GDM will now be disabled."

I believe this is because I had installed the latest Nvidia driver; how can i fix this? Thanks!

---

### Post by tseliot on 2006-07-05
[QUOTE=Cris987]I followed the guide to install kernel 2.6.17, but when I boot it the following message is displayed:

"Failed to start the X server...xconf...module nvidia not found...GDM will now be disabled."

I believe this is because I had installed the latest Nvidia driver; how can i fix this? Thanks![/QUOTE]
Try this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

---

### Post by Brando569 on 2006-07-05
[QUOTE=nix4me]I have successfully compiled the 2.6.17-3 kernel and I have one question.

What is the difference between patching the 2.6.17 and just installing the 2.6.17-3.

nix4me[/QUOTE]

the latter is a patched kernel, i figured that out when i tried to patch a .16-20 kernel and the patchset kept saying that so and so file had already been patched and should it continue. id say d/l the original kernel and get a patchset, or if u wanna be on the bleeding edge get the newest patched kernel with a patchset and skip over the already patched files

---

### Post by Cris987 on 2006-07-05
[QUOTE=tseliot]Try this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)[/QUOTE]

Thanks!

Okay, I originally installed my Nvidia by method 1, which only works with kernels available in the repositories. So I decided to just uninstall the driver. And kernel 2.6.17 works like a charm now. My question is...should I install my driver using Method 2 now - which requires the removal of "restricted modules" that are supposedly required for wireless cards (according to the site anyways)  ( I'm using a wireless card)  ?

---

### Post by d3x7r0 on 2006-07-05
[QUOTE=bittdude]I wanted to let everyone know that I solved my ATI driver problem and got the module to compile successfully with the vanilla kernel :) Took me a while but everything works great now.  

The problem with me was there was a file missing from the kernel headers which caused the module compile to fail.  The file missing is Makefile.cpu and it's supposed to be in 

```
/usr/src/*YOUR KERNEL HEADERS*/arch/i386
```

For me the headers directory was "/usr/src/kernel-headers-2.6.16-ck12" so it should be something similar for you.

The fix is quite simple just go to that directory and type

```
sudo touch Makefile.cpu
```

Then compile the module and it should work now.  I hope this helps for anyone who is having difficulty with installing the ATI Drivers.

Also thanks xXx 0wn3d xXx for the great HowTo, my system is quite a bit faster now with the new kernel :D .[/QUOTE]

To me sort of works but then it gives another error: 
```
gcc: scripts/Makefile.lib.c: Arquivo ou diretório não encontrado
gcc: sem arquivos de entrada
make[2]: ** [scripts/Makefile.lib.o] Erro 1
make[1]: ** [_module_/usr/src/modules/fglrx] Erro 2
make[1]: Saindo do diretório `/usr/src/kernel-headers-2.6.17.3'
```

Translated to english it sais that it doesn't find the file... :-?

---

### Post by kimu on 2006-07-08
I've update to kernel 2.6.16 following this guide and it's everything working well but my SATA DVD and DVD+RW are not more detected from the system. 
They are under a sata controller and detected as scsi devices. 
With the previous kernel they was perfetcly dected and working (still now if I reboot with kernel 2.6.15), now the DVD+RW has become a generic scsi and the DVD a not better specified volume called BACKUP.

What have I to do to make them be detected properly again? Pls, help me :confused: 

If I try to mount it I got 
mount: special device /dev/scd0 does not exist

Bye 
Kimu

---

### Post by kimu on 2006-07-09
I've fixed my problem installing Ubuntu again (after a lot of problems that avoid me just to delete kernel 2.6.16) and compiling directly kernel 2.6.17.4.

Now everything is working well. Thanks for the guide. With the new kernel I can watch DVB-T TV with my Hauppauge HVR 1100 tv-card. :rolleyes:

---

### Post by FrancoNero on 2006-07-09
sorry for being too lazy to browse through this topic, but why can't i just install a new kernel through add/remove programs, update manager or synaptic? all this compiling stuff is part of the reasons some people are still too shy to switch to linux, i think, btw...

---

### Post by ErikTheRed on 2006-07-09
> **FrancoNero said:**
> sorry for being too lazy to browse through this topic, but why can't i just install a new kernel through add/remove programs, update manager or synaptic? all this compiling stuff is part of the reasons some people are still too shy to switch to linux, i think, btw...

Synaptic provides newer kernels to some extent. For example, Dapper uses the 2.6.15 kernel, and provides minor updates to it for example 2.6.15.23 (or whatever it is these days). But they don't provide updates from 2.6.15 to say 2.6.16 or 2.6.17.

For a novice user, having the latest and greatest kernel is not going to make huge, if even noticeable, difference. Perhaps the only time a kernel upgrade is really going to be needed by the average user is when you have very new hardware in your computer.

Ultimately, the process is really not that hard, just follow the directions and after doing it a few times it becomes very easy to do. As alienating as the command line can be, it is an extremely powerful and useful tool if you know what you are doing. Also by use of kernel patchsets, my personal favorite being [Beyond]("http://iphitus.loudas.com/beyond.html"), you can add so cool features like fbsplash. 

In my opinion it is ok to have a slightly outdated kernel, even though some would argue otherwise. But it is always fun to have the choice to experiment with the cutting edge.

---

### Post by FrancoNero on 2006-07-10
coz i just read a review of the x.17 kernel and it sounded like there were lots of hardware improvements on all sides and all that so I am wondering if there's a reason to NOT upgrade to the latest kernel at all times...

but thanks for the reply

---

### Post by polka on 2006-07-12
Install the .deb fine in /usr/src. In terminal do[/COLOR] 

In step 15 you say to install the .deb file in /usr/src. I realize the kernel-image is the kernel and must be installed. Could you explain the pros and cons of installing the other 2 .debs (module-image kernel-headers). I have configured kernel in regular debian and never created those other 2 .deb files. I am trying to understand how they work.

Thanks for your help

Jerry

---

### Post by xXx 0wn3d xXx on 2006-07-12
> **polka said:**
> Install the .deb fine in /usr/src. In terminal do[/COLOR] 

In step 15 you say to install the .deb file in /usr/src. I realize the kernel-image is the kernel and must be installed. Could you explain the pros and cons of installing the other 2 .debs (module-image kernel-headers). I have configured kernel in regular debian and never created those other 2 .deb files. I am trying to understand how they work.

Thanks for your help

Jerry
The kernel headers are can be described as this:
> Kernel-headers include the C header files for the Linux kernel. The header files define structures and constants that are needed for building most standard programs. The header files are also needed for rebuilding the kernel. -linux.maruhn.com

A module image contains additional modules and puts them into an image like a kernel image. I am not going to be around that much because I do not use Ubuntu anymore :(  That's the best way I can explain what module-image and kernel-headers. I hope I gave you a better understanding of what you wanted to know.

---

### Post by Pasa Yildirim on 2006-07-14
Dependencies... I cannot install lib-mt-qt3, needs libxcursor-dev.
I trued installing libxcursor-dev, needs libxfixes-dev...

at the end i get:

libxfixes-dev: Depends: libxfixes3 (= 1:3.0.1.2-0ubuntu3) but 1:4.0-0ubuntu1 is to be installed

How to get qt3 lib?:d

++ or how to get installed gtk+ for make gconfig, I couldn't find it...

Regards, 
PY

---

### Post by [Yatta] on 2006-07-14
> **xXx 0wn3d xXx said:**
> .... I am not going to be around that much because I do not use Ubuntu anymore :(  That's the best way I can explain what module-image and kernel-headers. I hope I gave you a better understanding of what you wanted to know.

If you don't mind me asking what Distro will u be using now?:confused:  Debian? Just wonderign still

---

### Post by xXx 0wn3d xXx on 2006-07-14
> **'[Yatta] said:**
> If you don't mind me asking what Distro will u be using now?:confused:  Debian? Just wonderign still

I am currently using Archlinux. I found that it meets my needs better and I feel that it is currently better then Ubuntu. That said, Ubuntu is still a fairly new Linux Distribution and has alot of potential. I am hoping to use Ubuntu when the Edgy is out, while still dualbooting with Arch. I want to thank Ubuntu for starting me out in the Linux world because I would have never made it :)

---

### Post by OPaul on 2006-07-16
Is there anyway to add the usplash after I've compiled and installed? Or am I going to have to compile again?

I guess I forget to check "VESA VGA graphics support" and "framebuffer Console Rotation support," because all I get is a black screen during bootup and shutdown.

---

### Post by galactus51 on 2006-07-23
Ok Guys, very good tutorial. Really great. The compilation works fine, the system is very fast. But I'm having two problems (untill now): I can't access my USB card and my other two HDs. Ubuntu says that they're already mounted or busy.

I'm sure that I have not changed anything about USB and file systems supports. Any ideas?

I'm using kernel 2.6.17.6 .

---

### Post by hil on 2006-07-31
I suggest you put "cd .." to change dir into /usr/src after the line in the instructions

15. Install the .deb fine in /usr/src. In terminal do 

I had to download madwifi driver from [http://madwifi.sf.net/]("http://madwifi.sf.net/"), compile, install, and reboot. Then it worked on my Pentium III desktop and Pentium 4 laptop. Very satisfying. Thanks to the instructions.

---

### Post by mrojas73 on 2006-08-01
This ia a great how, I was able to update my kernel many times by following this guide, but since I couldn't get my broadcom 3418 card working I decided to go back to 2.2.16.

Thank you, It was fun!

---

### Post by pibarnas on 2006-08-22
[FONT="Arial"][COLOR="Black"][SIZE="3"][/SIZE][/COLOR][/FONT]
Hey, your how-to is wonderful! Everyone who's intermediate in linux should read it. I came from a Slackware world and imagine we can't recompile kernels in Ubuntu. Happily I was wrong. I've followed these steps and have the last kernel.org one runnig here (2.6.17.9, I think). But something went wrong. I can't connect the network, however the correct modules were loaded on boot (weird, isn't it?). I used the ubuntu's config to compile the kernel.

When I get into gnome, I get the following message from network applet:

Erro SIOCGIFFLAGS: No such device contact your network administrator

I can ping my machine, the eth1 is up on "ifconfig -a", but, for some reason, it can't reach the gateway. When I try to ping it, the computer says the network is unreacheable...

Could someone help me with this issue?

Thank you

---

### Post by xXx 0wn3d xXx on 2006-08-22
> **OPaul said:**
> Is there anyway to add the usplash after I've compiled and installed? Or am I going to have to compile again?

I guess I forget to check "VESA VGA graphics support" and "framebuffer Console Rotation support," because all I get is a black screen during bootup and shutdown.
1. Boot into an old kernel. 

2. Remove the new kernel. 

3. cd into /usr/src

4. Enable Vesa Vga graphics and boot up logo support

5. build the kernel

this way you can keep your old configuration. If anyone is haveing trouble with bcm43xx kernel module, I will post another post on how to compile and use it.

---

### Post by pibarnas on 2006-08-23
[FONT="Arial"][SIZE="2"][COLOR="Navy"][/COLOR][/SIZE][/FONT]

Hello, friends. I'm so glad I could put my Ubuntu box 100% working. I used this wonderful how-to and everything went well. First, I have troubles with my ethernet. So, I went to the config (make xconfig) and adapt the config to my system/hardware, excluding the things I wouldn't need. The problem with the Ethernet was an option unmarked that is referred to accept addresses by the gateway on boot...

If you are interested I could post somewhere my .config. Everything's working here, tooo faaast, mainly the internet (yep, guys, you were right about it), and I'm using Ubuntu 6.06.1 with kernel  2.6.17.9. I didn't apply any patch, but the system seems to go very well.

Thank you very much, guys!!!

---

### Post by Cubiq on 2006-08-24
Simply Amazing. I compiled kernel 2.6.17.11 with ck1 patch on a Pentium 4 prescott CPU and Ubuntu just flies! GDM on Nvidia starts in a fraction of a second, I can hardly see the ubuntu splash screen. I tried to install 686-smp kernel from the repository but it's nothing compared to this custom kernel.

Every user should recompile his/hers own kernel :) Luckly I read this thread because I was going to install Debian From Scratch or Gentoo.


PS: you souldn't need to copy [FONT="Fixedsys"].config[/FONT] file in the linux directory, xconfig will automatically fetch the configuration file from your latest kernel

---

### Post by crypiejay on 2006-08-25
I upgraded my kernel to the latest 2.6.17.xx and everything loads fine etc.. except when I try to run my video module installer it fails with the following:

```
sudo module-assistant build,install fglrx

#This is the end of the output

 /bin/sh:                                                                   
 &#9474; /usr/src/kernel-headers-2.6.17.11/arch/ia64/scripts/toolchain-flags: No    
 &#9474; such file or directory                                                     
 &#9474; /bin/sh: /usr/src/kernel-headers-2.6.17.11/arch/ia64/scripts/check-gas:    
 &#9474; No such file or directory                                                  
 &#9474; make[1]: Entering directory `/usr/src/kernel-headers-2.6.17.11'            
 &#9474;                                                                            
 &#9474;   WARNING: Symbol version dump                                             
 &#9474; /usr/src/kernel-headers-2.6.17.11/Module.symvers                           
 &#9474;            is missing; modules will have no dependencies and modversions.  
 &#9474;                                                                            
 &#9474; ln: creating symbolic link `./Makefile.lib.c' to                           
 &#9474; `../scripts/Makefile.lib.c': File exists
 &#9474; make[2]: *** [scripts/Makefile.lib.c] Error 1                              
 &#9474; make[1]: *** [_module_/usr/src/modules/fglrx] Error 2

```

Any ideas anyone? Not sure why this is happening..](*,)

-Crypiejay
HP Pavilion dv5030 Turion 2Ghz, 2 GIG memory, ATI 200M, 200 GIG, and "working most of the time" native linux broadcom driver :redface:

---

### Post by phenolholic on 2006-08-25
Is there a way to configure the kernel after you compiled? I think I accidentially left it at 250 Hz and want it at 1000 Hz. I've done it before, its a command (i think dpkg-reconfigure) that showed the configuration menu and after I saved, it "recompiled" only the necessarry changes. Thanks in advance

---

### Post by redwolf963 on 2006-08-26
This may be a little paranoid,but where is a checksum at any stage?

Not to say that I don't like things that are just too easy.
As I'm saying this,my HD is going crazy.

HMMM......no checksums of any kind seems to me to be : "Ican build into this kernel,anything I choose and,nooone will be the better for knowing it but me.

Seriously,no MD5sum,no Sha1,no checksums of any kind?

Seems kinda dangerous,even for some seasoned users.

---

### Post by Cubiq on 2006-08-26
> **redwolf963 said:**
> This may be a little paranoid,but where is a checksum at any stage?

do you mean that the howto shoud include checksum checks of downloaded kernel? If so, probably you are right.

---

### Post by xXx 0wn3d xXx on 2006-08-26
> **phenolholic said:**
> Is there a way to configure the kernel after you compiled? I think I accidentially left it at 250 Hz and want it at 1000 Hz. I've done it before, its a command (i think dpkg-reconfigure) that showed the configuration menu and after I saved, it "recompiled" only the necessarry changes. Thanks in advance

1. Boot into an old kernel.

2. Remove the new kernel.

3. cd into /usr/src/linux

4. Run "sudo make xconfig" and do what you need to.

5. build the kernel

this way you can keep your old configuration.

---

### Post by pibarnas on 2006-08-27
> **Cubiq said:**
> Simply Amazing. I compiled kernel 2.6.17.11 with ck1 patch on a Pentium 4 prescott CPU and Ubuntu just flies! GDM on Nvidia starts in a fraction of a second, I can hardly see the ubuntu splash screen. I tried to install 686-smp kernel from the repository but it's nothing compared to this custom kernel.

Every user should recompile his/hers own kernel :) Luckly I read this thread because I was going to install Debian From Scratch or Gentoo.


PS: you souldn't need to copy [FONT="Fixedsys"].config[/FONT] file in the linux directory, xconfig will automatically fetch the configuration file from your latest kernel

Did you apply the patch on 2.6.17.11? I imagine it only be possible to do it on the 2.6.17 itself... cool.

---

### Post by Cubiq on 2006-08-27
> **pibarnas said:**
> Did you apply the patch on 2.6.17.11? I imagine it only be possible to do it on the 2.6.17 itself... cool.

yes it worked, but probably it's not suggested ;)

---

### Post by mlind on 2006-08-27
> **phenolholic said:**
> Is there a way to configure the kernel after you compiled? I think I accidentially left it at 250 Hz and want it at 1000 Hz. I've done it before, its a command (i think dpkg-reconfigure) that showed the configuration menu and after I saved, it "recompiled" only the necessarry changes. Thanks in advance

Some parameters can be configured at runtime. See **man sysctl**.

---

### Post by rko618 on 2006-08-27
I followed this guide and compiled the 2.6.17.11 kernel (and did not apply the patch) and my computer is working beautifully much faster than before however I am having 1 problem.

When I turn my computer on I no longer see the "Ubuntu" bootup listing all the services.  Instead my screen is blank until I get to the Ubuntu GDM.  Everything else seems fine though.  Anyone know how I can fix this?

---

### Post by Cubiq on 2006-08-28
> **rko618 said:**
> When I turn my computer on I no longer see the "Ubuntu" bootup listing all the services.  Instead my screen is blank until I get to the Ubuntu GDM.  Everything else seems fine though.  Anyone know how I can fix this?

in kernel check graphics support > logo configuration > bootup Logo

---

### Post by ultraata on 2006-09-23
> **xXx 0wn3d xXx said:**
> I just finished compiling the newest 2.6.16 kernel from kernel.org and I am getting much better performance. 
...

thx for good how-to!

---

### Post by termite on 2006-09-24
Just compiled the new 2.6.18 kernel.  It works great, minus some DMA problems I found a workaround for...

---

### Post by berserker on 2006-09-24
> **termite said:**
> Just compiled the new 2.6.18 kernel.  It works great, minus some DMA problems I found a workaround for...

Would you mind explaining the problems and what you did to solve them?

Thanks.

---

### Post by termite on 2006-09-24
Sure, but it pretty complicated.  Here goes:

When I installed my kernel, and rebooted, the bootup wouldn't go past 'Loading Hardware Drivers' (I think that's what it's called, the 6th item anyway).  After having messed around a bit, I found that pressing ctrl-alt-F1, then ctrl-alt-F8 got me to the text version of the boot up screen.  I noticed that my hda was timing out on DMA.

So, I rebooted into my old kernel, dropped to a root shell (ctrl-alt F1 at the graphical login screen, login as root.  Or you could do all this with sudo), and started messing around with hdparm and /etc/hdparm.conf.

Eventually, I found that running ```
hdparm -d1 -X udma2
```, then editing /etc/hdparm.conf to include ```
/dev/hda {
	mult_sect_io = 16
	write_cache = off
	dma = on
	transfer_mode=udma2
}
```

and rebooting allowed me access to my new kernel.  However, udma2 was still not enabled.  So, now I need to type ```
sudo hdparm -d1 -X udma2
``` every time I boot up.  Actually, I need to type it twice.  The first time it tells me that the device isn't ready for the command.

Weird, eh?  If anyone has a solution, I'd appreciate it.

One more thing: if anyone has MadWifi 0.9.1 compiled from source (which you have to if you're using it with a custom kernel), note that it doesn't work with 2.6.18.  You need to update to 0.9.2.

---

### Post by GaryH on 2006-10-09
Worked great except a linux-restricted-modules folder wasn't generated for the new kernel. Some of my hardware needs restricted modules. How do I regenerate the linux-restricted-modles folder when upgrading the kernel?

Much thanks,
GaryH

---

### Post by abbeychase on 2006-10-10
> **xpmaniac4ever said:**
> Got this while trying to compile 2.6.17 kernel. Any ideas ?

Were you in GNOME or whatever gui environment you use?  xconfig is for those who are actually in the x environment.  If you are at console I would type 

```

make menuconfig

```

---

### Post by AlReece45 on 2006-10-20
This tutorial worked perfectly for me with the 2.6.18.1 kernel. After compiling, restarted. X failed to start, went in, ran script to recompile nvidia drivers and ndiswrapper load them into kernel, and restarted gdm and came up perfectly.

Thanks for the tutorial.

---

### Post by extremecarver on 2006-10-28
Help: Can anybody explain me how to get rid of those messages?
Kernel 2.6.17 from Kernel.org and Beyond4 = 2.6.17.13 or so.
System Edgy EFT- 
I need to take 2.6.17 because of some undervolt patches and beyond sources which are not yet available for 2.6.18

```
AR      arch/i386/lib/lib.a
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x604): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x909): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xbd3): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x1924): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o: In function `arch_ptrace':
(.text+0x5281): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:intel_cacheinfo.c:(.text+0x9e43): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17'
make: *** [debian/stamp-build-kernel] Error 2
root@felix-laptop:/usr/src/linux# 


```

---

### Post by OPaul on 2006-10-29
> **extremecarver said:**
> Help: Can anybody explain me how to get rid of those messages?
I'm getting the same with 2.6.17.14 and 2.6.17.
```
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x4b8): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x77f): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0x8ea): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xb75): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x4113): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:(.text+0x46f6): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17.14'
make: *** [debian/stamp-build-kernel] Error 2
```

Must be an Edgy thing, I swear this compiled fine in Dapper.

- EDIT - 
Solution, [http://ubuntuforums.org/showthread.php?t=230606&highlight=__stack_chk_fail](http://ubuntuforums.org/showthread.php?t=230606&highlight=__stack_chk_fail)

---

### Post by Xirkka on 2006-10-30
> **OPaul said:**
> 
Must be an Edgy thing, I swear this compiled fine in Dapper.

- EDIT - 
Solution, [http://ubuntuforums.org/showthread.php?t=230606&highlight=__stack_chk_fail](http://ubuntuforums.org/showthread.php?t=230606&highlight=__stack_chk_fail)

I got same problem after I upgraded to Edgy but that solution doesn't work with this :( Or am I doing something wrong? I edited Makefile and changed CFLAG to this: *HOSTCFLAGS = -fno-stack-protector -Wall -Wundef Wstrict-prototypes -Wno-trigraphs \ -fno-strict-aliasing -fno-common*

**Edit** Hehe, it look's like my problem was that I edited **HOST**CFLAGS -line :oops:... Now I edited correct line and it seems to work.

---

### Post by aalex77 on 2006-10-30
I'm tring to compile the new kernel downloaded from kernel.org 2.6.18.1 but i get this error
```
for module in /usr/src/modules/fglrx ; do                       \
          if test -d  $module; then                                \
            (cd $module;                                          \
              if ./debian/rules KVERS="2.6.18.1-ale" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG="EXTRAVERSION=.1-ale"        \
                             ARCH="x86_64"                  \
                             KDREV="10.00.Custom" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \                      echo "in fact being built as root, please file a bug ";  \                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
                 read ans;                                        \
              fi;                                                   \
             );                                                    \
          else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
          fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/fglrx'
dh_testdir
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules
make[2]: Entering directory `/usr/src/linux-2.6.18.1'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c:233: error: ‘UTS_RELEASE’ undeclared here (not in a function)
/usr/src/modules/fglrx/firegl_public.c:447: warning: initialisation from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function ‘firegl_stub_open’:
/usr/src/modules/fglrx/firegl_public.c:570: warning: assignment discards qualifiers from pointer target type
/usr/src/modules/fglrx/firegl_public.c: In function ‘firegl_put_user_ptr’:
/usr/src/modules/fglrx/firegl_public.c:1330: warning: cast from pointer to integer of different size
/usr/src/modules/fglrx/firegl_public.c:1330: warning: cast from pointer to integer of different size
/usr/src/modules/fglrx/firegl_public.c:1330: warning: cast from pointer to integer of different size
/usr/src/modules/fglrx/firegl_public.c:1330: warning: cast from pointer to integer of different size
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_unregister_ioctl32_conversion’:
/usr/src/modules/fglrx/firegl_public.c:2515: warning: ‘return’ with a value, in function returning void
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_vm_map’:
/usr/src/modules/fglrx/firegl_public.c:3175: error: ‘VM_SHM’ undeclared (first use in this function)
/usr/src/modules/fglrx/firegl_public.c:3175: error: (Each undeclared identifier is reported only once
/usr/src/modules/fglrx/firegl_public.c:3175: error: for each function it appears in.)
make[3]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1
make[2]: *** [_module_/usr/src/modules/fglrx] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.18.1'
make[1]: *** [build] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx'
Module /usr/src/modules/fglrx failed.
Hit return to Continue



```

any idea on how can i get it out??
Regards

---

### Post by ajarmoniuk on 2006-11-01
I think there is a problem with GCC 4.1 in Ubuntu Edgy. Try installing the gcc-4.0 package and then use this version to compile the kernel.

Works for me.

---

### Post by Orbitr8 on 2006-11-10
Just now compiled 2.6.18.2 using gcc 4.12 + by following the instructions on page one of this thread, reinstalled the nvidia drivers, and everything works just swell on my conroe.

Actually, the first time I tried, I fluffed up something along the way, so I tried again, disabled a ton of modules and it booted fine, so I did it over with even more disabled options and drivers, etc.

My first compile.  

They take 15 minutes each, and the resulting .deb file comes out to 12.3 megs.
Being a linux noob and all, how does the time and size stack up to 'normal' compilations, if there is such a thing.

Seems like it took longer to go through the modules than it did for anything else.

Compiz works fine, although I'm using a VIA board, so I can't get true NVAgp, but games play great.  I get almost 200 fps in UT2004 with a 6800 XT.

happy here ~ long live the Penguin

btw.   The Ubuntu experience has been awesome.  The amount of information available for Ubuntu is amazing, and growing all the time.
:p

---

### Post by goldenatom on 2006-11-30
Would this be pretty much the same for the 2.6.19 kernel?

---

### Post by Orbitr8 on 2006-12-02
Just now compiled 2.6.19, with basically the same step-by-step instructions from page 1 of this thread, reinstalled my  nVidia video drivers, and it's up and running so far, including Beryl.

 Had to reselect sound manager in a couple of programs.

If I weren't such a noob in Linux, I might be able to give some further insight to changes in gconf, but I basically went through each option and most options were already selected from the previous kernel upgrade (2.6.18.2).

I did have some issues trying to get a command line after the expected X failure , and so recompiled again, double checking all steps.  It worked the second time. (or was it the third ?)

Breaks VMWare at this point, so if you're reliant on VMWare... don't do this thing yet.

~kc  :cool:

---

### Post by thathatman on 2006-12-02
I compiled the 2.6.19 kernel on dapper with no problems.
In order to get fglrx support working, I had to do several things:
Change the make script to executable as described in the ati fglrx wiki.
Change every reference to config.h to autoconf.h in /usr/src/modules/fglrx/*
Move the fglrx.ko file to the right place. For some reason it installed in
```
/lib/modules/misc
```
when it should have installed to:
```
/lib/modules/2.6.19/misc
```
After that, I did a modprobe fglrx, restarted X, and i was back in business.
Let me know if anyone has any similar questions.

---

### Post by happy-and-lost on 2007-01-03
I tried compiling the 2.6.19 kernel on Edgy, but it stops dead at boot. Just sits there. Nothing. So now I'm left with 600mb of files created during the compilation in /usr/src/linux What can I do with them?

---

### Post by twinszg on 2007-01-06
Thanks m8,it works for me. Great tutorial

---

### Post by muxecoid on 2007-01-14
Compiled and installed successfully.:) :b:

---

### Post by michie86 on 2007-01-18
hello.. i was wondering.. are the steps you stated are the way to "upgrade" my kernel from 2.6.15 to a 2.6.16? Coz i'm currently having problems with detecting my modem for dialup connection and somebody told me that the solution is either upgrading to ubuntu 6.10 or compiling my own 2.6.16 kernel. Is this it? I decided that maybe i'll just compile since i do not have a 6.10 cd installer. Am i on the right track? And also, the "sudo apt get build....." in  the first step, that requires internet connection? Am i right? If so, how can i download the necessary files manually? since my i can't fix my dialup connection as of now. Thanks.

---

### Post by ryan76 on 2007-01-20
I tried this HowTo to get DRI working and it still isn't.

```
make sure fglrx is in the Driver section.
```

What does this mean?

---

### Post by muxecoid on 2007-02-19
Something wrong. USB-disks stopped working. Looks like I disabled something important with needless-looking name. Any ideas?

---

### Post by pay on 2007-02-19
> **muxecoid said:**
> Something wrong. USB-disks stopped working. Looks like I disabled something important with needless-looking name. Any ideas?[These](http://gentoo-wiki.com/HOWTO_USB_Mass_Storage_Device) are the options that you need> SCSI support  --->
     <*> SCSI support
     --- SCSI support type (disk, tape, CD-ROM)
     <*>   SCSI disk support
File systems --->
     <*> DOS FAT fs support
     <*>   MSDOS fs support
     < >     UMSDOS: Unix-like file system on top of standard MSDOS fs
     <*>   VFAT (Windows-95) fs support 
USB support --->
     <*> Support for USB 
     <*>   UHCI (Intel PIIX4, VIA, ...) support 
     <*>   OHCI (Compaq, iMacs, OPTi, SiS, ALi, ...) support 
     <*>   USB Mass Storage support 

---

### Post by muxecoid on 2007-02-19
I did not enable SCSI. Why do I need SCSI for USB? :-/

---

### Post by [Yatta] on 2007-02-26
> The umass(4) driver uses the SCSI subsystem to access to the USB storage devices, your USB device will be seen as a SCSI device by the system. Depending on the USB chipset on your motherboard, you only need either device uhci or device ohci, however having both in the kernel configuration file is harmless

If u look deeper enough you would have noticed ur USB HD's had a name like ***/dev/sdax*** or whatever. After it's all said and done you'll need to redo ur kernel with the SCSI system in there; basically like what ***Pay ***said.

---

