---
title: "/ Nearly Full - false report? Disk is BTRFS"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-10-08
For the past several weeks, intermittently, at power up, I get a message about "/" being nearly full. That seems inconsistent with a root of nearly 20 gig, installed in June of 2013.

```
mark@Lexington:~$ sudo btrfs fi show
failed to open /dev/sr0: No medium found
Label: none  uuid: 696dab11-a8ad-4515-864a-afd6aa1dc438
	Total devices 1 FS bytes used 87.44GB
	devid    1 size 346.53GB used 96.29GB path /dev/sda6

Label: none  uuid: d40df79f-cbb3-4e95-8302-c0f7de5dec59
	Total devices 1 FS bytes used 15.18GB
	devid    1 size 18.63GB used 18.63GB path /dev/sda1

Btrfs v0.20-rc1

mark@Lexington:~$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00052a4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda2        39065598   781422591   371178497    5  Extended
/dev/sda5       765798400   781422591     7812096   82  Linux swap / Solaris
/dev/sda6        39065600   765798399   363366400   83  Linux


mark@Lexington:~$ sudo df -h
[sudo] password for mark: 
Filesystem      Size  Used Avail Use%    Mounted on
/dev/sda1        19G   17G  876M  96%        /
udev               2.0G  4.0K  2.0G   1%         /dev
tmpfs              805M  936K  805M   1%      /run
none               5.0M     0  5.0M   0%          /run/lock
none               2.0G  2.6M  2.0G   1%        /run/shm
/dev/sda6       347G   89G  258G  26%      /home
```

and

```
mark@Lexington:~$ sudo df -i
Filesystem     Inodes IUsed  IFree IUse% Mounted on
/dev/sda1           0     0                  0           - /
```

and

```
mark@Lexington:~$ sudo dumpe2fs /dev/sda1 | grep -i reserved
dumpe2fs 1.42 (29-Nov-2011)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda1
```


but, the on-screen message offers to show help, opens Disk Usage Analyzer and then after the "/" populates, there is lots of room. I run Ub. Tweak after each 3rd new kernel and keep a pretty tight OS that way.

The [kernel.log]("http://paste.ubuntu.com/6210092/") says:

```
Oct  8 08:26:51 Lexington kernel: [  156.331424] EXT3-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
Oct  8 08:26:51 Lexington kernel: [  156.338470] EXT3-fs (sdb1): using internal journal
Oct  8 08:26:51 Lexington kernel: [  156.338476] EXT3-fs (sdb1): mounted filesystem with ordered data mode
```

but /sdb1 is a thumb drive and according to "Properties" is about 50% full.

and other kernel.log msg:

```
Oct  8 08:24:43 Lexington kernel: [    1.348881]   Magic number: 1:590:436

Oct  8 08:24:43 Lexington kernel: [   23.431468] device fsid 696dab11-a8ad-4515-864a-afd6aa1dc438 devid 1 transid 68341 /dev/sda6
```

The disk is formatted as: BTRFS.

---

### Post by whitesmith on 2013-10-08
What do you get from the / line in ```
df -hT | egrep -i "file|^/"
``` which I regard as an informal gold standard? Also, this posting seems a bit advanced for its location. Cheers.

---

### Post by Mark_in_Hollywood on 2013-10-08
mark@Lexington:~$ df -hT | egrep -i "file|^/"
[COLOR="#FF0000"]Files[/COLOR]ystem     Type      Size  Used Avail Use% Mounted on
[COLOR="#FF0000"]/[/COLOR]dev/sda1      btrfs      19G   18G  180M  99% /
[COLOR="#FF0000"]/[/COLOR]dev/sda6      btrfs     347G   89G  258G  26% /home

Also:

mark@Lexington:~$ btrfs fi df /
Data: total=14.60GB, used=13.74GB
System, DUP: total=8.00MB, used=4.00KB
System: total=4.00MB, used=0.00
Metadata, DUP: total=2.00GB, used=1.44GB
Metadata: total=8.00MB, used=0.00


As I'm a complete noob at btfrs, I thought my problem best posted here. If I'm in error, can a Moderator please move it somewhere more appropriate. 

I probably should have posted this earlier. Sorry.

[email]mark@Lexington:~/.local[/email][/email]/share/Trash$ du -ch | grep total
**1.6G**	total

mark@Lexington:~$ uname -r
3.2.0-54-generic-pae

Meanwhile, to be safe, I have emptied the Trash of that 1.5G.

---

### Post by heir4c on 2013-10-08
Post here the output of:
```
cd / && ls && cd
```

(The last cd is for returning to your own directory)

ThanX

---

### Post by Mark_in_Hollywood on 2013-10-08
mark@Lexington:~$ cd / && ls && cd
bin    dev   include     media  proc  sbin     sys  var
boot   etc   initrd.img  mnt    root  selinux  tmp  vmlinuz
cdrom  home  lib         opt    run   srv      usr

---

### Post by heir4c on 2013-10-08
I ask that because I was curious the /home is still in the / 
I have never had a separately /home partition so I don't know of this is normal.
Is this the /home on sda6 or is this an other /home you see in the output?
When that is a different home than maybe that is the problem.

---

### Post by Mark_in_Hollywood on 2013-10-08
Yes, my /home is on it's own partition. That's /sda6 I believe. But please don't post random, un-related questions about this question of mine.

No, the /home isn't nearly full. It's about 26% used.

The / or root "directory" is being reported as 98% used. That's probably not factual. I'm trying to find the problem.

to learn about putting /home on it's own partition please see:


