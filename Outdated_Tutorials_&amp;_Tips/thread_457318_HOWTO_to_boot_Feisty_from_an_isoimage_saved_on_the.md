---
title: "HOWTO to boot Feisty from an isoimage saved on the harddisk (fromiso patch)"
date: 2007-05-28
forum: Outdated Tutorials &amp; Tips
---

### Post by rna on 2007-05-28
I know there are a few other threads dealing with booting Ubuntu directly from the harddisk or through netboot without requiring  a cdrom, but this takes a slightly different approach than the other posts.  I patched the initrd file to add the 'fromiso' option similar to this [[COLOR="Blue"]cheatcode[/COLOR]]("http://kanotix.com/FAQ-id_cat-63.html#q298") in Kanotix. The advantage is that you dont need to extract the iso file or setup tftp for netboot. I find it useful to try out new releases.

*** Update [2/28/2009] ***
I have written a script to automate the patch process described in this thread. 

Fromiso_patcher v0.1, 2/28/2009 Initial release. 
Tested on Feisty, Hardy, Intrepid and Jaunty (alpha 1-3)

To use:
```
Download the file **([attach]104838[/attach])** 
tar -zxvf fromiso_patcher_v0.1.tar.gz 
cd fromiso_patcher
sudo ./patcher.sh <isofile>

```

Usage: sudo ./patcher.sh <ISOPATH> [<PATCHFILE>] 
   ISOPATH: path to isoimage (REQUIRED)
   PATCHFILE: specify patch to apply. This is optional. The default is to check the README.diskdefines file and select the correct patch.

*** Original Instructions Follow ***

Requirements: A working linux system, with grub.

[LIST=1]
Create a folder to hold iso image and boot files. Change path as desired.

***Caveat***
I havent tried an install-to-disk after booting the live-system, but it can't be good to try and install Ubuntu on the partition containing the isoimage. I would recommend creating the fromiso folder on a partition that wont be touched during install.
```
	
mkdir /fromiso 
cd /fromiso 
```

[*] Save ubuntu isoimage to: /fromiso/feisty.iso
[*]Save patch **([attach]33693[/attach])** to: /fromiso/fromiso_patch.txt
[*]Extract boot files from isoimage
```

	test ! -d /mnt/isoimage/ && mkdir /mnt/isoimage
	mount -o loop feisty.iso /mnt/isoimage
	cp /mnt/isoimage/casper/initrd.gz .
	cp /mnt/isoimage/casper/vmlinuz .
        umount /mnt/isoimage 
```
[*]Extract and patch initrd
```

	mkdir extract
	cd extract
	zcat ../initrd.gz|cpio -i
	patch -p1 < ../fromiso_patch.txt
	find . |cpio -H newc -o |gzip -9 >../initrd_isopatch.gz
	cd ..
```
[*]Append a section to grub. Remember to change device paths appropriately.
```

	title Ubuntu Feisty from ISO
        kernel (hd1,1)/fromiso/vmlinuz ramdisk_size=100000 boot=casper root=/dev/ram0 fromiso=/dev/hdb2/fromiso/feisty.iso
        initrd (hd1,1)/fromiso/initrd_isopatch.gz
```
[*]Reboot, Select Ubuntu Feisty from ISO in grub[/list]

---

### Post by ffz on 2008-04-28
I tried to do this with hardy and it didn't work. Do i need to change something?

---

### Post by rna on 2008-04-28
You are right, Heron needed a minor fix. I've attached a new patch which works for me.

---

### Post by Jose Catre-Vandis on 2008-04-29
This looks very handy. Can you tell me... once you have patched the boot files, can you theoretically place the fromiso directory anywhere, on any partition, perhaps even on a CD / DVD (I'll explain)? If on a CD/DVD would isolinux perform the same magic as grub? Do you know of, or how to create, a similar patch for alternate CD's?

---

### Post by rna on 2008-04-29
I think you should be able to place the image on any device, though I havent tried putting it on a CD/DVD. My motivation for this was to avoid having to use a CD ;) However I can imagine that you could have multiple distros on a DVD and have a menu to choose from at boot time. Is that what you are aiming for? 

