---
title: "Boot oversize .iso"
date: 2011-05-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-05-28
.iso oversize but still want to try it out?  See

[http://ubuntuforums.org/showthread.php?t=1549847&highlight=howto+.iso](http://ubuntuforums.org/showthread.php?t=1549847&highlight=howto+.iso)

Download the .iso with zsync or whatever,

Make a convenient directory like /boot/iso on /dev/sda1 or wherever.  I put the directory on /dev/sdc1 which is a USB hard drive.  Copy the .iso into this directory.

nano /etc/grub.d/40_custom

edit to look like:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ocelot ISO" {
set isofile="/boot/iso/oneiric-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
} 
#! exit

Do note the (hd0,1) has to point to the device that has the /boot/iso

sudo update-grub

Reboot and try it out.  I got screenfuls of whatever but the oversize oneiric iso did boot & get Firefox up, although some certificate complaint on [www.google.com](www.google.com) but ran anyway.

Enjoy.

Advantages of putting the oversize .iso on the hard drive is it will boot on pc's that don't boot on a USB, or don't have a DVD reader.

Do note you could put the .iso onto a USB stick anyway.  I'll try that next.  A lot less fuss than running startup disk creator.   

Jerry

p.s. this is Alpha time, so have everything backed up.  Breakages are guaranteed....

---

### Post by TerminX on 2011-05-29
That's pretty cool; I didn't realize GRUB 2 was capable of booting an iso directly now.  There were quite a few times with GRUB 0.97 where I could have used this but IIRC it wasn't possible (or if it was, it required patches to GRUB) at the time.

---

### Post by teh603 on 2011-05-29
I'll bet this is the intended solution for all those Macs with failing DVD drives, that also can't boot off USB.

---

### Post by MacUntu on 2011-05-29
Macs can't boot from USB? oO

---

### Post by scradock on 2011-05-29
Anyone clear which version of grub2 can do this? I've tried it with boot controlled from maverick (my rock-solid "mainline" version), and it didn't work, so maybe I need a newer grub2.....

---

### Post by oldfred on 2011-05-29
I have been using grub2 to directly boot ISO on my flash drive since about the start of Ubuntu using grub2. 

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

I did the above manually before some of these scripts became avaiable:
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by Starks on 2011-05-29
1. If an iso is a few megabytes oversized, you can still burn it unless you have a 10 year old CD burner.

2. You can always use a USB stick.

---

### Post by julianb on 2011-05-29
Starks - you can indeed use a USB stick. And for me the best way to do so is using grub2 to boot the ISO directly - no unpacking of the ISO (by unetbootin or similar) is required.

---

### Post by Starks on 2011-05-29
i know, but putting it on a stick is just as fast, if not faster than most traditional drives.

also, you get rescue stick if your grub ever gets fudged.

---

### Post by scradock on 2011-05-29
> **Starks said:**
> i know, but putting it on a stick is just as fast, if not faster than most traditional drives.

also, you get rescue stick if your grub ever gets fudged.

I am puzzled how you can access an .iso on a USB stick from grub. The only "drive" mounted when grub runs is the one referenced in the "grub-install" command, as far as I know. That's why the .iso has to be "unpacked" by unetbootin so that the stick can act as the booting medium, if enabled in BIOS.

Or am I missing something?

BTW, I still can't get the Ocelot oversized .iso to boot, from USB stick, from another partition, or from the partition that grub is working in.

---

### Post by scradock on 2011-05-29
AHA!!!

Trying to figure out why I can't get the oversized oneiric-alternate-amd64.iso to boot, as described by jerrylamos, I took a look inside.

It has no casper folder!

So of course when I try to boot, grub fails to find ../casper/vmlinuz and .../casper/initrd.lz

And so I get a "file not found" error message......

Now what is going on?

---

### Post by jerrylamos on 2011-05-29
I tried booting oneiric-desktop-i386.iso with Grub from USB formatted f32.  For whatever reason Grub2 couldn't find the file.

Living dangerously, on a Acer netbook multi boot Windoze 7, Meerkat, Narwhal copied the .iso into /boot/iso folder on the Meerkat /dev/sda5.

Appended this to /etc/grub.d/40_custom

