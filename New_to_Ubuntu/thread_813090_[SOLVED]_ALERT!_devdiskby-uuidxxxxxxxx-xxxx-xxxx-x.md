---
title: "[SOLVED] ALERT! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xx$ does not exist"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by ChompTheMan on 2008-05-30
I'll have to start by explaining some things.  I updated yesterday and installed a new kernel.  Later on, I tried to install something in the terminal when it informed me to execute 'dpkg --configure -a'(I think), which I did and it informed me a new version of Grub was available.  It gave a me a list of options to install it, so being unsure I chose 'package maintainers version' or something along those lines.

When I booted up today I was greeted by a messy, disorganized boot screen that had my old kernel options, then in the other operating systems section was Windows, the new kernel, and the old kernel.  So I booted into the new kernel and then edited grub.  I commented out the old kernel version, then copy pasted the new kernel lines at the top and deleted the additional old kernel lines.  Basically I cleaned up menu.lst to look like my old one before the update to grub, except with the new kernel listed instead.  I must have done something wrong because I now boot into Busybox with this:

```
Check root=bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
Alert! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xx$ does not exist.  Dropping to a shell!
```

I went into rescue mode with the alternate cd and chose to mount /.  Nano wouldn't work so I didn't know how to edit menu.lst, so I went back and chose the option 'Reinstall Grub', but it just took me back to the previous menu every time I hit enter.

I am a little out of my element here and not sure what to do next.  I am currently stuck using Windows right now...  Help!!!

---

### Post by Oldsoldier2003 on 2008-05-30
boot to recovery mode and give the results of ```
fdisk -l
``` Also please find the partition you installed ubuntu and post the contents of /boot/grub/menu.lst

With this info it wont be hard to get you sorted.

or you could download and burn the supergrub live cd.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by kebes on 2008-05-30
The content of your "/etc/fstab" file might also be relevant.

Sometimes the entries in fstab will be changed so that instead of referring to a device path (like "/dev/sda1") they will be switched to a UUID version (like "UUID=1b5a38ca-9f0d-4f1a-8fc1-7c418e79bf07"). The previous device mapping will be listed on the line above, commented-out.

In the past I've switched the UUID back to the device path without problems.

So I would check "/etc/fstab" and if it contains UUID listings for mountpoints, change them back to device paths (backup your fstab first, of course!). See also [this post]("http://ubuntuforums.org/showthread.php?t=747249").

Since you can't boot into Linux, you'll have to boot into a LiveCD, mount the drive, and make the changes from there. Let us know if you need any of these instructions to be more explicit.

---

### Post by ChompTheMan on 2008-05-30
Thanks for the quick responses guys.  Here are the results of fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a8d9a8d

Device    Boot Start  End   Blocks   ID System
/dev/sda1  *       1  3264 26218048+  7 HPFS/NTFS
/dev/sda2       3265 28704 204346800 83 Linux
/dev/sda3      28705 30009 10482412+ 83 Linux
/dev/sda4      30010 30401   3148740 82 Linux swap/Solaris
```

Ubuntu is installed in sda3.

When I open menu.lst in vi I get a warning message that it has "Found a swapfile by the name '.menu.lst.swp'" and that it is still a running process.  It informs me that another program is running or that an edit session has crashed and that I should use ":recover" or "vim -r menu.lst".  When I went to get the results of fdisk -l it occurred to me to try vi since nano wouldn't work.  I couldn't figure out how to exit vi so I did a hard reboot and booted into Windows to take a crash course in vi.  I got the above message after going back into recovery and opening menu.lst again.  I have four menu.lst in /boot/grub: menu.lst, menu.lst.080424211840, menu.lst~, menu.lst_original.  When I do ls -a these ones pop up: .menu.lst.swn, .menu.lst.swo, .menu.lst.swp.

I went and had a look at fstab and noticed the UUID was different for the one in my menu.lst.  In fstab it's a5d9692d-c46e-4b50-81ed-f6d3fa65d7a7 in menu.lst it's a5d9692d-c46e-4b50-81$.

So my first question is what do I do about .menu.lst.swp?  There are no edits I would want to keep so is it okay to just delete it?  The process ID for it is 17873.  Do I kill it?  What about .menu.lst.swn and .menu.lst.swo?

After that is taken care of should I change the UUID in menu.lst to match the one in fstab?  Will that solve my problem?

Do I need menu.lst.080424211840?  Can it be removed as well?

I'm hoping that changing the UUID in menu.lst to match the one in fstab will resolve my problem so I didn't bother writing down the contents of menu.lst and fstab.  If you still need them let me know and I'll type them up.  Thanks in advance.

---

### Post by kebes on 2008-05-30
> **ChompTheMan said:**
> I couldn't figure out how to exit vi so I did a hard reboot
I'm assuming you figured out that to quit vi, you can type ":q!". It's also worth noting that on the commandline you can go Ctrl+Z to put the program in the background and get back to the prompt. (If you really can't quit a program, you can go back to the prompt and kill it manually. Better than a reboot.)

> So my first question is what do I do about .menu.lst.swp?
Unless you were in the middle of making changes to menu.lst when you rebooted, just ignore all that recovery non-sense. On the other hand, reverting to the version of menu.lst before you started making edits might be a good idea. (Assuming you made a backup at that stage.)

In any case, having backups of menu.lst lying around doesn't do any harm.

> I'm hoping that changing the UUID in menu.lst to match the one in fstab will resolve my problem
Well, it's not obvious whether the "right" UUID is the one in menu.lst or in fstab. (Or maybe they are both wrong.) At least for fstab, as far as I know, you can safely alter the UUID values back to the corresponding device paths. So edit your "/etc/fstab" and if it looks like:
```
# /dev/sda3
UUID=1b5a38ca-9f0d-4f1a-8fc1-7c418e79bf07 /   ext3 defaults,errors=remount-ro 0       1