The fromiso patch is pretty simple, so it should be fairly straightforward to patch other distros. Extracting the initrd image will give you an idea of how the boot scripts are setup.

I dont have much experience with isolinux but i think it should work the same way.

---

### Post by Jose Catre-Vandis on 2008-04-30
Thanks. I can see it working with Live Cds, but it would be different with alternate Ubuntu CDs as there is no casper. I have tried some editing within initrd.gz on alternates but the installation stalls on bootstrap-base, giving errors about release names. Can't see where this is looking though, as it finds the release and cd name earlier on.

---

### Post by Pondussi on 2008-11-19
Does it work with Kubuntu Intrepid too? When I try using the Hardy-Patch on the Intrepid-initrd I get a "patch: **** strip count l is not a number"?

---

### Post by rna on 2008-11-19
> **Pondussi said:**
> Does it work with Kubuntu Intrepid too? When I try using the Hardy-Patch on the Intrepid-initrd I get a "patch: **** strip count l is not a number"?
I havent tried Kubuntu, but it works with the gnome intrepid iso. Remember to use the patch for Hardy. The error you posted looks like there might have been a typo while patching. Make sure that the 1 in -p1 is the number 1 not the letter l.

patch -p1 < ../fromiso_patch.txt

---

### Post by Pondussi on 2008-11-23
You are so right - thanks!

---

### Post by Pondussi on 2008-11-23
Obviously the patch applied - but I cannot boot into kubuntu from the iso. Booting stops with an 
"ALERT! /dev/ram0 does not exist. Dropping to a shell!" How can I figure out what I have to use as root= in the menu.lst entry instead of /dev/ram0?

---

### Post by eramax on 2008-11-23
i have a problem with these two lines 

	```
zcat ../initrd.gz|cpio -i
	patch -p1 < ../fromiso_patch.txt
```
the first give me a large output about "No such file or directory" and "Permission denied" even when execute by root
such as this output 
```
cpio: scripts/casper: Cannot open: No such file or directory
cpio: scripts/casper-functions: Cannot open: No such file or directory
cpio: scripts/casper-helpers: Cannot open: No such file or directory
cpio: scripts/lupin-helpers: Cannot open: No such file or directory
cpio: init: Cannot open: Permission denied
cpio: var: Cannot mkdir: Permission denied
cpio: var/run: Cannot mkdir: No such file or directory
cpio: usr: Cannot mkdir: Permission denied
cpio: usr/lib: Cannot mkdir: No such file or directory
cpio: usr/lib/usplash: Cannot mkdir: No such file or directory
cpio: usr/lib/usplash/usplash-artwork.so: Cannot open: No such file or directory
cpio: lib/modules/2.6.27-7-generic/kernel/drivers/video/vesafb.ko: Cannot open: No such file or directory
48712 blocks
```
 the other give me a questions :
```
eramax@eramax-desktop:/fromiso/extract$ patch -p1 < ../fromiso_patch.txt
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -uNr orig/init extract/init
|--- orig/init  2008-04-28 21:33:31.000000000 -0400
|+++ extract/init       2008-04-28 20:52:29.000000000 -0400
--------------------------
File to patch: initrd.gz
initrd.gz: No such file or directory
Skip this patch? [y]   
```
what is wrong ?
thanks

---

### Post by Ani on 2008-11-26
rna, could you upgrade your patch for Ubuntu 9.04?

---

### Post by rna on 2008-11-27
> **Ani said:**
> rna, could you upgrade your patch for Ubuntu 9.04?

Which image of 9.04 are you patching?
Have you tried applying the Hardy patch? If so what errors do you see?

---

