---
title: "Booting to LiveUSB question"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by GLE3 on 2013-07-31
Hi, I'm GLE3, and I am an absolute beginner..  :)  Seriously though, I am totally new to linux and am looking for a little direction now that I think I have my booting usb in order.  I used LiveUSB creator in windows and downloaded the 10.04(tried 12.04 but had pae kernel issues) iso version of ubuntu.  What I am looking to do is install everything on my flash drive so I can keep things off my hard drive that has windows on it.

Anyway, my USB succesfully boots and I am greeted by about 7 or 8 options.  The first two options are to install (I don't know if it means install on my hard drive or install on the flash drive) and there is other options that do not look like the way to go (memory test, boot to first hard disk, etc....) but I have never used this stuff before so I am not sure.  Would there be any documentation out there that would help me with this?  Or is it just as easy as choosing install and it gives me the choice to install to my flash drive?

Besides just experimenting with ubuntu, I do have a specific project I want to get into that I need linux for.  My hard drive on my NAS crashed and I am trying to set up a new one using this direction:  [http://iomega.nas-central.org/wiki/Installing_firmware_on_a_new_disk_%28Home_Media%29](http://iomega.nas-central.org/wiki/Installing_firmware_on_a_new_disk_%28Home_Media%29)

I'm guessing I will have to use what I hear is the Terminal command line to get most of what is in that site done.  It sounds like it is somewhere in the folder structure of 10.04 but I'm not quite sure where.  Could someone confirm these things for me?  I'm just a 'windows guy' and any help would be appreciated!  Thanks in advance!

---

### Post by Chris of Arabia on 2013-07-31
Try this page here. It should answer your questions - [http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

---

### Post by lah7 on 2013-07-31
**Welcome to the world of Ubuntu!** Running Ubuntu off a memory stick might give you unbearably slow performance then if you was to dual boot on your hard drive, due to USB 2.0's write speeds as well as depending on your hardware. It could wear out your flash drive too so you risk losing critical data if you was to use it constantly.

From the sounds of things, you should be able to install Ubuntu to another flash drive during the graphical set up, assuming it isn't the same one as you're installing from. Double check your options so you do not accidentally format your hard drive Windows is sitting on (select the "custom" option)

You may wish to virtualize Ubuntu instead, software such as **Virtualbox** ([http://www.virtualbox.org](http://www.virtualbox.org)) let you run another operating system within your physical one (in which case Windows), both of which are isolated from each other and can be really useful for sandboxing and exploring without interfering with Windows at all (besides a virtual drive file). If you've got a dual core CPU or better and plenty of RAM, you shouldn't hit performance degradation.

---

### Post by oldfred on 2013-07-31
IF system is older an you need the non-PAE, it would be better to use Lubuntu? The 10.04 is not really supported for desktop use anymore and 12.04 would be much better.
 [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

But most systems that are new enough to boot from flash drives are new enough to have a processor with PAE. What cpu do you have? Low end Pentium-M and before need non-PAE. Some higher end Pentium-M have PAE, but do not report it.

 To see processor
lscpu
grep --color=always -i PAE /proc/cpuinfo

The install option will offer to install it where ever you want. Either internal hard drive, external hard drive or another flash drive. 

 Full Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

 HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

---

### Post by sudodus on 2013-07-31
I repeat *oldfred*'s question about CPU, and I would add: Please specify your computer! It makes it possible to give much better advice.

At least, specify the CPU, how much RAM and the graphics chip/card!

If you really have problems with PAE, I have some tips, because I have worked a lot with it. But first we need to know what CPU you have, otherwise we will only make you confused.

---

### Post by C.S.Cameron on 2013-07-31
Welcome to the Forums.

Sudodus has done some neat things with Lubuntu and PAE.

Check out [http://ubuntuforums.org/showthread.php?t=2151890&highlight=usb](http://ubuntuforums.org/showthread.php?t=2151890&highlight=usb)

---

### Post by gordintoronto on 2013-07-31
Let me clarify one thing for you: "install" means, "install to a different device than you booted from." You could install from a flash drive to the hard drive, or another flash drive, or a USB external hard drive.

And yes, I agree with the people who suggested Lubuntu, don't use 10.04, and tell us about your CPU, memory and video adapter.

---

### Post by GLE3 on 2013-07-31
Thanks for all the replies!  Lots of good stuff here.  Many thank yous...  I'll be booting off 2 machines both have different specs...

Laptop:  Thinkpad T42  Intel pentium M 1.8 Ghz, 1GB ram, ATI Mobility Radeon 9600 series

Base specs: [http://support.lenovo.com/en_US/landing.page?](http://support.lenovo.com/en_US/landing.page?)

Also have Desktop I want to boot with Getting specs for that now...

Desktop: Dell Optiplex GX620, Pentium 4, 2gb ram, BFG tech geforce 210 video


I know prehistoric stuff...  Will this stuff even run 12.04 well?

---

### Post by sudodus on 2013-08-01
> **GLE3 said:**
> Thanks for all the replies!  Lots of good stuff here.  Many thank yous...  I'll be booting off 2 machines both have different specs...

Laptop:  Thinkpad T42  Intel pentium M 1.8 Ghz, 1GB ram, ATI Mobility Radeon 9600 series

Base specs: [http://support.lenovo.com/en_US/landing.page?](http://support.lenovo.com/en_US/landing.page?)

Also have Desktop I want to boot with Getting specs for that now...

Desktop: Dell Optiplex GX620, Pentium 4, 2gb ram, BFG tech geforce 210 video


I know prehistoric stuff...  Will this stuff even run 12.04 well?

1. My Thinkpad T42 has a Pentium M 1.7 Ghz CPU without PAE flag. Yours with 1,8 GHz has probably very similar properties, so I suggest that you try either of these alternatives depending on which desktop environment you prefer:

Xubuntu 12.04.2 LTS [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

Lubuntu 13.04 or Saucy alpha-2 (to be 13.10 in October) [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

2. The Dell with a P4 and 2 GB RAM should run without problems unless there are problems with the graphics. In that case you might need boot options and later on install a proprietary nvidia driver.

I think that you can try either of Xubuntu 12.04.2 and any current version of Lubuntu to run it. It does not need fake-PAE, but is not hurt by it either, so you should be able to use the same flavour of Ubuntu for both computers (unless limited by the graphics).

---

### Post by gordintoronto on 2013-08-01
The key point is that both computers have enough RAM to run Xubuntu or Lubuntu. They might be slow, but they should work.

---

