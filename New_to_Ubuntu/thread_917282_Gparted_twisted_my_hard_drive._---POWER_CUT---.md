---
title: "Gparted twisted my hard drive. ---POWER CUT---"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Tjcrazy on 2008-09-11
I was making my ubuntu partition bigger on the ubuntu LIVECD using gparted. I had a powercut... I restarted back into Ubuntu on the HD and crap:

```

modprobe: WARNING: Failed to open config file etc/modprobe.d/oss-compat$ not a directory.

```

Im in livecd now. Good news is I can still mount a view my ubuntu partition. I am trying to back it up onto External HD as I type but would like to try restore ubuntu back to original state.

How can I do this? Ive tried stuff like sbackup and it doesnt install on livecd.

Tim

P.S. oss-compat is there but it is a broken link to: /lib/oss-compat/linux which isnt there.

---

### Post by Pro-reason on 2008-09-11
Have you read [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)?

---

### Post by Tjcrazy on 2008-09-12
I have tried, most options failed. the last couple I am trying now. Th testdisk and disk checkers came up with partition OK, so I think its just the fact that oss-compat is missing?

---

### Post by bumanie on 2008-09-12
That is the one time partitioning definitely will fail - with a power cut part way through the process. Would suggest that dd commands may be the best thing here. > dd if=/dev/<name of hard drive> of=/dev/<name of hard drive2>That will do a full copy of the hard drive and may be if it goes onto a good filesystem on another drive, you may be able to save most of your data. The other thing you can try is to use the live cd of photorec from [here]("http://www.cgsecurity.org/wiki/PhotoRec") Despite the name it looks for nearly all file types, including text files etc. It is filesystem independent as it tries to read the raw data off the disk.
I'm sorry this has happened. It's a bit ironic - about 2 weeks ago I warned someone on this forum that partitioning would fail and wreck their filesystem if there was a power outage - they didn't believe me according to the curt reply I got. Try photorec, if that fails try dd commands onto a good filesystem on another drive > dd if=/dev/sda of=/dev/sdb (substitute the names of your drives.

---

### Post by Tjcrazy on 2008-09-12
I've only got one HD. I got a 500gb external HD (LaCie) I entered your code and got this:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=/media/LaCie  
dd: opening `/media/LaCie': Is a directory

```

---

### Post by Tjcrazy on 2008-09-12
I've only got one HD. I got a 500gb external HD (LaCie) I entered your code and got this:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=/media/LaCie  
dd: opening `/media/LaCie': Is a directory

```

Would it not be easier just to replace my missing file oss-compat. Maybe someone can send it to me, cause I am pretty sure that is the only problem.

---

### Post by bumanie on 2008-09-12
Linux does not name drives like that, unless you have specifically mounted it in /etc/fstab by that name to a specific mount point. It will be /dev/media/LaCie or /dev/sdc1 or something similar.

---

### Post by ibuclaw on 2008-09-12
Have you heard of chroot?

you can mount the partition and chroot into it.

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt

```

If you can get in (unless you have a bash error, shouldn't happen if you use the same LiveCD you used to install Ubuntu)
Run this
```
dpkg -S /lib/oss-compat/linux
```
And dpkg will output the name of the package that uses that.

Then it's just a case of reinstalling.
```
sudo aptitude reinstall xyz
```

But, in you case of the powercut during repartitioning, you may as well reinstall all packages.

Regards
Iain

---

### Post by Tjcrazy on 2008-09-12
I would do what tinivole said, but now my partion is not viewable at all. In gparted I get the ! symbol next to the partition. If I got to information my (LIVECD) res isnt big enough to view it. I did

```
sudo tune2fs -l /dev/sda2
```
And it outputted:
```
tune2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          a156cca5-d4e0-4dd0-bde0-a95e39b90aae
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              4210304
Block count:              16946566
Reserved block count:     169465
Free blocks:              7197267
Free inodes:              3896520
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      621
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8128
Inode blocks per group:   254
Filesystem created:       Tue Jul 15 16:00:25 2008
Last mount time:          Thu Sep 11 22:30:50 2008
Last write time:          Fri Sep 12 15:35:21 2008
Mount count:              3
Maximum mount count:      39
Last checked:             Thu Sep 11 17:36:49 2008
Check interval:           15552000 (6 months)
Next check after:         Tue Mar 10 17:36:49 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      b745c4c3-d81a-446f-9341-99edfe1442f1
Journal backup:           inode blocks
```

testdisk says the partition is OK.

I then tried:
```