### Post by rna on 2008-11-27
> **eramax said:**
> i have a problem with these two lines 

	```
zcat ../initrd.gz|cpio -i
	patch -p1 < ../fromiso_patch.txt
```
the first give me a large output about "No such file or directory" and "Permission denied" even when execute by root
such as this output 
```
cpio: scripts/casper: Cannot open: No such file or directory
cpio: scripts/casper-functions: Cannot open: No such file or directory
cpio: scripts/casper-helpers: Cannot open: No such file or directory
cpio: scripts/lupin-helpers: Cannot open: No such file or directory
cpio: init: Cannot open: Permission denied
cpio: var: Cannot mkdir: Permission denied
cpio: var/run: Cannot mkdir: No such file or directory
cpio: usr: Cannot mkdir: Permission denied
cpio: usr/lib: Cannot mkdir: No such file or directory
cpio: usr/lib/usplash: Cannot mkdir: No such file or directory
cpio: usr/lib/usplash/usplash-artwork.so: Cannot open: No such file or directory
cpio: lib/modules/2.6.27-7-generic/kernel/drivers/video/vesafb.ko: Cannot open: No such file or directory
48712 blocks
```
 the other give me a questions :
```
eramax@eramax-desktop:/fromiso/extract$ patch -p1 < ../fromiso_patch.txt
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -uNr orig/init extract/init
|--- orig/init  2008-04-28 21:33:31.000000000 -0400
|+++ extract/init       2008-04-28 20:52:29.000000000 -0400
--------------------------
File to patch: initrd.gz
initrd.gz: No such file or directory
Skip this patch? [y]   
```
what is wrong ?
thanks

I cant replicate your errors. Looks like a file permissions issue. Make sure you have write access to the folder you are extracting to.

---

### Post by Ani on 2008-12-01
> **rna said:**
> Which image of 9.04 are you patching?
Have you tried applying the Hardy patch? If so what errors do you see?
I am patching jaunty-desktop-amd64.iso

I have tried the Hardy patch and it seems to work. I think a few lines are off a little offset.

patching file init
Hunk #1 succeeded at 149 (offset 21 lines).
patching file scripts/casper
Hunk #1 succeeded at 550 with fuzz 1.
Hunk #2 succeeded at 610 (offset 2 lines).

---

