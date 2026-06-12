---
title: "grub boot problem on BTRFS + ZFS system"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Beeblebrx on 2011-08-30
I share my home folder with another system so it's on ZFS. ZFS is v28 (using dajhorn ppa for zfs & zfs-grub).
Ubuntu root is on BTRFS (oneiric).  After update-grub, my system would not boot and kept dropping to busybox.
So I had to modify the entry in grub as below, but now when I boot up I get several problems:
```
linux	/vmlinuz-3.0.0-9-generic root=UUID=123456  rootflags=subvol=@
```
1. Process hangs for a while and looks like it is checking file systems.  Then it stops, stating that it cannot mount /home. After selecting "manual fix", I run these commands and system can continue the boot (I have not booted into the other system in between ubuntu boots, so zfs is not being shared yet)
```
# zpool export home
# zpool import home
# mount -a
```
2. my # df looks messy and incomprehensible.  Last 3 entries are mine so those are fine, as is root by UUID. As you can see, root seems to be mounted twice and there are these strange entries:
```
rootfs                10485760   4602572   2951156  61% /
udev                    486720        12    486708   1% /dev
tmpfs                   197956       744    197212   1% /run
/dev/disk/by-uuid/123456   10485760   4602572   2951156  61% /
none                      5120         0      5120   0% /run/lock
none                    494880       124    494756   1% /run/shm
tmpfs                   494880        20    494860   1% /tmp
home                  58317568  21904000  36413568  38% /home
/dev/sda6               490340     29231    434946   7% /boot
```
I suspect the problem is with the entry in grub and that I need to make the correction there.  Thanks for the input.

---

### Post by dino99 on 2011-08-30
you have chosen the wild bleeding edge ;) Hope you have some skills :)

EXT3/4 is easier and quite bug free, but digg the link below.

---

### Post by ranch hand on 2011-08-30
You give no information on your grub installation.

Do you have a separate /boot formatted to ext3 or 4?

Running this script and posting the results (complete) here would be a help to anyone trying to work on this problem;
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Beeblebrx on 2011-08-31
Hi and thanks to both for your input.  My main system is FreeBSD actually, and I am trying to get GRUB to play nice with BSD's BTX and root on ZFS.  So far, not so good. 
 
1. The zpool export - reimport problem "magically" went away - after my latest update I suspect, so that's resolved.  I noticed after I had posted that I get 2 significant errors for the posted issue:
a- When I run [COLOR=DarkGreen]update-grub[/COLOR] I get error message ```
xbtrfs not found - No volume groups found 
```b- At boot-up I get message below. [COLOR=DarkGreen]# ps -ax[/COLOR] shows a bunch of z_processes  (z_fr, z_wr, z_dr) - I suspect this herd of processes has something to  do with this error:
```
failed to execute /lib/udev/zpool_id -d: devices/virtualblock/ram8 no such file or directory
```2. Boot_info_script: [COLOR=DarkGreen]Grub[/COLOR] is on separate [COLOR=DarkGreen]ext2fs[/COLOR] (inode 256 for BSD compatibility) partition at the end of my GPT disk (sda6).  The script shows clearly the identification problem it is having with both zfs + btrfs: Nice utility, btw (file attached).
    ```
File system:       zfs_member 
    Boot sector type:  Unknown 
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'zfs_member'
```3. I had to comment out [COLOR=DarkGreen]tmpfs[/COLOR] for [COLOR=DarkGreen]/tmp[/COLOR] in [COLOR=DarkGreen]fstab[/COLOR] because it hangs when [COLOR=DarkGreen]lightdm[/COLOR] tries to start. Boot-up also shows this message, but nothing significant there: 
```
 fsck from util-linux 2.19.1 
grub: clean, 251/131072 files, 63938/523264 blocks 
root 256 inode 130010 errors 400 
root 256 inode 235250 errors 400 
found 4512526336 bytes used err is 1 
total csum bytes: 4154652 
total tree bytes: 258162688 
total fs tree bytes: 240930816 
btree space waste bytes: 70508749 
file data blocks allocated: 30747115520 
 referenced 4173144064 
Btrfs Btrfs v0.19 
mountall: fsck / [347] terminated with status 1 
fsck from util-linux 2.19.1
```4. I would like to be able to boot into my FreeBSD system on ZFS through [COLOR=DarkGreen]grub[/COLOR], so any suggestions appreciated.  Root is on [COLOR=DarkGreen]bsdr/root[/COLOR] with [COLOR=DarkGreen]bootfs[/COLOR] property set, bsdr it self is not mountable.  When I boot the Direct menu the boot process hangs with not being able to find root; when I boot BTX chainload, it loads the kernel but then drops to BTX rescue prompt where no files under /boot are visible.```
menuentry 'FreeBSD 9.0-Direct'--class freebsd --class bsd --class os { 
    insmod zfs 
    insmod zfs-info 
    set root='(hd0,gpt6)' 
    search -s -l bsdr 
#    freebsd  /boot/kernel/kernel.gz boot=zfs bsdr=AltPool bootfs=AltPool/root 
    kfreebsd  /root@/boot/kernel/kernel 
        kfreebsd_module_elf  /root@/boot/kernel/opensolaris.ko 
        kfreebsd_module_elf  /root@/boot/kernel/zfs.ko 
        kfreebsd_module  /root@/boot/zfs/zpool.cache type=/root@/boot/zfs/zpool.cache 
        kfreebsd_loadenv  /root@/boot/device.hints 
        set kFreeBSD.vfs.root.mountfrom=zfs:bsdr/root 
} 
menuentry 'FreeBSD 9.0-BTX'--class freebsd --class bsd --class os { 
    insmod zfs 
    insmod zfs-info 
    set root='(hd0,gpt3)' 
    kfreebsd  /root@/boot/loader 
    chainloader +1 }
```