sudo e2fsck /dev/sda2
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Group descriptors look bad... trying backup blocks...
Superblock has an invalid ext3 journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Corruption found in superblock.  (blocks_count = 0).

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 32768 <device>

```

BUT:

```

sudo e2fsck -b 32768 /dev/sda2
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sda2
Filesystem mounted or opened exclusively by another program?

```

So, any ideas? I am stuck.

---

### Post by Tjcrazy on 2008-09-12
UPDATE: I just did:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda2 of=/media/LaCie/archaemic.iso
dd: writing to `/media/LaCie/archaemic.iso': Input/output error
3866625+0 records in
3866624+0 records out
1979711488 bytes (2.0 GB) copied, 143.012 s, 13.8 MB/s
ubuntu@ubuntu:~$ 

```

On the livecd, but as you can see there was an error. The external 500gb HD (LaCie) is not full for your information.

---

### Post by Tjcrazy on 2008-09-12
ANother UPDATE:

Now if I try booting the PC from hard disk there is nothing.Just the flashing _. Theres not evene a GRUB error.

Please help. Im beginning to think the worst has come.

---

### Post by Tjcrazy on 2008-09-12
Last update for the day:

PLEASE HELP! **_I_** cannot recover anything, I have got hours of work (websites, codes, graphics, school work) on the partition. The stupid thing is I was partitioning my HD so I could back it all up when this **** happened.

Please someone help me! I am willing to pay a small fee if you can help me recover all my files!

---

### Post by Pro-reason on 2008-09-12
> **Tjcrazy said:**
> UPDATE: I just did:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda2 of=/media/LaCie/archaemic.iso
dd: writing to `/media/LaCie/archaemic.iso': Input/output error
3866625+0 records in
3866624+0 records out
1979711488 bytes (2.0 GB) copied, 143.012 s, 13.8 MB/s
ubuntu@ubuntu:~$ 

```

On the livecd, but as you can see there was an error. The external 500gb HD (LaCie) is not full for your information.

Is LaCie OK?  Can you mount it and see what files there are on it?  Can you drag files to it?

---

### Post by Tjcrazy on 2008-09-13
Yep. LaCie is brand new, I can view files in it.

---

### Post by Pro-reason on 2008-09-13
> **Tjcrazy said:**
> Yep. LaCie is brand new, I can view files in it.

OK.  Try again then.

Make sure that LaCie is mounted.

Then do a test to see if you can write files to it:

```

echo "hello" > /media/LaCie/test.txt
cat /media/LaCie/test

```

The first command should create the file with no errors.  The second command should print "hello".

Does that work OK?

If so, then proceed to the next phase.

```

sudo dd if=/dev/sda2 of=/media/LaCie/archaemic.iso

```

---

### Post by Tjcrazy on 2008-09-13
Yep the hello thing worked.

While you were replying I was trying:

```
dd_rescue /dev/sda3 /media/LaCie/backuping.img 
```
(The corrupted drive is sda3 now... weird) 

But at about 1.9Gb it staretd outputting:

```

dd_rescue: (warning): /media/LaCie/backuping.img (5628352.0k): File too large
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /media/LaCie/backuping.img (5628416.0k): File too large!


dd_rescue: (warning): /media/LaCie/backuping.img (5628416.0k): File too large
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /media/LaCie/backuping.img (5628480.0k): File too large!


dd_rescue: (warning): /media/LaCie/backuping.img (5628480.0k): File too large
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /media/LaCie/backuping.img (5628544.0k): File too large!


dd_rescue: (warning): /media/LaCie/backuping.img (5628544.0k): File too large
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /media/LaCie/backuping.img (5628608.0k): File too large!

```

Stuff like that, its been outputting it constantly for a couple of minutes now, and I don't know when it started I think its still writing the backuping.img because the backuping.img is now 2.3Gb.


Also, I remember doing:
```

sudo dd if=/dev/sda2 of=/media/LaCie/archaemic.iso

```
Last night, and I got an input/output error.

Any help here?

---

### Post by Pro-reason on 2008-09-13
I think you are coming up against a [2GB filesize-limit problem]("http://linuxmafia.com/faq/VALinux-kb/2gb-filesize-limit.html").

I've forgotten how you make it copy in chunks of no more than 2GB.

On the other hand, you said that it seems to be continuing to grow, so maybe it's OK.  Just let it finish and see if it has worked.

If the /dev/ name of the drive keeps on changing, you should be able to run “sudo blkid” in order to find out what the UUID or LABEL of it is.  Then you can use that instead of /dev/.  For example, I can use /dev/sdb7 or LABEL=Ubuntu.

---

### Post by Tjcrazy on 2008-09-13
Unfortuanetly it stopped increasing at 2.3GB. Its still going in the terminal:

```