### Post by centguy on 2009-01-10
The idea look interesting. Can someone provide a detailed description for 
ubuntu-8.10-desktop-i386.iso (took me some time to download this file so I don't fancy to download an older ubuntu..) ? I don't mind extracting the the content of iso file and put everything under /dev/sda7. 
In fact, I already have 

[root@fc9 sda7]# ls /sda7
autorun.inf  dists    isolinux    pics  preseed             ubuntu     wubi.exe
casper       install  md5sum.txt  pool  README.diskdefines  umenu.exe

I just need the magic touch of the stanza in the menu.lst.

I tried the following but it does not work..

title Ubuntu LiveCD @ sda7
       root (hd0,3)
       kernel /boot/vmlinuz-Ubuntu-8.10 file=/boot/ubuntu.seed root=/dev/sda7/casper
       initrd /boot/initrd-Ubuntu-8.10.gz

Somehow, /dev/sda7/casper is not found..

Thanks for the help!

---

### Post by rna on 2009-01-10
Please see my original post on this thread. You don't need to extract the whole iso to disk, just the boot files. Patch the initrd using the Hardy patch. The boot folder should contain the original iso, the patched initrd, and vmlinuz. Use the grub stanza as described (updating the disk location as required). Post back if you run into problems.

---

### Post by centguy on 2009-01-10
Thanks for the reply. You know what ? I am using a Hardy Ubuntu LiveCD firefox to reply this email (through wireless, just to show off that wireless work out of the box!).

Since I didn't receive the reply in time, I went to digest the entire posts in this thread and decided that I may have better luck with 8.04 (Hardy).
So I downloaded the ISO and repeat the tutuorial and it worked !

I was not too sure about the compatibility of the 8.04 patch file for 8.10, plus I have not done anything like this for ubuntu, that's why I tried something that has a higher chance of success.
It seems there is no mention of the Hardy patch file works (Ani's post scare me quite a bit) for Intrepid iso, I don't know.

Keep up with this good effort rna for future releases of ubuntu !!

---

### Post by rna on 2009-01-11
I can confirm that the Hardy patch works with Intrepid. The patch output from Ani's post seems to suggest that it applied cleanly to Jaunty as well.

---

### Post by centguy on 2009-01-11
Thanks for confirming rna. Any comments on unetbootin that can run on linux too ? Should I get serious with that ?

---

### Post by centguy on 2009-01-14
I am replying from Intrepid Ibex Live CD booted from the hard drive, so it works.

---

### Post by hal2000@megamail.pt on 2009-01-21
Hi, i have patch the ubuntu 8.10 with the patch for hardy and it worked, i boot up from the iso file that was on my /dev/hda2.

     I tryed to copy the same iso file to a usb pendrive configure grub for fromiso=/dev/sdb1/ubuntu/file.iso 
     
     It starts to boot, but after a while it hangs, stops for some minutes and then show prompt #initramfs.

     Is there any way to boot fromiso when the file is on a usb pendrive ?     
     I guess the problem is when try to mount the iso file from usb, the pendrive is fat32.

     Any ideas to correct this problem ?

     Thank you

---

### Post by Ani on 2009-02-27
Jaunty iso images used to boot just fine for a long time now. But recently they stopped working. The boot process goes for a long time, and then it gets to the part where it remounts the root partition, and it keeps repeating a similar phrase for a long time.

rna, can you test your patch on latest jaunty 64 bit iso files?

---

### Post by rna on 2009-02-28
@Ani 
Is this the alpha-5 release of Jaunty?
Can you post the patch output? Does it apply cleanly?
Also is it a 64-bit issue, do you face the same problem with the 32-bit iso?

---

### Post by rna on 2009-02-28
Just an update to say that I have written a script to automate the patch process described in this thread. 

Fromiso_patcher v0.1, 2/28/2009 Initial release. 
Tested on Feisty, Hardy, Intrepid and Jaunty (alpha 1-3)

To use:
```
Download the file **([attach]104838[/attach])** 
tar -zxvf fromiso_patcher_v0.1.tar.gz 
cd fromiso_patcher
sudo ./patcher.sh <isofile>

```

Usage: sudo ./patcher.sh <ISOPATH> [<PATCHFILE>] 
   ISOPATH: path to isoimage (REQUIRED)
   PATCHFILE: specify patch to apply. This is optional. The default is to check the README.diskdefines file and select the correct patch.

---

### Post by Ani on 2009-03-03
@rna:

I just tried today's jaunty 64 bit image, and it gives the same error message while booting repeatedly:
EXT3-fs: remounting the filesystem with ordered mode ...

here are the results of patching the file. it seems to have applied cleanly:

patching file init
Hunk #1 succeeded at 149 (offset 21 lines).
patching file scripts/casper
Hunk #1 succeeded at 553 with fuzz 1 (offset 3 lines).
Hunk #2 succeeded at 613 (offset 5 lines).
52576 blocks

I haven't tried 32 bit version yet. I'll let you know when I try it.

---

### Post by Ani on 2009-03-03
today's 32 bit version of jaunty gives the same error message "mounted filesystem with ordered data mode"

---

### Post by rna on 2009-03-05
> **Ani said:**
> today's 32 bit version of jaunty gives the same error message "mounted filesystem with ordered data mode"

I dont have access to a 64-bit machine, seems to work fine for me for 32-bit using the Hardy patch. Could you try with the patcher script? Also check if you are using the patched initrd.

---

### Post by Ani on 2009-03-06
I had accidentally screwed up my grub configuration file. That was causing the problem. Now it works very nicely. I am writing this comment from a LiveCD booted from my HDD. Sorry for wasting your time guys.

---

### Post by floborg on 2009-03-24
Not working for me.  I am trying to boot Intrepid from a hard drive with a Hardy installation.  The bootup drops to the initramfs shell after a while.

I noticed an error, though, when running the patcher script.  It called out line 99: command not found.  This is line 99 of the script:

```
patch -p1 < $patchfile
```

Any ideas?

---

### Post by floborg on 2009-03-24
Ok, it turns out that I did not have the "patch" package installed.  Is that not in a default install?  You might want to add a note about that.

With the patch package installed, I made the new initrd.gz and booted Intrepid.  I added a "splash" kernel option and the normal Ubuntu splash screen was shown, with some logging.  It seemed to run like a LiveCD.  It didn't, however, reboot when I selected reboot.  Instead, my monitor shut off while the tower kept running.

Overall, a nice utility.  They should put a fromiso option in the official releases!

---

### Post by rna on 2009-03-25
@floborg
Thanks for heads up. I'll add a check for patch in the next update.
You might consider voting for the feature in Brainstorm ([here]("http://brainstorm.ubuntu.com/idea/9711/")).

---

### Post by floborg on 2009-03-25
> **rna said:**
> @floborg
Thanks for heads up. I'll add a check for patch in the next update.
You might consider voting for the feature in Brainstorm ([here]("http://brainstorm.ubuntu.com/idea/9711/")).

Thanks, but I don't feel like registering.  They are bad-mouthing your suggestion over there.  I think this thread makes it fairly clear what is requested, but it's like they didn't read it.  There was one mention of Unetbootin, which appears to have added a frugal install option for Linux.  I have a thread on that is getting no views.

Any ideas on why the Intrepid reboot command fails for me?

---

### Post by rna on 2009-03-26
> **floborg said:**
> Thanks, but I don't feel like registering.  They are bad-mouthing your suggestion over there.  I think this thread makes it fairly clear what is requested, but it's like they didn't read it.  There was one mention of Unetbootin, which appears to have added a frugal install option for Linux.  I have a thread on that is getting no views.

Unetbootin definitely offers a general and user-friendly solution the problem. But it still involves extracting the entire iso to the usb drive which takes time. The fromiso approach works well for me but is perhaps too niche for general use.

> Any ideas on why the Intrepid reboot command fails for me?

I hadnt noticed it earlier but I run into the same issue while rebooting. It is waiting for a key press, since the normal sequence when booting off a cdrom is to eject the CD and wait for the user to press ENTER. 

One way to fix it would have been to patch the shutdown scripts on the iso image and then remaster the iso. That seemed a bit overkill. However while poking around the source I found that the relevant script aborts if it detects the find_iso kernel parameter. Try appending the following empty parameter to the kernel line of your grub stanza and see if it works. It is a bit of a hack, but worked for me.
```
find_iso=
```

PS: This also points to the existence of code in the official release that provided fromiso like functionality but seems to have fallen out of favor. I cant find much documentation for the find_iso parameter except for this entry in the Gutsy guide: 
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_boot_Ubuntu_from_ISO_image_on_hard_drive_or_USB_stick]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_boot_Ubuntu_from_ISO_image_on_hard_drive_or_USB_stick")

---

### Post by locutus42 on 2009-04-15
just a couple of notes on this,

make sure the "fromiso:/dev/xxxN/fromiso/filename.iso" section uses the SCSI based representation( ex. /dev/**[COLOR="Red"]s[/COLOR]**da1/fromiso/filename.iso ). On my Hardy system, it's an /dev/hda1 name when but booting from the Jaunty kernel and initrd image it uses the SCSI device names.

[UPDATE: the following is now true for the daily build image. You **can** install to a partition on the same drive your iso image is on as long as it is another partition] If you use an older/existing GRUB bootloader and install to a partition, then you can't use ext4 and you'll need to format the target partition with an older mkfs.ext3 tool. Something about a 128bit vs 256bit ext3 or something like that.

I also tried moving the iso image onto a USB drive and set up the fromiso entry to use /dev/sdb1/.....iso but while the kernel finds the device and loads the drivers, something prevents the image from being used and the boot drops to the BusyBox prompt. This still occurs with the daily build as of 2009-04-15

UPDATE:
Not only is the partition dialog fixed( yes/no for unmounting mounted partitions ) but the timezone window is not one timezone off as it was for the PST zone the last time I tried it. Also fixed is in the final install screen under [advance] where you can not pick a partition for the boot loader to be installed in. I'm able to boot the Jaunty partition with an older version of grub after I format it to ext3 in Hardy first and **didn't** check format in the manual partition dialog.

---

### Post by rna on 2009-04-16
@locutus42
thanks for the update. I have not played with the latest images. Regarding booting off the USB stick, I suspect the image is not being mounted correctly. Can you take a look at the casper.log file from the bubsybox prompt ? It could also be that the filesystem type is not being detected properly. You could try formatting the USB drive as ext2.

---

### Post by floborg on 2009-04-16
> **rna said:**
> 
PS: This also points to the existence of code in the official release that provided fromiso like functionality but seems to have fallen out of favor. I cant find much documentation for the find_iso parameter except for this entry in the Gutsy guide: 
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_boot_Ubuntu_from_ISO_image_on_hard_drive_or_USB_stick]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_boot_Ubuntu_from_ISO_image_on_hard_drive_or_USB_stick")

I just found this:

[https://bugs.launchpad.net/ubuntu/+bug/94204]("https://bugs.launchpad.net/ubuntu/+bug/94204")

It suggests that Ubuntu has an iso-scan boot option, but it provides an example using Grub2.  As far as I know, Grub2 is not an official release, and Ubuntu doesn't install it.

---

### Post by floborg on 2009-04-17
Update to my previous post:

The "iso-scan/filename" boot option works.  I booted from an iso w/o the fromiso patcher.  Of course, I still had to extract the kernel and initial ramdisk, but neither needed any patching.  Here's the grub entry I used with the Kubuntu Jaunty Daily Build.

```
title  Kubuntu 9.04 "Jaunty Jackalope" - Beta i386 from iso
kernel (hd0,2)/fromiso/vmlinuz iso-scan/filename=/fromiso/jaunty-desktop-amd64.iso boot=casper quiet splash
initrd (hd0,2)/fromiso/initrd.gz
```

---

### Post by locutus42 on 2009-04-18
> **rna said:**
> @locutus42
thanks for the update. I have not played with the latest images. Regarding booting off the USB stick, I suspect the image is not being mounted correctly. Can you take a look at the casper.log file from the bubsybox prompt ? It could also be that the filesystem type is not being detected properly. You could try formatting the USB drive as ext2.

@rna
I just checked the filesystem on the USB drive and it's ext3 so there shouldn't be any problems mounting it. For the heck of it, maybe I'll try that iso-scan option and see if that does anything helpful.

---

### Post by locutus42 on 2009-04-28
still no go booting to an iso on a USB or SD card. The USB was ext3 while the SD was vfat. 

casper.log didn't say much but here goes:
```

Touch: /var/run/lupin-waited-for-dev no such file for directory
stdin: error 0
mount: mounting /dev/sda7 on /isodevice failed, invalid argument
Cannot mount /dev/sda7 on isodevice
```

my grub entry looked like this:
```

title           Kubuntu 9.04 i386 LiveCD.iso USB-Drive
kernel          (hd0,7)/boot/isolinux/ubuntu/vmlinuz ramdisk_size=100000 boot=casper root=/dev/ram0 iso-scan/filename=/dev/mmcblk0p1/jaunty-desktop.iso quiet splash i8042.reset
initrd          (hd0,7)/boot/isolinux/ubuntu/initrd.gz

```

I did mount the SD card from busybox on the isodevice mountpoint using /dev/mcblk0p1 without problem so I suspect it's just a scripting problem in the init processing. Maybe it doesn't mount USB or SD device before the loop command and so it's failing. /scripts/lupin-helper seems to be a good place to look.


Here is the casper.log file when trying to boot from USB:
```

Begin: Running /scripts/casper-premount ...
Done.
Done.
Begin: try_mount /dev/sdb1 /cdrom.isosrc ...
/init: line 1: cannot open /dev/sdb1: no such file
BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) multi-call binary

Usage: mount [flags] DEVICE NODE [-o options,more-options]

Mount a filesystem. Filesystem autodetection requires /proc be mounted.

Options:
	-a		Mount all filesystems in fstab
	-f		don't mount
	-i		Don't call /sbin/mount.<filesystem> helper
	-r		Read-only mount
	-t fs-type	Filesystem type
	-w		Read-write mount (default)
-o option:
	loop		Ignored (loop devices are autodetected)
	[a]sync		Writes are asynchronous / synchronous
	[no]atime	Disable / enable updates to inode access times
	[no]diratime	Disable / enable atime updates to directories
	[no]dev		Allow use of special device files / disallow them
	[no]exec	Allow use of executable files / disallow them
	[no]suid	Allow set-user-id-root programs / disallow them
	[r]shared	Convert [recursively] to a shared subtree
	[r]slave	Convert [recursively] to a slave subtree
	[r]private	Convert [recursively] to a private subtree
	[un]bindable	Make mount point [un]able to be bind mounted
	bind		Bind a directory to an additional location
	move		Relocate an existing mount point
	remount		Remount a mounted filesystem, changing its flags
	ro/rw		Mount for read-only / read-write

There are EVEN MORE flags that are specific to each filesystem
You'll have to see the written documentation for those filesystems

Cannot mount /dev/sdb1 on /cdrom.isosrc

```

---

### Post by hal2000@megamail.pt on 2009-05-14
Hi all, i have solve my problem, i tryed ubuntu 9.04 with the iso-scan option with the iso on a usb pen in vfat and it works, no need to patch.
      only need to extract vmlinuz and initrd from iso.

      Thanks to all for there help.

---

### Post by floborg on 2009-05-14
Now all we need is "img-scan"

---

### Post by domthehat on 2009-05-27
[EMAIL="hal2000@megamail.pt"]hal2000@megamail.pt[/EMAIL] - more details please?  Or your grub menu.lst entry?  

iso-scan didn't work for me.    

Locutus42, I was also trying to get it to boot a kernel stored on disk and then install (or run) from an ISO on a USB pendrive.    I used the patcher script to create a patched initrd.   

My grub entries looked a bit like this:    
kernel  (hd0,3)/fromiso/vmlinuz ramdisk_size=100000 boot=casper root=/dev/ram0 fromiso=/dev/sdb1/jaunty.iso vga=791   
initrd  (hd0,3)/fromiso/initrd.gz     

To begin with I was getting dumped to a busybox prompt and it appeared that the mount was failing with invalid options.  So in the hardy patch file I replaced "try_mount" with "mount -t vfat" (and re-ran the patcher script).  After that it was getting further, but still failing to mount.  So I inserted a "sleep 10" before the mount command and it actually booted.  Slowly.  It's an old laptop so the USB port isn't very fast.  I am now installing 9.04.

---

### Post by floborg on 2009-05-28
Why don't you extract the kernel and initrd to the USB stick as well?  Then, iso-scan should work.  I've never tried it from a stick however.  Here's an example for the new Linux Mint booting from the main filesystem of my Ubuntu install:

```
title		Linux Mint 7 i386 (from ISO)
kernel		(hd0,2)/fromiso/vmlinuz iso-scan/filename=/fromiso/LinuxMint-7.iso boot=casper quiet splash
initrd		(hd0,2)/fromiso/initrd.gz
```

---

### Post by domthehat on 2009-05-28
It's an old laptop that can't boot off USB - in fact I don't think it can even "see" the USB stick until it's loaded the kernel, which must therefore be on the hard disk.  OTOH I didn't want the ISO on the disk because I didn't want to create a separate partition for it and you can't install to the same partition as the one that's got the ISO on it.  As for why I  didn't just install from CD... that's another story.

---

### Post by floborg on 2009-05-28
> **domthehat said:**
> It's an old laptop that can't boot off USB - in fact I don't think it can even "see" the USB stick until it's loaded the kernel, which must therefore be on the hard disk.  OTOH I didn't want the ISO on the disk because I didn't want to create a separate partition for it and you can't install to the same partition as the one that's got the ISO on it.  As for why I  didn't just install from CD... that's another story.

My guess is that the root and ramdisk kernel options you had have confused the iso-scan command.  You could try it again without those options.

What you're trying to do is possible.  I've done it with Puppy.  Maybe iso-scan isn't that smart...yet.

---

### Post by domthehat on 2009-05-31
floborg,

I've gone through the process again, and the crucial thing is inserting the "sleep" command into the patch (no need to change the mount command).  My guess is that with
this old hardware, it takes time for the USB stick to get mounted; so iso-scan would probably work fine if it were not for the need for this delay.

However, the main thing is that, using the fromiso patch, with the sleep modification, I am able to boot a kernel off hard disk and then perform an installation from the ISO on the USB pendrive.

Hopefully this post will help someone else in future <grin>.

---

### Post by internalkernel on 2009-07-16
I see this thread has gone kinda quite... 

I like this approach though, I was trying to make floborg's method work. I keep getting dropped to an initramfs prompt though. I've got grub identifying the iso and the kernel/initrd - just doesn't seem to actually boot the iso. 

When I try to mount it complains about filesystem with special options... I have two questions... 

What version of Grub are you using? (Grub2?)
What filesystem types have you tried this on? Specifically wanting to know if this has been tested on ext4, otherwise I think that is the issue... 

thanks.

---

### Post by floborg on 2009-07-24
> **internalkernel said:**
> I see this thread has gone kinda quite... 

I like this approach though, I was trying to make floborg's method work. I keep getting dropped to an initramfs prompt though. I've got grub identifying the iso and the kernel/initrd - just doesn't seem to actually boot the iso. 

When I try to mount it complains about filesystem with special options... I have two questions... 

What version of Grub are you using? (Grub2?)
What filesystem types have you tried this on? Specifically wanting to know if this has been tested on ext4, otherwise I think that is the issue... 

thanks.

I assume my version of Grub is that which came with Hardy 8.04.  I think it's 0.97-29ubuntu53.  My filesystem is ext3.  I just got a daily build of Karmic to boot from the ISO last week using this:

```
title		Karmic Daily 64 (from ISO)
kernel		(hd0,2)/fromiso/vmlinuz iso-scan/filename=/fromiso/karmic-desktop-amd64.iso boot=casper quiet splash
initrd		(hd0,2)/fromiso/initrd.lz
```

---

### Post by internalkernel on 2009-07-24
> **floborg said:**
> I assume my version of Grub is that which came with Hardy 8.04.  I think it's 0.97-29ubuntu53.  My filesystem is ext3.

Just tested it on another box that has ext3, it worked flawlessly... doesn't like ext4 though. Thanks for the help...

---

### Post by Jose Catre-Vandis on 2009-12-06
Just tested this out, using the script, with an Intrepid iso on Jaunty running grub2.

Amendments:

1. The script created **initrd_fromiso.gz** so I had to rename it in the grub stanza

2. Things are quite different in grub2 from a menu point of view. Here is the entry I used:


> menuentry "Live Ibex" {
	set root=(hd0,7)
	linux  /home/jose/fromiso/vmlinuz ramdisk_size=100000 boot=casper root=/dev/ram0 fromiso=/dev/sda7/home/jose/fromiso/ii.iso
	initrd /home/jose/fromiso/initrd_fromiso.gz
}

Some explanation:

I created a **fromiso** folder in my home for all the files
In grub2 the partition numbers for (hd0) and (sda) are the same!
You use **linux** instead of **kernel** in the "**vmlinuz**" line

But hey, it works and this was posted from the "Live Ibex":)

Couldn't get the script to work for Karmic 9.10, any chance of an update?

EDIT

Forgot to mention, I don't get the normal graphical bootup, it just drops to cli and loads that way,

---

