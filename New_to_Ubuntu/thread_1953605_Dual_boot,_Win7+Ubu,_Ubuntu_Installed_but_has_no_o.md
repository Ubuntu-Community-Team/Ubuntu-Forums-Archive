---
title: "Dual boot, Win7+Ubu, Ubuntu Installed but has no option to boot."
date: 2012-04-06
forum: New to Ubuntu
---

### Post by Jake5 on 2012-04-06
Hey, Title pretty much says it. I have a computer that I partitioned off the HDD on to setup a dual boot system. I have Windows 7 on the first partition, 100gigs NTFS, I have Ubuntu on the second, Ext4 200gig. I ran the ubuntu installation, but when I was prompted to restart, I did so and the computer rebooted to Windows. I have no options to select from like on my other dual boot setup. Wondering if I have to change something in the BIOS?

---

### Post by PhantomTurtle on 2012-04-06
You need to add an entry to the Windows boot menu using easy bcd ([http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)) (free for non-commercial use). Open it and add an entry for Ubuntu and set it to grub2, not grub legacy. Here is a tutorial for it with pictures: [http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/2/]("http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/2/").

---

### Post by Boyntonstu on 2012-04-06
> **Jake5 said:**
> Hey, Title pretty much says it. I have a computer that I partitioned off the HDD on to setup a dual boot system. I have Windows 7 on the first partition, 100gigs NTFS, I have Ubuntu on the second, Ext4 200gig. I ran the ubuntu installation, but when I was prompted to restart, I did so and the computer rebooted to Windows. I have no options to select from like on my other dual boot setup. Wondering if I have to change something in the BIOS?

Hi!

I am probably too much of a nube to give advice, but I can tell you what I use.

I created a live CD.

It bypasses the bios and it asks what sector or what drive you wish to select to boot.

Works fine.  It was Yumi or Plop, I don't remember which.

---

### Post by oldfred on 2012-04-06
Did you do a full partitioned install or just install wubi to another partition?

If a full install the easyBCD may work and some here that are primarily Windows 7 users find it works well. If running proprietary software that uses DRM, easyBCD may work better than grub as the DRM software often just overwrites grub. Grub has created work arounds for several of the popular DRM like Flexnet which is used by 

But grub2 is the Ubuntu boot loader and lets you boot Windows and many other systems.

You can often easily repair system with this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Jake5 on 2012-04-06
So I have Windows 7 in the first partition of the HDD, on the second partition i have Ubuntu, I did as suggested by Phantom Turtle. Now I do get an option to boot Ubuntu, however it kicks me onto a black screen with the grub> command line. I have no idea what to do from here, and I suspect that the program did not find the kernel in the correct partition. I suspect this because it seems that this tutorial is for booting from two different hard drives.

---

### Post by Jake5 on 2012-04-06
> **oldfred said:**
> Did you do a full partitioned install or just install wubi to another partition?

If a full install the easyBCD may work and some here that are primarily Windows 7 users find it works well. If running proprietary software that uses DRM, easyBCD may work better than grub as the DRM software often just overwrites grub. Grub has created work arounds for several of the popular DRM like Flexnet which is used by 

But grub2 is the Ubuntu boot loader and lets you boot Windows and many other systems.

You can often easily repair system with this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.
I did in fact do a full partition install, at least I think so... I partitioned off the hard disk before I installed windows on it. I have a 100gig NTFS partition for windows, A 200gig ext4 partition for ubuntu, Another 100gig ext2 partition with nothing on it yet, then I have three appx 20 gig ext2 partitions again with nothing on them yet, and finally a 2 gig linux swap partition, I have installed ubuntu on the second partition and have verified that it is there using a live cd and gparted. I am following your boot repair link now and will post the results shortly. Thanks..

---

