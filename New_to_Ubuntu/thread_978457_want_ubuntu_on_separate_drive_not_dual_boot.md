---
title: "want ubuntu on separate drive not dual boot"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Yumpin_Yimminie on 2008-11-11
I just installed a second hard drive on my computer.  It is an IDE hard drive that is 250 GB in size.  Have very little experience with Ubuntu, so please be gentle regarding instructions.

At this time I am strongly tethered to Windows XP since I use some programs that are only written for Windows and have no similar programs in Linux.  Currently I'm not ready to handle the challenges of 'Wine.'

What I would like to do is install Ubuntu on the IDE hard drive.  **But not have a dual boot system as such**.  Instead I would like my system by default to boot up to Windows XP.  When I want to run Ubuntu I would like to change the boot order using the boot order change menu that is available when first turning on the computer.  For my computer system I can hit the F12 key as the computer is starting to boot and it gives a boot change menu.  From there I could select the IDE hard drive and hopefully boot right into Ubuntu.

Windows XP is showing that the IDE hard drive has actually 236 GB available.  I would like to allow a grand total of about 90 GB for Ubuntu and Ubuntu specific data.  The remainder of about 146 GB I would like to use as back up for Windows XP and Windows XP data files.  

I'm hoping you could give me the specific configurations to put into the live install so that I could:

1)  avoid the dual boot menu when I turn on the computer.
2)  the exact designations for the partitioning of the hard drive for Ubuntu.

Your help is greatly appreciated.  Thank you.

Have a Great Day,
Jim

---

### Post by bumanie on 2008-11-11
All you need to do is install ubuntu to the second hard drive whilst the hard drive you have windows on is unplugged. To get the drive partitioned how you want, I would suggest getting gparted live cd and using it to pre-partition 90gbg to ext3 filesystem and the remaining space to ntfs. When installing ubuntu at its partitioning stage direct the installation to the 90gb ext3 partition and it will set itself up from there. Post back if this is not clear, but the process should be simple, also as you have your main windows drive unplugged, you can't muck it up so give it a go.

---