---

### Post by ranch hand on 2011-08-31
I will look this over when I am not whipped.  It is 9:30PM local here and I have to be at work at 6:00AM.  Haven't had dinner or a shower yet so I am done for tonight.

You may want to point this thread out to drs305;
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

He is the go to guy on strange things having to do with grub.  He may be able to point you to some information.   I would post on that thread with a link to this thread.

Be sure to check out his links at the bottom of the first post.  He has several other grub threads and one is about doing some fairly intense editing of grub scripts.

I would run a thread search on that thread for your file systems too.  Who knows, there may be a post on there about something related anyway (80 pages).

Thanks for that boot info script result.  That should shed some light on it whether I can see it or not.

---

### Post by cariboo on 2011-08-31
Unfortunately drs305 is on holidays, and is only checking in occasionally, he should be back in a week or so.

---

### Post by ranch hand on 2011-09-01
OK, I have to declare myself really ignorant.

I just spent a little bit looking into zfs.  I am boogled.  Sounds really neat but  I am not fluent enough in geek to really understand what I am reading.

Will have to put this on my list of things to try myself.

All that said, I did find a couple links that may help you in setting it up;
[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

[http://www.wizy.org/wiki/ZFS_on_FUSE/Debian](http://www.wizy.org/wiki/ZFS_on_FUSE/Debian)

I think the problem you are running into is that grub is not ready for zfs.  You may want to communicate this to the grub folks directly so that they know folks want it.

What I would do is try installing it differently.  You have a /boot so that you have a grub that tries to work.  It is not able to deal with the format so it freaks out.  I really wonder if a separate /etc in some suitable format would make it work.  That would give the grub on the mbr direct contact with the grub.d and fstab files.

Have no real idea if that would work, it is just what I would try.

The other thing that would work, I am pretty sure, is to have your entire / partition on btrfs, /boot as it is and then your /home and other partitions on the zfs business.  I know that grub will boot your system on btrfs with a separate /boot on ext?.   I also just read a blog the other day about someone with all data on zfs (this was last week and the first I ever heard of zfs).  They had their / partition on some other strange (to me) format.  I should have paid more attention, I was really only looking into the person writing the thing and trying to figure out if they knew what they were talking about.

What they recommended on another forum worked for an unrelated problem.  I think she (pretty sure it was a she) is pretty sharp.

---

### Post by pressureman on 2011-09-01
I've watched this thread with a bit of amusement at the OP's daringness to live on the bleeding edge. Sharing a ZFS between two different OSes will certainly add some excitement to your day.

> **ranch hand said:**
> I think the problem you are running into is that grub is not ready for zfs.  You may want to communicate this to the grub folks directly so that they know folks want it.

Grub is perfectly capable of supporting zfs - I've installed over 30 OpenSolaris and OpenIndiana boxes which use it. However, in those instances, it was a version of grub legacy (0.9.x) that Sun patched to support booting from single-disk and raidz1 (mirror) zpools. Booting from raidz2 or raidz3 was not supported.

Grub2 officially supports booting from ZFS (single/raidz1), since they formally accepted the OpenSolaris ZFS code that had previously been in grub-extras.

> **ranch hand said:**
> What I would do is try installing it differently.  You have a /boot so that you have a grub that tries to work.  It is not able to deal with the format so it freaks out.  I really wonder if a separate /etc in some suitable format would make it work.  That would give the grub on the mbr direct contact with the grub.d and fstab files.


Grub does not use any files from /etc during booting. If /etc is being read, it means the rootfs of the selected OS has already been mounted, and the OS kernel is booting - eg. grub has already served its purpose. The only parts of the disk that grub reads are the MBR, and the /boot partition. Exceptions to this are when grub chain loads an OS, such as in the case of booting Windows.

The grub.d directory you see in /etc is simply used by update-grub and friends for building a grub.cfg config, which gets written to /boot/grub.

> **ranch hand said:**
> The other thing that would work, I am pretty sure, is to have your entire / partition on btrfs, /boot as it is and then your /home and other partitions on the zfs business.  I know that grub will boot your system on btrfs with a separate /boot on ext?

The thing is that /boot is going to need to be writable by both Linux and FreeBSD, since it's where the kernels must reside. That probably means either ext2 or zfs.

The OP is going to have to be very careful that neither the Linux nor FreeBSD install ever upgrade the zpool or zfs version past what the other can support.

> **ranch hand said:**
> I also just read a blog the other day about someone with all data on zfs (this was last week and the first I ever heard of zfs).  They had their / partition on some other strange (to me) format.  I should have paid more attention, I was really only looking into the person writing the thing and trying to figure out if they knew what they were talking about.

What they recommended on another forum worked for an unrelated problem.  I think she (pretty sure it was a she) is pretty sharp.

That didn't happen to be Claudia Hildebrandt by any chance? She certainly knows her ZFS internals. I had the opportunity to attend a seminar by her at a GUUG meeting, focusing mainly on the insanely clever L2ARC and using logzillas.

---

### Post by ranch hand on 2011-09-02
I do not think that was her.

GUUG?  Goofy Ubuntu Users Group?

Whatever it is I like the look of the initials.  Look good on shirt.  "Proud member of GUUG"

I know that grub doesn't use those files.  Shouldn't respond when dead tired, getting that way now.

I think I will quit while ahead and crash.

---

### Post by pressureman on 2011-09-02
> **ranch hand said:**
> GUUG?  Goofy Ubuntu Users Group?

Whatever it is I like the look of the initials.  Look good on shirt.  "Proud member of GUUG"

Wow, look at that, the number one Google result for GUUG is.... German Unix User Group :)

Before Ubuntu there was Linux... and before that, there was Unix.

---

### Post by ranch hand on 2011-09-03
Very nice.

---

### Post by Beeblebrx on 2011-09-03
Thanks to all of you for posting.  From my viewpoint, there are several different topics here so I will try to separate these problems.
   **1.** Grub script is unable correctly update a rooot-on-btrfs ubuntu system (related error: xbtrfs not found) and needs manual intervention.  No Big Deal...
   **2.** tmpfs for /tmp is buggy, probably because of the rooot-on-btrfs.  A similar issue existed in older ZFS versions. Nothing I can do...
   **3.** "Dajhorn ZFS" compatibility on Oneiric spawns too many childrens and the population overflow is not pretty (related error: failed to execute /lib/udev/zpool_id). Again, Nothing I can do...
   **4.** The Bloody Bleeding Edge or [http://www.youtube.com/watch?v=xtrEN-YKLBM](http://www.youtube.com/watch?v=xtrEN-YKLBM) (for you, pressureman):
***** ZFS is certainly not bleeding edge in IMHO. Would you drive a new car, or a 5-year old auto if they were priced the same? The newer car would have a great number of technology improvements and fail-protection/security measures.  If you are running a commercial or corporate server, then of course don't mess with what is already working. But if you are setting up a new system or if you are using the system as PC, then you actually risk MORE by not incorporating the latest technology.  ZFS is leaps beyond other FS for PC and servers.
**    *** A second reason is that ZFS is the best way to share a folder between Linux and BSD. Any extfs > 2 does not work on BSD, and even then the ext2 needs to be tweaked to Inode 256 for R/W.  UFS support in Linux is equally flimsy.  What's left - FAT32? Well, why not go with FAT16 then - proven technology!  I'm not even going to get into the error checksum, automated snapshots and a whole lot more advantages zfs provides.
***** Upgrading a Zpool only happens with the "zpool upgrade" command and it is not automatic.  So you could have a zfs v14 pool running on a system updated to v28-no problem. You would upgrade only when both distros become in sync for zpool versions.  I have 2 systems: one is AMD Athlon64, the other P4-64, both with with 1G ram each (far below the 4G).  They run like a charm and no undue load from ZFS (except item 3 above).
**    5.** What I hope to solve or really the unexplored side here: Getting Grub to boot the FreeBSD kernel on ZFS or getting the BTX loader to chainload.
> Grub does not use any files from /etc during booting. If /etc is being read, it means the rootfs of the selected OS has already been mounted, and the OS kernel is booting - eg. grub has already served its purpose   Exactly! One thing I learned with Grub early-on is that once you see the kernel boot message on the screen, Grub has done its job; and this is what's confusing to me.  Grub has passed some parameters to the kernel and I can see it booting. Then, for whatever reason, it cannot identify the Z file system.  If it could not identify zfs, it would not be able to boot the kernel in the first place? The only explanation is that we have not passed the _correct parameters on to the kernel through Grub_...

@ ranch hand: Will do some more reading-up about grub-zfs myself and get back.
@ pressureman: I hope you liked the link, I searched long hours for it :)

---

### Post by pressureman on 2011-09-03
> **Beeblebrx said:**
> **4.** The Bloody Bleeding Edge or [http://www.youtube.com/watch?v=xtrEN-YKLBM](http://www.youtube.com/watch?v=xtrEN-YKLBM) (for you, pressureman):
***** ZFS is certainly not bleeding edge in IMHO. Would you drive a new car, or a 5-year old auto if they were priced the same? The newer car would have a great number of technology improvements and fail-protection/security measures.  If you are running a commercial or corporate server, then of course don't mess with what is already working. But if you are setting up a new system or if you are using the system as PC, then you actually risk MORE by not incorporating the latest technology.  ZFS is leaps beyond other FS for PC and servers.

@ pressureman: I hope you liked the link, I searched long hours for it :)

Heheh, I did indeed enjoy the link... it's a great track from a couple of great bands/artists.

I completely agree, ZFS is an amazing filesystem, and I have a fair bit of experience with it myself, on OpenSolaris and OpenIndiana. Our standard server buildout is usually a smallish raidz1 rpool, and then a second, larger zpool in either raidz2 or raidz3. On several systems we added a 32GB high performance Intel SSD, partitioned roughly in half, for logzilla and L2ARC respectively. It's quite mature technology on Solaris. I don't have any first-hand experience with the FreeBSD or Linux ports of it, so I can't vouch for its stability on those platforms.

Part of the difficulty with integrating ZFS into Linux is that ZFS is more than just a filesystem. It's a block device layer also. As such, it somewhat duplicates the functionality of the VFS layer in Linux. Reiser4 had similar issues to contend with, and this was one of the reasons why it still isn't merged into the mainline kernel.

I would love to see ZFS become the defacto filesystem of all Unixes (Unices?) and even perhaps MacOS. The ZFS motto "the last word in filesystems" is no joke. There really isn't a lot out there that can compete with it, not in the open source world, and I think a Solaris box with a well designed ZFS infrastructure can give a lot of commercial SANs a serious run for their money. I was told by a colleague that the University of Ulm (in Germany) was used as a beta site for Sun in the early days of ZFS, and they had approximately 10,000 disks in a single zpool!

One of the GUUG members (and a former employee of Sun Microsystems) once described a setup he had built in the lab, comprised of 240 consumer grade SATA hard disks in a single zpool, plus about a dozen SSDs for L2ARC and ZIL, which was able to saturate four 10 GigE NICs when setup as an iSCSI target. The cost per gigabyte of storage (and per gigabit of disk IO) was considerably less than an equivalent capacity SAN. You can save money by using mid-range SATA hard disks, and redirect some of that money towards good quality SSDs for caching, instead of spending a fortune on SAS disks.

So yeah... I have the utmost respect for the ZFS developers. It's just a shame that the license is not really compatible with Linux (or vice versa perhaps).

A link for you... some fun with ZFS on USB sticks [http://video.google.com/videoplay?docid=8100808442979626078](http://video.google.com/videoplay?docid=8100808442979626078)

---

### Post by emk2203 on 2011-09-16
You are much better off posting your questions in the discussion list zfs-discuss of zfsonlinux.org. The developers are there and answer most questions, and from personal experience, if it has to do with zfs on linux, you better ask there. Chances are slim that you find the needed expertise with zfs elsewhere.

---