```
You can change it to:
```
# /dev/sda3
/dev/sda3 /   ext3 defaults,errors=remount-ro 0       1

```
(Of course, make a backup copy before making these changes.)

It's possible that this will fix everything. If not, you may have to also edit your menu.lst to avoid the UUID notation. E.g. instead of "root=UUID=b7e34129-5824-4292-b56f-3afc8051e2da" switch to the notation "root=/dev/sda3". (I've never done this myself... anyone else have experience with this?)

You can also try "ls -l /dev/disk/by-uuid/" to get the UUID and corresponding device names.

---

### Post by chrisccoulson on 2008-05-30
The best fix is to replace the incorrect UUID in your menu.lst with the correct UUID, which should also match the UUID in your fstab. To find out the correct UUID, do the following from the live CD:
```
sudo blkid
```
...you will see an output which maps device nodes to UUID's. IN my case, it looks like this:
```
/dev/mapper/nvidia_effeccbe7: TYPE="swap" UUID="c7f0b160-7189-480b-8184-6aa575ae275a" 
/dev/mapper/nvidia_effeccbe6: LABEL="root" UUID="4a810ba8-bfc5-4a54-b9f3-e7588805b872" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/nvidia_effeccbe5: LABEL="tmp" UUID="4d2dbdd4-b441-4c3b-b3b1-63598b5091f4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/nvidia_effeccbe3: LABEL="boot" UUID="450a14e7-7e17-41e1-9c0a-5c576aaade73" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/nvidia_effeccbe1: TYPE="ntfs" UUID="B080F3DA80F3A54E" 
/dev/mapper/nvidia_effeccbe9: UUID="dfa88fa9-e0e7-4a3f-bc76-08c2e087d431" SEC_TYPE="ext2" TYPE="ext3" LABEL="misc" 
/dev/mapper/nvidia_effeccbe8: LABEL="var" UUID="7568e5ba-bc0a-4773-98dd-051aabdd9430" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="home" UUID="7cfd1f74-70d1-412e-8dfd-1c1ed4dd9526" SEC_TYPE="ext2" TYPE="ext3"
```

When editing your menu.lst, you need to make sure that the correct root filesystem is specified on the line beginning "# kopt=root", otherwise it will just break again next time you install a new kernel or manually run update-grub. 

To edit your menu.lst correctly from the live CD, mount your root filesystem first:
```
sudo mkdir /mnt/target
sudo mount -t ext3 /dev/sda3 /mnt/target
```
Modify the line beginning "# kopt=root" in /mnt/target/boot/grub/menu.lst with the correct UUID. In my case, it looks like this:
```
# kopt=root=UUID=4a810ba8-bfc5-4a54-b9f3-e7588805b872 ro
```

Then you need to chroot in to your environment and run update-grub to fix it:
```
sudo chroot /mnt/target
update-grub
```

Then verify all your kernel entries contain the correct UUID, and it also matches the UUID specified in your /etc/fstab

---

### Post by ChompTheMan on 2008-05-30
Thank you very much everyone, I learned an awful lot doing this.  I just changed the UUID in menu.lst to match the one in fstab and everything works fine now.  I just read chriscoulson's response, thank you the correct root file system is now specified.

---

### Post by Rup.Xamqon on 2008-11-02
I did a clean install of Kubuntu II (64bit) from the Live CD, on a PC with 2 hard disks. After restart, I couldn't even get to the boot screen. I just got the mentioned error message.

I followed kebes' advice. I run Puppy Linux from CD, and used it to check "/etc/fstab". After backing it up, I changed the UUID listings for mountpoints to my device paths (like "/dev/sda1"). The same thing I did for "/boot/grub/menu.lst", changing UUIDs to "/dev/sda1" or to "(hd0,0)", following the examples given in the same file. I attached this file to my comment in launchpad, in case it helps others: [https://bugs.launchpad.net/ubuntu/+bug/284774/comments/11](https://bugs.launchpad.net/ubuntu/+bug/284774/comments/11). And yes, kebes, it works!

With this changes written to both files, I was able finally to boot into my new Kubuntu II without other problems.

---

### Post by gravyface on 2009-03-12
Hopefully somebody can assist me here.  I've attempted the recommendations in this thread but had Damn Small Linux lying around, so used it instead.  Booting into DSL is fine, but can't seem to find my hdd.  
I'm pretty sure it's /dev/sda1, but fdisk -l /dev/sda returns "cannot open /dev/sda".  Same for /dev/hda, /dev/hdb, /dev/sda[1-5], etc.

Bit of background:

Had an old P3 running Ubuntu 7.04 Feisty server version and did a physical to virtual migration (ESXi), which has been running flawlessly for a few weeks (had to fiddle with NICs a bit, but everything else worked fine).

Decided I should upgrade to the latest 8.10 LTS and as per Ubuntu's upgrade docs, was planning on doing an incremental upgrade to Gutsy first, using do-dist-upgrade.
Went ok until I'm assuming the kernel was updated (it asked me to restart) and am experiencing the same errors in this thread.

Any ideas?  Is this a kernel/driver limitation of DSL?  Maybe I should try Puppy instead?

---

### Post by Neobuntu on 2009-04-16
I didn't have to reinstall.
None of the Busybox commands helped me.
No drive or UUID was wrong for me.
I don't have RAID. 

My SOLUTION:
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)

---

### Post by walterdf00 on 2009-08-16
gravyface, I ran into that problem as well while trying to solve this issue.  I acutally had to do "sudo fdisk -l".

---