[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by heir4c on 2013-10-08
I don't post random or ask un-related questions.
There IS a home IN the / 
Look to the output:


mark@Lexington:~$ cd / && ls && cd
bin dev include media proc sbin sys var
boot etc initrd.img mnt root selinux tmp vmlinuz
cdrom **home** lib opt run srv usr

---

### Post by DuckHook on 2013-10-08
> **heir4c said:**
> There IS a home IN the / 
Look to the outputIt is there because it has been symlinked (everything must branch from /... that's why it is called "root"); nonetheless it is in it's own partition. This is similar drive architecture to many of my machines.

---

### Post by DuckHook on 2013-10-08
Know nothing about btrfs except that it sounds intriguing and I would like to try it some day. Having said that, were this to have happened in ext4, I would run fsck. Does this work in btrfs, or does it have an equivalent?

EDIT

From Wikipedia:

Unix systems traditionally rely on "[fsck]("http://en.wikipedia.org/wiki/Fsck")"  programs to check and repair filesystems. The "btrfsck" program is now  available but, as of May 2012, it is described by the authors as  "relatively new code" which has "not seen widespread testing on a large range of real-life  breakage", and that "may cause additional damage in the process of  repair".[SUP][/SUP]

 There is another tool, named btrfs-restore, that can be used to  recover files from an unmountable filesystem, without modifying the  broken filesystem itself (i.e., non-destructively).

/EDIT

---

### Post by oldfred on 2013-10-08
Did you install this?
btrfs-tools

synaptic reports this with 12.04
This package contains utilities (mkfs, fsck, btrfsctl) used to work with btrfs
and an utility (btrfs-convert) to make a btrfs filesystem from an ext3.

WARNING: Btrfs is under heavy development, and is not suitable for any uses
other than benchmarking and review.

       10-Way Linux File-System Comparison On Linux 3.10
[http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1)
BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)

---

### Post by Mark_in_Hollywood on 2013-10-09
heir4c

I apologize. Yours was, to my ignorant mind, a very odd question. Would you accept an apology?

---

### Post by Mark_in_Hollywood on 2013-10-09
Response to oldfred  

apt-get reports the btrfs-tools as installed.

I believe I have found the solution and ask for some help in understand whether HaraldWeber's post is specific to the OP's computer or a general response to all users with the more-or-less same problem.


 [installation on btrfs]("http://ubuntuforums.org/archive/index.php/t-2003556.html")

To get it started here is my fstab

  GNU nano 2.2.6              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d40df79f-cbb3-4e95-8302-c0f7de5dec59 /               btrfs   defaults,subv$
# /home was on /dev/sda6 during installation
UUID=696dab11-a8ad-4515-864a-afd6aa1dc438 /home           btrfs   defaults,subv$
# swap was on /dev/sda5 during installation
UUID=4db72d1e-d26b-4936-927e-52cec964f0db none            swap    sw           $
##
# above ## to add readability
## line below commened 3-sep-13 by mp. file system in linux have problems mount$
## UUID=f3c43eab-5888-4e6d-9755-4807e1bf6f7d    /media/wd160    ext4    default$

---

### Post by heir4c on 2013-10-09
> **Mark_in_Hollywood said:**
> heir4c

I apologize. Yours was, to my ignorant mind, a very odd question. Would you accept an apology?

  :-k ...... :D ;) Yes,  I accept your apology. No hard feelings. (Or how you say that in English)

---

### Post by Mark_in_Hollywood on 2013-10-09
Very well said, sir.

---

### Post by Mark_in_Hollywood on 2013-10-10
Hi

I quickly read your post. Your problem is that your root partition is full. Right? My post was about the wrong disk layout after the installation. All mounted btrfs partitions has to be subvolumes. If not the some btrfs features can't be used. E.g. snapshots.

To determine your used disk space you can run "sudo du -schx /*"
du is a command to see the disk usage (du)
The parameters schx stands for:
s: summarize
c: show total usage
h: human readable format
x: stay on the same filesystem (ignores /home. In your case /dev/sda5)

If the used disk space is near your 20GB then your disk is full.

Normally on btrfs drives you have one btrfs partition and many
subvolumes on it (subvolumes for /, /home, and so on). Every subvolume
can take the whole disk space (if not set a quota).
So you have subvolumes which can grow as they like till the disk is full.

In the current ubuntu setup the system is installed directly on the
btrfs partition and not in a subvolume. Therefore you can not use the
btrfs features.

What I would do in your case:

Boot from a live usb drive.
make two subvolumes, @ and @home like in my post, on your big volume
(i call it /dev/sda5 here). These subvolumes appears as simple
directories in /dev/sda5.
copy your root partition to @ (don't copy the subvolumes and your home
directory)
move /home to @home (take care to not copy the @ subvolume too)

Now your layout should look like this
/dev/sda1 (your old / partition)
(extended and swap)
/dev/sda5 (btrfs partition with subvolumes)
/dev/sda5 @ (your new root subvolume)
/dev/sda5 @home (your new home subvolume)

Now use gparted to shrink /dev/sda1 to approx. 150MB and format it to
ext2. (this will be used as boot partition)
Move and extend the left partitions.

Now you have a small /boot partition at /dev/sda1 and an extended
partition at /dev/sda5 (your btrfs partition)

Move the contents of /boot on your @ subvolume to /dev/sda1. Your
system will boot the kernel from this partition.

Then follow the steps i posted a year ago.

In my opinion this should be the correct setup.

Regards
Harald

---

### Post by heir4c on 2013-10-10
Interesting. I will look for that btrfs.

---