dd_rescue: (warning): /media/LaCie/backuping.img (41455552.0k): File too large
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (info): ipos:  41455616.0k, opos:  41455616.0k, xferd:  41455616.0k!
                   errs: 609344, errxfer:         0.0k, succxfer:   2457600.0k
             +curr.rate:     4491kB/s, avg.rate:    16126kB/s, avg.load:  9.2%
dd_rescue: (warning): /media/LaCie/backuping.img (41455616.0k): File too large
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /media/LaCie/backuping.img (41455680.0k): File too large!


dd_rescue: (warning): /media/LaCie/backuping.img (41455680.0k): File too large
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /media/LaCie/backuping.img (41455744.0k): File too large!


dd_rescue: (warning): /media/LaCie/backuping.img (41455744.0k): File too large
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /media/LaCie/backuping.img (41455808.0k): File too large!


dd_rescue: (warning): /media/LaCie/backuping.img (41455808.0k): File too large
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /media/LaCie/backuping.img (41455872.0k): File too large!

```

EDIT:

I just realized the dd_rescue I set earlier is still running... I set it to:

```
sudo dd_rescue /dev/sda3 /dev/sda2
```

I thought I cancelled this becausen I didn't mean it to go to the sda2 partition, which I just found out is a 30gb ext2 partition, because I cannon mount sda2. Its still running though:

```
ubuntu@ubuntu:~$ sudo dd_rescue /dev/sda3 /dev/sda2
dd_rescue: (info): ipos:  36011008.0k, opos:  36011008.0k, xferd:  36011008.0k
                   errs:      0, errxfer:         0.0k, succxfer:  36011008.0k
             +curr.rate:    13013kB/s, avg.rate:    12174kB/s, avg.load:  7.1%
```

END OF EDIT

EDIT 2
Now the ```
sudo dd_rescue /dev/sda3 /dev/sda3
``` has got an error:

```

escue: (warning): /dev/sda2 (37843456.0k): No space left on device!


