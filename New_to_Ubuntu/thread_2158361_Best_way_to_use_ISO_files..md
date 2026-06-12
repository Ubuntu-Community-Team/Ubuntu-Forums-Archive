---
title: "Best way to use ISO files."
date: 2013-06-28
forum: New to Ubuntu
---

### Post by zozza on 2013-06-28
What is the easiest way to use an ISO file. I want to experiment with a different Linux OS.  I use Windows XP when necessary with VirtualBox.  The main problem is that it uses masses of memory.  Ubuntu is really slow so it's not possible to use it with VirtualBox.  Would using VirtualBox and the ISO in an external hard drive make a difference?  Or any other ideas?  Thanks.

---

### Post by BBQdave on 2013-06-28
> **zozza said:**
> What is the easiest way to use an ISO file. I want to experiment with a different Linux OS.

Live Linux CD or DVD :)

It is a little slower in response than an actual install of Linux, but it lets you test hardware compatibility and explore the Linux distro.

---

### Post by Cheesemill on 2013-06-28
If your machine can boot from USB then use [UNetBootin]("apt://unetbootin") to make a bootable USB drive from your iso file.

---

### Post by squakie on 2013-06-28
An external drive (perhaps with the exception of esata) will always be slower than an internal drive due to the interface between the PC and the external disk.  Putting your ISO out there but running virtualbox to use it would do no good.

It may be that your hardware just doesn't have the resources to support running much in virtualbox.  My won experience over the years has been that anything less than quad-core usually doesn't work out so well unless the CPU's are fast - don't even bother with a single core processort.  When you have 4 or more you can allocate 2 to the virtual machine and still have 2 cores left for the host.  Memory is also variable - your virtual machine doesn't have to take a lot of memory - the default when setting up a vm is normally fairly small and I have always had to increase it.  I try to give a minimum of 2 gig of memory to the vm and still leave 2, or preferably more, for the host.  Video can also be a slow down.  Be sure you have allocated enough memory to the virtual machine's virtual video adapter.  The default is extremely small for most things today.  Check to see if you have the accelerations set on the configure page for the video on the virtual machine as well.

There are a couple of other things I would keep in mind:

With the later versions of Ubuntu the Unity interface for the desktop has been standard.  This will require more CPU power and more memory allocated to the vm to be effective.

If the vm is installed with Windows 8 as the host - do a lot of research on the net.  I needed to change one of the video settings to even have a chance running 12.xx on up in a VM with Windows 8 as the host.  Otherwise it ran unbelievably slow - and I mean SLOW, not just slow.  There are other settings that may need to be adjusted if Windows 8 is the host as well.  For me, on a multi-core system running Windows 8, allocating 2 CPU's and 4 gig or memory to the vm did nothing - ubuntu in that vm was completely unusable in my experience.

So, check the vm settings - how much total memory are you giving the vm, how much memory are you giving the vm's virtual video adapter, do you have video acceleration set for the vim's virtual video adapter, how many CPU cores does your system have, what are their speeds and how many are you allocating to the vm. how much physical memory is still left for the host OS after configuring the vm.  I'd check those.

As BBQdave indicated, running the live media from a DVD drive or a USB thumb drive is another possibility.  You can also use a tool like unetbootin when making the USB thumb drive and set "persistence" - the ability to "remember" changes between boots.  In that way you can actually run ubuntu or another distro from the USB thumb drive.  Use a larger thumb drive if you do so.

---

### Post by oldfred on 2013-06-29
You can boot ISO from grub directly.

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

