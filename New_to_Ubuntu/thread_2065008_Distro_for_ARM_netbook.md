---
title: "Distro for ARM netbook"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by chrisak on 2012-09-30
Hello everyone! I am not new to Linux, used quite a few distros on various computers. Right now all I have is an Asus X401 but I wanted a separate cheap laptop to code in Linux on... so as a promotion gift to myself, I ordered this for a challenge...

[Here is the netbook I ordered for me.]("http://www.ebay.com/itm/New-7-VIA8850-4GB-Android-4-0-Netbook-Mini-Notebook-1-2GHz-Wifi-Camera-Black-/180977999171?forcev4exp=true&forceRpt=true#ht_500wt_1271")

Spec wise, I am happy... except for one thing, which I am not unhappy of, just unsure... the CPU. It's an ARM architecture, which I previously didn't know of. After a little research, I learned I do use it every day on my iPhone and iPad! However I have never used Linux on it... so I ask the following question: Can anyone recommend a lightweight distro that eclipse can be installed on? It's my favored IDE (unless you can suggest one better) because of it's quality of life features.

I have heard that Ubuntu has ARM versions available but since it is a weaker computer I have considered it may not be able to have the fancy graphics on it... actually I wouldn't mind a distribution like PuppyLinux which I hear ALSO supports ARM. But have been unable to find a direct download link or precise instructions.

That said, can anyone point my to precise instructions to install Puppy or any other distro that supports ARM? I also know there is a revision change in the ARM line that means some CPUs are supported and some aren't. I haven't been able to find out about this one and it's not here yet... can anyone decipher what it is?

---

### Post by AndyOpie150 on 2012-09-30
What's the specific ARM version (ie ARMv6, ARMv7, etc.).

---

### Post by chrisak on 2012-09-30
I don't know for sure. This processor is a VIA WM8850. A little 'google-fu' makes it out to be an ARM Cortex A9 processor...

---

### Post by mips on 2012-09-30
I would start looking here,

