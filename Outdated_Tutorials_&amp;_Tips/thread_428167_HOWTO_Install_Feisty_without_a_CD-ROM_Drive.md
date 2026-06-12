---
title: "HOWTO: Install Feisty without a CD-ROM Drive"
date: 2007-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Flarebringer on 2007-04-30
So you want to install to a system without a cd-rom drive. Or maybe the LiveCD is giving you that irritating tty error thingy.

If you have a sufficiently large hard drive with enough space free to have both Windows and Ubuntu, go for a no-cd install. Disclaimer: I in no way claim to be a linux guru: this is simply the method I worked out after hours of tears, sweat, and fixing my partition tables after yet another mishap. I give full credit to two excellent guides that I basically mixed together for my method: 
1) [http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948), which goes into detail but uses the outdated hoary hedgehog version of ubuntu
2) [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html) which assumes a little more knowledge of grub and linux than many newbies have.
This guide aims to mix the ease-of-use of the former source with the timeliness of the latter.

Obviously, this is a guide written by a newbie for newbies, so you´ll want to look elsewhere for anything but the most rudimentary support, although I´ll try to help as I may. On the other hand, my comparative stupidity at Linux means that this guide is written out step-by-step, assuming no knowledge of GRUB or Linux, since I didn´t have any when I puzzled this method out off of the older guides on the subject. I will assume basic knowledge of stuff like moving files and editing text and that sort of thing. The most complicated thing in here is partitioning, but that´s not too hard to learn the ropes of if you&#341;e careful. Eat your heart out, first-time Linux migrators. 

Remember, everything in here is slightly to stupidly risky, and if you mess something up, uh...don´t ask me, since I don´t know what to do if you blow up your master boot record or something either.

This method itself was tested on a Pentium 4 with half a gig of RAM, using the 32-bit i386 installer, and was written for Ubuntu 7.04 (Feisty Fawn).

You will need:
- An working internet connection, to download the stuff we need
- The ALTERNATE version of the iso file for your chosen Ubuntu flavor
- Your brain. This method is not for someone with no computer knowledge.

First, you need to repartition your hard drive. Partition Magic or the like should let you do it (Obviously, repartitioning is fraught with risk: think everything through, and if in doubt back up.). Assuming you have a single Windows partition, shrink it down and add a small (maybe 1 GB partition). So you should have a primary bootable windows partition, a tiny primary partition, and free space adding up to however much you want to give Ubuntu. From now on, I´ll call the primary windows partition C: and, for lack of a better name, the tiny one will be imaginatively called ¨the tiny partition¨.

As a concrete example, my system started as a single 120 GB windows hard drive, C:. I used Partition Magic to shrink the 120 GB single partition into a 95 GB one, leaving 25 GB of free space after it. I then used Partition Magic again to make a new logical partition after the primary one but before the free space, sizing a single gigabyte. End result: a 94 GB Windows partition, a 1 GB empty partition, and 25 GB of unallocated space, in order. If it matters, I used the NTFS file system. 

You´ll need to get GRUB going. (Warning: The following steps are quite easy to screw up and if you do, may render your system unbootable for all time to come. Backups are indicated.) Get ahold of the GRUB for DOS package ([http://linux.softpedia.com/get/System/Boot/GRUB-for-DOS-3507.shtml](http://linux.softpedia.com/get/System/Boot/GRUB-for-DOS-3507.shtml) has a copy) and take out the files grldr and menu.lst. Glrdr should go into the root of your primary hard drive (that&#347; probably C:). Make a folder in C: called boot, and make a folder in that one called grub. Put menu.lst into it.

You also need to edit menu.lst with a text editor. At the end of it, append the following, where **X** is the partition number of your tiny partition, the first partition being 0. As a concrete example, in the scenario I gave above, the windows partition would be number 0, the tiny partition is number 1, and the free space isn´t a partition so it doesn´t get the number. So I´d set the line to root (hd0, 1), since my partition number 1 is the tiny one.

```
title Ubuntu
root (hd0,**x**)
kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw &#8211;
initrd /boot/initrd.gz
```

Next, prep the tiny partition, which is currently empty. Make a folder in it called boot. You need to put 3 files into /boot:
1) The .iso file of your ubuntu distribution. *it must be the alternate CD!* Remember to checksum it.
2) initrd.gz ([http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/))
3) vmlinuz. If like me you have problems getting vmlinuz from the site above, you can rip it from the Ubuntu CD: just search it for a file called vmlinuz and copy it into the boot folder.