dd_rescue: (warning): /dev/sda2 (37843456.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /dev/sda2 (37843520.0k): No space left on device!


dd_rescue: (warning): /dev/sda2 (37843520.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /dev/sda2 (37843584.0k): No space left on device!


dd_rescue: (warning): /dev/sda2 (37843584.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /dev/sda2 (37843648.0k): No space left on device!


dd_rescue: (warning): /dev/sda2 (37843648.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /dev/sda2 (37843712.0k): No space left on device!


dd_rescue: (warning): /dev/sda2 (37843712.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /dev/sda2 (37843776.0k): No space left on device!


dd_rescue: (warning): /dev/sda2 (37843776.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /dev/sda2 (37843840.0k): No space left on device!


dd_rescue: (warning): /dev/sda2 (37843840.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /dev/sda2 (37843904.0k): No space left on device!


dd_rescue: (warning): /dev/sda2 (37843904.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (info): ipos:  37843968.0k, opos:  37843968.0k, xferd:  37843968.0k
                   errs:   5442, errxfer:         0.0k, succxfer:  37495708.0k
             +curr.rate:     9450kB/s, avg.rate:    11973kB/s, avg.load:  6.9%
dd_rescue: (warning): /dev/sda2 (37843968.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /dev/sda2 (37844032.0k): No space left on device!


dd_rescue: (warning): /dev/sda2 (37844032.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /dev/sda2 (37844096.0k): No space left on device!


dd_rescue: (warning): /dev/sda2 (37844096.0k): No space left on device
dd_rescue: (warning): assumption rd(65536) == wr(0) failed! 
dd_rescue: (warning): /dev/sda2 (37844160.0k): No space left on device!

```

Any ideas?
END OF EDIT 2

EDIT 3
I did ```
mke2fs -S
``` on /dev/sda2 (I don't want to do it to sda3 until I know/think it works).
It seemed to do something, now I have done:
```
sudo e2fsck -y /dev/sda2
```
and it is doing loads of inode stuff:
```
Inode 2080756, i_blocks is 2146980029, should be 0.  Fix? yes

Inode 2080759 has INDEX_FL flag set but is not a directory.
Clear HTree index? yes

Inode 2080759, i_size is 16907935077165563527, should be 0.  Fix? yes

Inode 2080759, i_blocks is 687382306, should be 0.  Fix? yes

Inode 2080757 has INDEX_FL flag set but is not a directory.
Clear HTree index? yes

Inode 2080757, i_size is 11797321396749660322, should be 0.  Fix? yes

Inode 2080757, i_blocks is 1735766955, should be 0.  Fix? yes

```

Its been running 15mins(ish)

END OF EDIT 3

EDIT 4
Another edit, the e2fsck check has just outputted:
```

Restarting e2fsck from the beginning...
/dev/sda2 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Root inode is not a directory.  Clear? yes

Inode 36080 has illegal block(s).  Clear? yes

Illegal block #17 (1221311276) in inode 36080.  CLEARED.
Illegal block #49 (1221311276) in inode 36080.  CLEARED.
Illegal block #81 (1221311276) in inode 36080.  CLEARED.
Illegal block #113 (1221311276) in inode 36080.  CLEARED.
Illegal block #145 (1221311276) in inode 36080.  CLEARED.
Illegal block #177 (1221311276) in inode 36080.  CLEARED.
Illegal block #209 (1221311276) in inode 36080.  CLEARED.
Illegal block #241 (1221311276) in inode 36080.  CLEARED.
Inode 36080, i_blocks is 2248, should be 2112.  Fix? yes

Special (device/socket/fifo) inode 47685 has non-zero size.  Fix? yes

Deleted inode 48001 has zero dtime.  Fix? yes

Deleted inode 48002 has zero dtime.  Fix? yes

Deleted inode 48003 has zero dtime.  Fix? yes

Deleted inode 48004 has zero dtime.  Fix? yes

Deleted inode 48005 has zero dtime.  Fix? yes

Deleted inode 48006 has zero dtime.  Fix? yes

Deleted inode 48007 has zero dtime.  Fix? yes

Deleted inode 48008 has zero dtime.  Fix? yes

```

Ill wait and see what happens

END OF EDIT 4



Any other ideas, all I want are a few folders from my old partition and I will be OK to re install ubuntu. And this livecd is slow :(

---

### Post by Tjcrazy on 2008-09-13
SO... I am well and truly stuck now.

---

### Post by Tjcrazy on 2008-09-13
Well I got adviced to try installing fedora 9 live cd. Im on it now, but none of the ubuntu stuff (testdisk etc) works :(. ANy advice on what to do next?

---

### Post by Pro-reason on 2008-09-13
Hang on a sec... are you running a filesystem check and two recovery methods all at the same time??

One at a time!

---

### Post by Tjcrazy on 2008-09-14
Ok, I did:

```
ddrescue /dev/sda3 /dev/sda1
```

Sda1 is 41.9gb so this is what i got:

```
sudo ddrescue /dev/sda3 /dev/sda1

rescued:    40846 MB,  errsize:       0 B,  current rate:   20905 kB/s
rescued:    40854 MB,  errsize:       0 B,  current rate:   20905 kB/s
   ipos:    40854 MB,   errors:       0,    average rate:   17308 kB/s
   opos:    40854 MBr: No space left on deviceerage rate:   18362 kB/s
               

```

I then tried opening sda1 and I got an I/O error (It mounted OK)

Do you think I should try ddrescuing it to my 500gb external HD?

If I try:
```

ubuntu@ubuntu:~$ sudo ddrescue /dev/sda3 /dev/sdb1/
ddrescue: cannot open output file: Is a directory
ubuntu@ubuntu:~$ sudo ddrescue /dev/sda3 /media/LaCie/
ddrescue: cannot open output file: Is a directory

```
LaCie is again the external HD

---

### Post by Tjcrazy on 2008-09-15
Ive managed to dd_rescue my sda3 into a image. But if I go 
```
sudo e2fsck -y -b 32768 /media/disk/disk.img
```(Thats the hard drive image, all 69gb of it)
it still says:

```
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Group descriptors look bad... trying backup blocks...
Superblock has an invalid ext3 journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Corruption found in superblock.  (blocks_count = 0).

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 32768 <device>

```
Any help?

---

### Post by Tjcrazy on 2008-09-15
Sorry, but I really need help so I've gota BUMP this. This is a problem many experts are struggling with.

---

### Post by Tjcrazy on 2008-09-15
I hate double/triple/quadriple posting, but I need help. I am about to delete sda3 to reinstall ubuntu. I still need to fix the disk image I have. HELP!!! There is VITAL stuff on there, like my websites I was coding.

---

### Post by Pro-reason on 2008-09-15
I felt you weren't really listening to me, so I gave up.

---

### Post by Tjcrazy on 2008-09-16
I was listening, I did do them one at a time, and I managed to make the HD into an image. Now I still have the problem of fixing the HD image which has the errors I stated in previous posts.

---