menuentry "Ocelot sda5 /boot/iso" {
set isofile="/boot/iso/oneiric-desktop-i386.iso"
loopback loop (hd0,5)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
#! exit

That worked, wireless and all.

Let me see if formatting the USB to ext2 might work....Dinner time.  Bye.

Jerry

---

### Post by scradock on 2011-05-29
> **scradock said:**
> AHA!!!

Trying to figure out why I can't get the oversized oneiric-alternate-amd64.iso to boot, as described by jerrylamos, I took a look inside.

It has no casper folder!

So of course when I try to boot, grub fails to find ../casper/vmlinuz and .../casper/initrd.lz

And so I get a "file not found" error message......

Now what is going on?

Further research: the -amd64 alternate .iso has no casper; vmlinuz and initrd.gz (NOT .lz) are in /install. 

Using 

```
linux (loop)/install/vmlinuz.....
initrd (loop)/install/initrd.gz
```

allows grub to find files, and gives me a screen-full or two of text output, but the boot then stalls. I've tried putting "boot=install" and "boot=boot" on the "linux" line, but neither works. Keeping it at "boot=casper" obviously doesn't, because there is no /casper.

What next? The .iso has its own grub menu, but I never get to it.......

---

### Post by Hanmac on 2011-05-29
have some try the grub-imageboot package to boot an image?

---

### Post by drs305 on 2011-05-29
> **scradock said:**
> What next? The .iso has its own grub menu, but I never get to it.......

EDIT: Didn't work...
I'm downloading the daily build to take a look, but if there is a grub.cfg file you may be able to boot it by simply creating a menu entry which points to it (with the normal loopback, etc entries prior to the following line):
> configfile (loop)/path/grub.cfg

---

### Post by drs305 on 2011-05-29
I just downloaded the oneiric-desktop-amd64.iso daily build and it was a pretty standard menuentry. The ISO I downloaded included the standard 'casper' folder containing the kernel and initrd image.

In this example, the file is located in sdb6 in the /iso folder:
> menuentry 'Oneiric                      ' 		{
isofile=oneiric-desktop-amd64.iso
loopback loop (hd1,6)/iso/$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/$isofile  noprompt noeject
initrd (loop)/casper/initrd.lz
}


---

### Post by teh603 on 2011-05-29
> **MacUntu said:**
> Macs can't boot from USB? oONeither of mine have been able to. I've had a macmini 2,1 (?) and a 3,1; and neither of them have taken to USB booting, at least from a stick. The older one wouldn't even boot from an external DVD drive, go figure.

Add to it that Apple's DVD drives have a life expectancy of just under 2 years, and you've got a bit of a problem with hardware life expectancy. Its why my next compy is going to be built out of off-the-shelf parts. If I can build it myself, I can replace failing components myself.

---

### Post by scradock on 2011-05-29
> **drs305 said:**
> I just downloaded the oneiric-desktop-amd64.iso daily build and it was a pretty standard menuentry. The ISO I downloaded included the standard 'casper' folder containing the kernel and initrd image.

In this example, the file is located in sdb6 in the /iso folder:

That's weird - maybe I downloaded the wrong file - oneiric-alternate-amd64.iso?

---

### Post by drs305 on 2011-05-29
> **scradock said:**
> That's weird - maybe I downloaded the wrong file - oneiric-alternate-amd64.iso?

That sounds likely as I can't imagine they would vary the file structure between the 32 and 64-bit versions or between a daily build and what's available on the Ocelot site - unless there was an incorrect link.

---

### Post by scradock on 2011-05-29
> **drs305 said:**
> That sounds likely as I can't imagine they would vary the file structure between the 32 and 64-bit versions or between a daily build and what's available on the Ocelot site - unless there was an incorrect link.

OK - gottit. I downloaded the ALTERNATE .iso, which is not a liveCD; you downloaded the LiveCD .iso. I was misled by the first post about dailies, which specifically referenced the alternate versions, as they were the first to be released. 

Now downloading the LiveCD version - keeping my fingers crossed! I've checked the manifest files, and indeed the LiveCD has a /casper folder, whereas the alternate does not.

I did get the alternate .iso to boot after making a Startup USB, but it failed to complete the install because I wasn't using a wired network connection.

---

### Post by jerrylamos on 2011-05-29
Got the oversized oneiric-desktop-i386.iso on USB stick to boot on this Acer Aspire one netbook.

With Narwhal on the hard drive and a USB stick,
sudo gparted to make 2 partitions on the USB stick.
formatted first partition ext2
labeled first partition oneiriciso
formatted second partition ext2
labeled second partition casper-rw
just in case persistence worked.
/etc/grub.d/40_custom looks like:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ocelot sda5 /boot/iso" {
set isofile="/boot/iso/oneiric-desktop-i386.iso"
loopback loop (hd0,5)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
menuentry "Ocelot sdb1 USB" {
set isofile="/boot/iso/oneiric-desktop-i386.iso"
loopback loop (hd1,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
#! exit

sudo update-grub

Now I have the netbook boot order set for USB first so booting, Grub2 says "missing operating system" then goes on to display the grub options which were set with Narwhal on the hard drive and I have a choice of booting on the hard drive Meerkat, Narwhal, Windoze 7, .iso on /boot/iso on Meerkat, and also the USB stick.

Let the Ocelot breakage resume, way oversized .iso & all ... 

Now if I should try to install or update Ocelot first thing it does is screw up Grub2 and the grub boot menu.  On my Compaq I installed Ocelot on a USB /dev/sdc hard drive and it promptly overwrote the grub menu on the main hard drive /dev/sda with a garbled mess.  Ugh.  I was able to get another partition with a released Ubuntu to boot and straighten out the mess....I did volunteer for this.  And it isn't even Alpha yet.  

Jerry

---

### Post by drs305 on 2011-05-29
> **jerrylamos said:**
> 
Now if I should try to install or update Ocelot first thing it does is screw up Grub2 and the grub boot menu.  On my Compaq I installed Ocelot on a USB /dev/sdc hard drive and it promptly overwrote the grub menu on the main hard drive /dev/sda with a garbled mess.  Ugh.  I was able to get another partition with a released Ubuntu to boot and straighten out the mess....I did volunteer for this.  And it isn't even Alpha yet.  

Jerry

If you have a second drive you could always tell Ocelot's Grub to install to that drive, and then make sure your BIOS boots to your original OS's drive and your working Grub MBR.

I know I'm going to curse this thread. Now that I have downloaded the ISO it will not be long before I feel compelled to install it.  ;-)

---

### Post by Starks on 2011-05-29
> **scradock said:**
> I am puzzled how you can access an .iso on a USB stick from grub. The only "drive" mounted when grub runs is the one referenced in the "grub-install" command, as far as I know. That's why the .iso has to be "unpacked" by unetbootin so that the stick can act as the booting medium, if enabled in BIOS.

Or am I missing something?

BTW, I still can't get the Ocelot oversized .iso to boot, from USB stick, from another partition, or from the partition that grub is working in.
You boot from USB before GRUB.

---

### Post by scradock on 2011-05-29
> **Starks said:**
> You boot from USB before GRUB.

That's why I'm puzzled how making a grub entry to point to a USB stick can ever work.

If BIOS tells the machine to boot from USB it never sees the grub files.

But if you start from the grub files, which are running FROM some mounted partition, BEFORE the USB drive gets mounted, I don't see how grub can recognize the correct place to look.

---

### Post by Starks on 2011-05-29
You can have GRUB on the USB drive in question in order to boot the iso, but that's rather stupid.

---

### Post by scradock on 2011-05-29
I agree, it would seem like an unusual way to go.

That said, I now have the correct .iso, in a folder on my main HD, with a grub entry pointing to it. And it indeed boots, and installs Oneiric. And Oneiric seems to be working just as well as my dist-upgraded version that has been settling in for a month now.

---

### Post by inportb on 2011-05-30
> **TerminX said:**
> That's pretty cool; I didn't realize GRUB 2 was capable of booting an iso directly now.  There were quite a few times with GRUB 0.97 where I could have used this but IIRC it wasn't possible (or if it was, it required patches to GRUB) at the time.

To be sure, this behavior requires support from both the bootloader and the OS. Grub4DOS had this capability, but the OS could only go so far before it also needs to loop-mount its image. It's not totally transparent.

---