Lastly, we need to change boot.ini. This is the dangerous part. Windows makes it fireproof, earthquake-proof, user-proof, etc. by default. You need to go into command prompt and enter this command: 

```
attrib -a -r -s -h c:\boot.ini
``` 

Now, you can go into C: and edit boot.ini. Append the following command into the end of the file.

```
C:\grldr="GRUB"
```

Oh, if you´re nervous about one of the most important and sensitive files in your computer (boot.ini is laserproof by default for a reason) you can reverse the command we used to unlock it. attrib +a +r +s +h c:\boot.ini should do the trick.

The upshot should come something like this.
When you turn your computer, it checks boot.ini for what it should do. Boot.ini tells the computer to look to the grldr file you put into C:, and give you a choice between starting grub or windows. When you start grub, it reads the menu.lst file you modified, and sees our addition: the Ubuntu entry. When you select that, it reads our entry, which hopefully points to the correct partition, and starts the text-based ubuntu install. When it asks you how you want your partitions done, tell it to do a guided install with the largest continuous free space.

Last note: try to do this near another computer that´s connected to the internet, so you can go onto the ´net and ask questions if you blow something.

End results: One dual-booting system with both Linux and Windows.

Things that could go wrong (Ongoing list) :
1) I turned the computer on, and it tells me that it has an error loading the operating system:
Either the computer is trying to boot a hard drive other than the one it's supposed to be doing, or boot.ini is broken, or something else that I haven't thought of happened. Hope you backed up, my friend. In my case, the first time, I forgot to MD5 the Alternate ISO, the installation exploded, and I had to reboot. The installer had set the linux partition it made as the booting one, but the install failed, so there was no OS on that partition. A little work with a boot disk got me my OS back. 
2) GRUB tells me that it can't mount the drive when I tell it to install Ubuntu:
You made the tiny partition logical, not primary. It's trivial to change it, but remember that you can't have more than 4 primary partitions.
3) GRUB tells me that it can't find a file:
Either you chose the wrong partition when you edited menu.lst, or the tiny partition is improperly configured. Check to make sure that your tiny partition has a boot folder with vmlinuz, initrd.gz, and the ISO file in it. If it does, make sure that the menu.lst entry points to the right partition (theoretically, trial-and-error should work). In my case, I tried to download vmlinuz from the Ubuntu archives instead of ripping it from disk. Firefox read it as a .txt file instead of a plain file, so grub didn't see it.

---

### Post by codeslicer on 2007-05-03
Nice job:KS :-P :lol: :grin: 8-) Although later I decided to burn a third cd, (I have dapper and edgy cds), hoping that this time my rt61 card will work :)

---

### Post by nonlinear on 2007-05-06
thanks for this man, worked great.  i wish i would've jsut followed your instructions from the beginning, rather than wasitng 3 hours trying to 'save time' using instlux :)

---

### Post by gsruizvtec on 2007-05-14
Hey I followed this guide but for some reason when I go into grub I dont see ubuntu only mandrake and linux.  I have my primary windows partition and my smally "tiny" one is drive F is (0,1) not right?  Its the only other partition on my pc other then my C drive.  Also on that drive it says new volume is that right?  Any help would be great im kinda excited to start playin with linux I've been trying to burn a proper cd now for 2 weeks heh.

Dan

---

### Post by envmyz on 2007-05-15
Hey, Thanks for guide.  I've been messing around trying to get Ubuntu on my P1120 (nocd).

For those who dont want to mess with the boot.ini try this..

Create an unpartioned space, thats all.  One partition for Windoz and one black unformatted.

[http://downloads.sourceforge.net/instlux/instluxNETUbuntu6_06english.exe?modtime=1150144115&big_mirror=0](http://downloads.sourceforge.net/instlux/instluxNETUbuntu6_06english.exe?modtime=1150144115&big_mirror=0)

Download instlux, run the application and choose to reboot later.

Download the initrd.gz and vmlinuz
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/)

After downloading (Put them on your desktop)
Rename vmlinuz to linux

Copy these two file to the c:\instluxNETUbuntu6_06 folder (overwrite them)

Copy the alt_feisty ISO to the root of C:\

Reboot computer, select Ubuntu, then again.

ALL DONE!!

Reboot into windows after finished and instlux will un-install itself and your all set!!

Hope this helps, Cheers

---