[http://archlinuxarm.org/](http://archlinuxarm.org/)
[http://www.debian.org/ports/arm/](http://www.debian.org/ports/arm/)
[https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)

See which has packages for the software you need and go browse their forums.

---

### Post by AndyOpie150 on 2012-09-30
EDIT: The ARM Cortex-A9 has the ARMv7 instruction set (sorry for the error) .
What is the actual brand and model number of your netbook?

---

### Post by chrisak on 2012-09-30
Well if you look at the eBay listing, it's pretty much just a generic clone computer ( which I don't mind ) with no markings. Also the computer isn't here yet either.

Thanks mips

*Edit* I'd like to get Ubuntu but that page doesn't show any downloads to it... any ideas? I don't see which image would work for mine... Again I am new to advanced installs such as this one appears to be.

---

### Post by AndyOpie150 on 2012-09-30
Any Idea what the RAM and disk space are?

---

### Post by chrisak on 2012-09-30
> **AndyOpie150 said:**
> Any Idea what the RAM and disk space are?

Once again, on the eBay listing...

1GB Ram
4GB Flash Storage (instead of HDD)
I'd use the storage for the OS obviously and then use an SD card for programs.

---

### Post by AndyOpie150 on 2012-09-30
It almost seems like it set up like a Tablet with a keyboard. The ARM Cortex-A9 is used in Tablets.

Maybe you could google how to install Linux on a tablet as well as the links mips gave?

---

### Post by SonicSteve on 2012-09-30
I tried installing Ubuntu on a similar system (atom CPU though) and honestly the biggest (rather smallest) problem was the resolution limitations. Desktop apps couldn't run on a screen that small, OK buttons were missing etc.

---

### Post by chrisak on 2012-09-30
@Andy: It has internal storage of 4GB. It's a flash memory storage so it's like having a permanent SD card inside.

@Steve: I've run a couple of Linux distros on a screen this small and they run fine. I did notice it but remedied by maximizing the screen, at least on the last two.

---

### Post by mips on 2012-10-01
> **chrisak said:**
> 
Thanks mips

*Edit* I'd like to get Ubuntu but that page doesn't show any downloads to it... any ideas? I don't see which image would work for mine... Again I am new to advanced installs such as this one appears to be.

[http://www.ubuntu.com/download/arm](http://www.ubuntu.com/download/arm)

I don't see much documentation for the Ubuntu ARM stuff or maybe I'm not looking in the right places. I've seen more documentation for Arch & Debian.

---

### Post by jerrrys on 2012-10-01
Check it out

[ATTACH]224922[/ATTACH]

When you get yours, flip it over and I think you will find something like WM bla bla.

That be WonderMedia

[http://www.wondermedia.com.tw/en/products/platform/index.jsp](http://www.wondermedia.com.tw/en/products/platform/index.jsp)

---

### Post by AndyOpie150 on 2012-10-01
chrisak: When I installed Ubuntu on my old 2003 Windows box I used Pendrivelinux which is a utility that will configure a USB storage device to be bootable and downloads and installs a distro from a huge list.
The list includes most distro from:
Ubuntu Latest
Ubuntu Old
Linux Mint
Debain Live/Netinst
Backtrack
Fedora
openSuse
Puppy Linux Based
Linux Distros for Kids
And a list of over 90 other Distros as well as a few other options.

All in all there must be close 200 to choose from. The one's that will work for your upcoming netbook should be in one of those list's

You should be able to use a 2GB SD card with the Penndrive utility. It wouldn't hurt to buy a 16GB Sandisk SD card as they have the fastest read speed of any SD card I've seen which will make install of the distro from the SD card a lot faster and only cost $20.00 at WalMart. I got read speeds of right at 40MB/s 

There site is here: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
They also have a version that will allow a live .iso to be installed.

---

### Post by nautilus on 2012-12-31
There appear to be a couple misconceptions right off the bat about this netbook.

First off, it has no traditional drive to speak of, rather an eMMC which contains a non-msdos partition table which most Linux distributions won't be able to understand.

ARm doesn't have ACPI, and instead uses a non-standard sysfs interface (from Android) to access what ACPI would normally provide.  This makes things like setting your LCD brightness or suspending the netbook difficult, at least, it won't work out-of-the-box.

Installing an OS on ARM shares very little with installing an OS on a PC.  If you've ever installed Gentoo from stage2 or so you'll probably not be too uncomfortable.

There is hope though.  I have this exact netbook (actually, 40 or so of them,) and have had great success loading Debian Squeeze on it.  The trick is that the bootloader (u-boot) will attempt to boot to the sdcard when you power it on.  From there, you are free to boot to a Linux desktop of your choice (assuming it is built for arm7 or lower in Thumb or lower) or boot an installer.

In all my research and searching I have yet to find a general Linux installer which can properly install to the NAND, but Debian's netinst is closest.

Java runs great on it, and although I haven't tried Eclipse on it, I use Qt Creator regularly.  It is cramped.  It feels like I'm Hagrid and I'm coding on a Mac Classic.  Of course once you're setup you can even cross compile to x86_64 for style points, or if you are motivated, bootstrap a qemu-x86 userspace jail with wine on it and run adobe photoshop on it.... maybe? :)

But basically what you own is an unlocked cell phone with a bigger display, a keyboard, and a touchpad... and no 'phone'.  Treat it as such during development: you CAN brick it!

I hope some of this info helps on your crusade, keep us posted on your progress!

(By the way, Ubuntu Core 12.04+ uses thumb2 binaries which the WM8850 can't run)

---

### Post by PereXDenver on 2013-01-19
> **nautilus said:**
> There appear to be a couple misconceptions right off the bat about this netbook.

First off, it has no traditional drive to speak of, rather an eMMC which contains a non-msdos partition table which most Linux distributions won't be able to understand.

ARm doesn't have ACPI, and instead uses a non-standard sysfs interface (from Android) to access what ACPI would normally provide.  This makes things like setting your LCD brightness or suspending the netbook difficult, at least, it won't work out-of-the-box.

Installing an OS on ARM shares very little with installing an OS on a PC.  If you've ever installed Gentoo from stage2 or so you'll probably not be too uncomfortable.

There is hope though.  I have this exact netbook (actually, 40 or so of them,) and have had great success loading Debian Squeeze on it.  The trick is that the bootloader (u-boot) will attempt to boot to the sdcard when you power it on.  From there, you are free to boot to a Linux desktop of your choice (assuming it is built for arm7 or lower in Thumb or lower) or boot an installer.

In all my research and searching I have yet to find a general Linux installer which can properly install to the NAND, but Debian's netinst is closest.

Java runs great on it, and although I haven't tried Eclipse on it, I use Qt Creator regularly.  It is cramped.  It feels like I'm Hagrid and I'm coding on a Mac Classic.  Of course once you're setup you can even cross compile to x86_64 for style points, or if you are motivated, bootstrap a qemu-x86 userspace jail with wine on it and run adobe photoshop on it.... maybe? :)

But basically what you own is an unlocked cell phone with a bigger display, a keyboard, and a touchpad... and no 'phone'.  Treat it as such during development: you CAN brick it!

I hope some of this info helps on your crusade, keep us posted on your progress!

(By the way, Ubuntu Core 12.04+ uses thumb2 binaries which the WM8850 can't run)

Nautilus- your post gives me hope. 

I have three of these generic 8850 netbooks. (two with 512MB and one with 1gb memory) I have a project involving use of such devices in a (totally underfunded, non-tech) classroom. 

I had also purchased 3 generic netbooks of the older 8650 processor (natively running Android 2.2 rather than 4.0). Although I had originally hoped to use the devices in their native Android modes, some device limitations (being able to explicitly mount and unmount usb drives) led me to switch to Linux. On the 8650s I was able to use instructions and files for Arch Linux (two articles outlining "Arch Linux on WM8650 Netbook" - [http://kernelhacks.blogspot.com/2012/06/arch-linux-on-wm8650-netbook.html](http://kernelhacks.blogspot.com/2012/06/arch-linux-on-wm8650-netbook.html)). With a bit of tweaking, this got a very basic Linux environment, with X and LXDE WM running on the 8650s. I never did get networking up and running, though, since that was not a core part of my need, I did not pursue it too hard.

OK, enough lead-up. 
I am able to easily clone the SD cards that will boot Linux on the 8650s. I tried the card in the 8850s, but it seems to have no effect whatsoever on the boot process which just continues on to Android 4.0.

Unless I misread your post, you are able to get Debian Squeeze running on these 8850 devices using an SD card. I am nowhere near clever enough to do my own kernel builds etc. So I am wondering if there is a site where there is a Debian Squeeze image for ARM for a SD card. Or perhaps a fairly simplistic "cookbook" set of instructions (such as what existed for the Arch/8650).

Any guidance you can provide is greatly appreciated!

-Pere

---

### Post by ld114 on 2013-01-20
Don't know if this will be useful, but I read that linux kernel 3.7 has better support for arm processors:

[http://www.zdnet.com/linux-3-7-arrives-arm-developers-rejoice-7000008638/](http://www.zdnet.com/linux-3-7-arrives-arm-developers-rejoice-7000008638/)

I doubt if any distros ship with 3.7 yet, though the snapshot of ubuntu 13.04 looks to contain 3.7... maybe worth a try.

---

### Post by PereXDenver on 2013-01-23
Hello Nautilus-
I had hoped for my posting to get your attention, but I think that including the lengthy quote of what you had posted blunted the impact of my implied plea for guidance!
Thoughts?
Thanks.
-Pere

---

### Post by chelovek84 on 2013-04-10
VIA released WM8850 kernel source
[http://github.com/wondermedia/wm8850](http://github.com/wondermedia/wm8850)
This might help in near future.

---

### Post by chelovek84 on 2013-04-24
> **chelovek84 said:**
> VIA released WM8850 kernel source
[http://github.com/wondermedia/wm8850](http://github.com/wondermedia/wm8850)
This might help in near future.

Assembly source files missing in kernel source :(.

Hope this one [https://github.com/apc-io/apc-8950](https://github.com/apc-io/apc-8950) can somehow help.

---

