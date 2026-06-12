---
title: "Have I understood these directory names?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by ginestre on 2008-10-29
Can I just check my understanding of the names of some directories? 

/dev contains (amongst other devices) some pointers to physically present disks. But being in /dev isn't enough to be used. Disks in /dev will only be usable if they are not only physically present, but also 'mounted' - which is the linux equivalent of being introduced to someone. It's not enough to be merely present, you have to have been also introduced in order to be used.

/mnt defines mountpoints: these are just names by which disks in /dev can become known, if the occasion arises. So being in /dev and /mnt is a good start t becoming useful, but there's still more to it. 

/media contains mounted disks: ie, disks that are both physically present and have been 'introduced, as it were', to the computer because they hahve a mountpoint. ONly if you're in /dev and /mnt and /media can you be used. Is that right?

SO: 
if a disk is not visible in /dev, does that mean there's probably a hardware problem?

---

### Post by igknighted on 2008-10-29
/dev... well, i'll leave that alone.  You're not entirely right, but I can't explain why.

/mnt is for permanently attached drives (in the traditional unix sense).  So if you have 3 hard drives (or partitions), then they would get mounted there.  /media is for removable storage, like cd's, flash drives, network drives, etc.

These are guidelines though (the use of /mnt and /media).  You can actually mount any drive at any location (in your home folder, in /... anywhere).  Ubuntu chooses to mount all drives in /media for whatever reason, and honestly it really doesn't matter.

---

### Post by _sAm_ on 2008-10-29
Overview here; [http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)

Isn't the different between /media and /mnt that stuff in /media will show up as icons on the desktop to make it more easy(for some).

---

### Post by igknighted on 2008-10-29
> **_sAm_ said:**
> Overview here; [http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)

Isn't the different between /media and /mnt that stuff in /media will show up as icons on the desktop to make it more easy(for some).

I believe that is the result of mounting everything to /media, rather than the reason for mounting everything there.

---

### Post by ginestre on 2008-10-29
Thanks for that. 

SO- if a device isn't in /dev does that mean it's a hardware problem? Perhaps it's not 'available' because it's broken? Or perhaps it is invisible because whilst it's there and not broken, it's simply not been detected? Is there some way to check which of these is the case?

---

### Post by Nepherte on 2008-10-29
Is the drive detected in bios when you startup your computer?

```
sudo fdisk -l
```
shows the detected disks and their partitions but it relies on /dev, so yes if it's not in /dev I'd suspect a hardware problem.

---

### Post by igknighted on 2008-10-29
> **ginestre said:**
> Thanks for that. 

SO- if a device isn't in /dev does that mean it's a hardware problem? Perhaps it's not 'available' because it's broken? Or perhaps it is invisible because whilst it's there and not broken, it's simply not been detected? Is there some way to check which of these is the case?

You probably have a lot of 'devices' in /dev that aren't attached to your computer.  As far as I understand, /dev contains essentially addresses of where hardware should be, regardless of whether it is there or not.  What piece of hardware are you concerned about?  Typically, the commands 'lsusb' and 'lspci' are the best ways to determine whether a given piece of hardware is recognized.

---

### Post by ginestre on 2008-10-29
Thanks, yet again. I'm interested in a MAXTOR STM325082OAS hard drive that the bios does see but which ubuntu won't. It isn't listed by fdisk or in /dev, though /dev has a lot of stuff -ttty etc - that could be anything as far as I know. But there are no hd* or sd* entries. 

I'll reboot and try lspci - it didn't give anything I could understand yesterday, but I don't remember what it gave. However, if the disk is NOT recognised, how can I force recognition?

I'm using the live cd of 8.04, by the way, and trying to install.

---

### Post by igknighted on 2008-10-29
You'll be looking for an ide or sata controller, not the actual disk.  A drive can't have a driver issue, but the controller can (this is a chip, usually on the motherboard).  It's possible you are having issues with Ubuntu recognizing this.

EDIT: This is what the relevant line from lspci looks like for me:
```
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
```

---

### Post by germanix on 2008-10-29
> /dev contains (amongst other devices) some pointers to physically present disks. But being in /dev isn't enough to be used. Disks in /dev will only be usable if they are not only physically present, but also 'mounted' - which is the linux equivalent of being introduced to someone. It's not enough to be merely present, you have to have been also introduced in order to be used.

/Dev is where the files that control the peripherals live. These are the files that talk to the printer, disk drives, usb devices etc. if these devices are not present than obviously as you yourself noted, they cannot be talked to. If they are there, they are normally automatically mounted, or under circumstances you may have to mount them yourself.

---

### Post by ginestre on 2008-10-29
OK, so it looks like ubuntu doesn't recognise the drive. Is there some way to tickle it into submission? Or, to put it another way, what does it actually look for, when it's looking and fails to see the disk? Both BIOS and windows can see it, so it must somehow be a communication issue with ubuntu and this disk, I think.

---

### Post by ginestre on 2008-10-29
As always, thanks for your time and your trouble. You do all really make the difference! 

Below I've pasted the complete output from lspci, from which I can see the following (I presume relevant) 4  lines- but which is doing what? Does the fact that these entries show up in lspci mean they are somehow visible? Where do I go from here?
.....

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)


02:00.0 SATA controller: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02) 
............

COMPLETE LISTING just in case

<code>

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)
02:00.0 SATA controller: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
</code>

---

### Post by ginestre on 2008-10-29
I found this bug report, which seems to be my case

[https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/244363](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/244363)

but it's way over my head, and I don't really follow what the solution offered is- assuming that I've understood correctly and this is my problem. Grateful for pointers, as always.

---

### Post by ginestre on 2008-10-29
I seem to have moved on here: I booted with the IRQPOLL option, and the disk became visible. I have no idea why- on googling the name of my SATA controller: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02) I found a suggestion to use this command on boot, and it worked. But what on earth is IRQPOLL?

---

### Post by unutbu on 2008-10-29
Hi ginestre, I'm glad to hear you've found a way to make your hard drive visible to Linux.
The linux kernel source documentation (/usr/src/linux-2.6.25/Documentation/kernel-parameters.txt) says this about irqpoll:
```

irqpoll		[HW]
			When an interrupt is not handled search all handlers
			for it. Also check all handlers each timer
			interrupt. Intended to get systems with badly broken
			firmware running.
```

According to [http://en.wikipedia.org/wiki/Interrupt_request](http://en.wikipedia.org/wiki/Interrupt_request) the Linux kernel relies on interrupt requests (irqs) to communicate with hardware devices. For some reason the SATA controller's irqs were not getting handled properly. 

I really don't understand this very well, so I thank you for giving us this example of how this kernel boot option can be used successfully.

---

