---
title: "[SOLVED] Monumental C**k up with permissions on external drive"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-09-25
Hi.
With a lot of music and 2 kids that love using ubuntu I decided to back up my music, reformat my external drive to ext3 with gparted. Copy it back then delete the back up.
Then I created users for my kids and chowned and chmoded around until I thought I`d made it so they couldn`t delete/ruin my collection.
You guessed it - I can`t mount my drive.

dmesg gives me
```

 EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 16895)!
[ 1457.568506] EXT3-fs: group descriptors corrupted!
```

I`ve tried editing /etc/fstab
and I`ve tried messing with group but I can`t figure it out.

Can anyone help or is it time to upgrade to Hardy (reinstall)

Thanks

---

### Post by unutbu on 2008-09-25
Do you still have your backup? 
It may not be necessary, but it would be comforting (to me) to know before I suggest anything (like fsck) which will change the state of your hard drive.

---

### Post by nothingspecial on 2008-09-25
No I don`t have my back up. I`d rather do a complete reinstall than risk messing up my drive with the music on it.

Thanks for the reply.

---

### Post by unutbu on 2008-09-25
Let's see if there is an easy fix that avoids doing a reinstall.

Please post the output of
```

cat /etc/fstab
blkid
group
```

Indicate which partition is the problem partition.

Then try ```

sudo e2fsck -nv /dev/sdXY
```
(changing /dev/sdXY to the correct device name for the problem partition)

The -nv flag above tells e2fsck to not make any changes to your hard drive (except to update the bad-blacks list -- which I don't think is the problem in your case).

It will show some output about what it would do to fix the filesystem without actually making any changes. Please post the output.

---

### Post by nothingspecial on 2008-09-25
cat /etc/fstab = 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5434314a-6c00-4959-9d4f-628e69d65b0b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=77c72610-6595-4969-8b9e-7cf415d807da none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

blkid = 

```
/dev/sda1: UUID="5434314a-6c00-4959-9d4f-628e69d65b0b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="77c72610-6595-4969-8b9e-7cf415d807da" TYPE="swap" 
/dev/sdc1: UUID="c3b02780-5aa1-4bb1-bb39-b2f2f507b7f0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="762bea99-f3fd-4c2f-9b47-928f6b863824" SEC_TYPE="ext2" TYPE="ext3" 

```
sudo e2fsck -nv /dev/sdXY = 


```
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: No such file or directory while trying to open /dev/sdXY

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

```

group = command not found

Thanks.

---

### Post by nothingspecial on 2008-09-25
Sorry the device in question is sdb1

---

### Post by nothingspecial on 2008-09-25
Sorry just copy and pasted. Here is the out put of sudo e2fsck -nv /dev/sdb1

```
Group 174's inode bitmap at 100781265 conflicts with some other fs block.
Relocate? no

Illegal block number passed to ext2fs_test_block_bitmap #336262480 for in-use block map
Illegal block number passed to ext2fs_mark_block_bitmap #336262480 for in-use block map

```

---

### Post by unutbu on 2008-09-25
Edit: Oops -- I didn't see your last post.

------------------------------------------

What is the output of 
```

sudo mount -t ext3 /dev/sdb1 /mnt
```

if it works, your music partition will be mounted at /mnt. 
If we are lucky, you might be able to browse the files using nautilus. If you run into a permission problem, try 
```

gksu nautilus
```

This will give you root permissions in the file browser.

If the "sudo mount..." command does not work, post the output.
Also post
```

sudo e2fsck -nv /dev/sdb1
```

---

### Post by nothingspecial on 2008-09-25
Same story `i`m afraid
```
wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The correct output of
```
sudo e2fsck -nv /dev/sdb1
```

is above if you`ve not seen it.

Thanks

---

### Post by nothingspecial on 2008-09-25
For some more imformation the message after
```

sudo e2fsck -nv /dev/sdb1
```

Went on for a few minutes. Do you need more info.

I don`t know how to go back up that far

```
Group 174's inode table at 100781766 conflicts with some other fs block.
Relocate? no

Group 174's inode table at 100781767 conflicts with some other fs block.
Relocate? no

Group 174's inode table at 100781768 conflicts with some other fs block.
Relocate? no

Group 174's inode table at 100781769 conflicts with some other fs block.
Relocate? no

Group 174's block bitmap at 100781264 conflicts with some other fs block.
Relocate? no

Group 174's inode bitmap at 100781265 conflicts with some other fs block.
Relocate? no

Illegal block number passed to ext2fs_test_block_bitmap #336262480 for in-use block map
Illegal block number passed to ext2fs_mark_block_bitmap #336262480 for in-use block map
Error reading block 1222336389 (Invalid argument) while getting next inode from scan.  Ignore error? no

Error while scanning inodes (2097152): Can't read next inode

```

---

### Post by unutbu on 2008-09-25
From your original post it seems like you were only altering ownership and permissions, 
and those kinds of actions should not lead to errors of this kind

Do you have any suspicion what might have caused this? Unplugging the drive without unmounting it first is one way these errors can occur.

I ask because if we knew what caused this, it might help us guess how extensive might be the data loss.

---

### Post by unutbu on 2008-09-25
The problem can not be solved by reinstalling Hardy.
The problem is in the filesystem on /dev/sdb1.

When fsck returns errors, the usual solution is to bite the bullet and allowing fsck to try to repair the errors using the command. 
```

sudo e2fsck -vy /dev/sdb1

```
The flags mean:
-v   verbose mode
-y   answer yes to all question (all e2fsck to repair non-interactively)

Note, however, that using fsck to repair errors can leave you with a working filesystem but one where some data has been lost. 

If you are very concerned about data loss, the safest route you can take is to clone the partition using a tool like Partimage ([http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)).
Then you can run "sudo e2fsck -vy /dev/sdb1" on the cloned partition. If it works, great, if not you can clone again and try other recovery tools.

If you clone the partition, run e2fsck, and find files missing, then the next step is to try using a data recovery tool. See [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery).
Photorec is one such tool, often recommended here at the forums. It searches the partition bit-by-bit and tries to recognize it as data files. Despite its name, it can recognize music file types, not just images.

I don't mean to scare you unnecessarily. It is possible that 
"sudo e2fsck -vy /dev/sdb1" will restore your partition with no data loss, 
but I don't want to tell you to do this without you first being aware that there is some risk.

---

### Post by nothingspecial on 2008-09-25
I have not unplugged the drive without unmounting. The data is still there from what I can see using gparted. All I know is that both my kids have used the computer without my supervision. But they shouldn`t be able to do anything.

Here`s gparted

[ATTACH]86393[/ATTACH]

---

### Post by nothingspecial on 2008-09-25
I seem to be replying at the same time as you do hence the missmatched order in this thread. I really appreciate this help.

I`m going to go to bed and try your suggestions tomorrow when I am thinking clearly. I really don`t want to loose all this.

Thank you again.

---

### Post by nothingspecial on 2008-09-26
Ok, There`s good news and bad news.
The bad news is I lost the lot, all 465gigs (except for 1 album).

However I am not downhearted. I have most of the music on another drive in mp3 format so I can still play my music. I also have the hard copies (cds), So I`ve got alot of ripping to do to restore my flac collection.

I would like to know what caused this so I can avoid this situation in the future. Anyone know?

I wonder why, of almost 20,000 tunes on that drive, e2fsck decided to save Pink Floyd`s "The Final Cut"?

---

### Post by Orange_and_Green on 2008-09-26
Dear nothingspecial,

I don't think I can contribute technically to this thread since my guess is as good as yours as to what may have caused that...

But I just feel I have to tell you how much I admire you for the cool attitude you are taking this with.

If something like this had happened to me, I think I would have bashed my head against the first 20 really hard things I would have come by...

---

### Post by unutbu on 2008-09-26
nothingspecial, I'm sorry to read of your loss. However, I'm glad you have backups of a sort in the form of CDs. You have certainly handled this with a cooler head than most. Hats off to you.

Filesystem errors like this could happen if the drive was abruptly powered off while in the middle of writing to disk. There might be other ways, but I can't think of any.

Next time, mounting the partition as read-only might help prevent this kind of disaster.

It is highly unlikely that 400+GB of data is really out of place in the filesystem, so it might be worth trying to use Photorec to recover more of the data so you don't have to re-rip it all.

Here are 2 articles demonstrating how to use Photorec:
[http://www.linux.com/articles/56588](http://www.linux.com/articles/56588)
[http://blog.mypapit.net/2007/10/how-to-recover-photo-files-from-sd-card-mmc-with-photorec.html](http://blog.mypapit.net/2007/10/how-to-recover-photo-files-from-sd-card-mmc-with-photorec.html)

Best wishes and good luck.

PS. It is probably the case that anyone who deals with computers long enough will suffer a catastrophic loss of data at some point. On the positive side, only after you've experienced such a loss does the drudgery of backing up seem so keenly interesting.

---

### Post by silverglade00 on 2008-09-26
> **nothingspecial said:**
> 
I wonder why, of almost 20,000 tunes on that drive, e2fsck decided to save Pink Floyd`s "The Final Cut"?

Good taste? :p

Seriously, you put up a good fight and I would have lost it long before I got to the point you did.

---

### Post by nothingspecial on 2008-09-26
Thanks for the encouragement guys.
 Honestley it`s not so bad. 
 The best thing is that every vinyl lp I converted (audacity) is backed up.  Doing all that again would be a right pain in the a***.
 Like I said, I`ve got most of my music on the original cds so as I rip my way through the first box (they`ve all been consigned to the attic since January), I`m getting to look at them again which is kind of nice if you know what I mean.

Since they`ve all been on the pc, I`ve hardly ever listened to an album the whole way through. However good cover art support is, it`s not the same as looking through a shelf of cds and choosing one to play. 99% of the time, I just hit random.

 Since I`ve started this again I`ve actually listened to a couple of cds all the way through. So at the moment, I`m kind of enjoying it.
 And when I`m done, I`m going to copy the whole lot to a drive and put it away, so a valuable lesson learned.

 I`d still like to know what happened though.

---

### Post by nothingspecial on 2008-10-02
I`m up to 6228 songs. Nearly a third of the way there.

:guitar:

---

### Post by nothingspecial on 2008-10-17
13,974 of 19,333. Getting closer.

---

### Post by Orange_and_Green on 2008-10-17
:KS:KS:KSYAAAY, the first half is done:KS:KS:KS
Keep it up my friend!!!

---

### Post by nothingspecial on 2008-10-17
Thankyou. Got my wife and kids involved too. Anyone passing the family pc, seeing the disk drive open, rips another.

:guitar:

---

### Post by Orange_and_Green on 2008-10-17
I wish there will be such coop projects also in my family when the time comes for me to have a family too... just sounds so lovely. Well keep it up everybody and save daddy's record collection!!:guitar:

---

### Post by nothingspecial on 2008-11-02
Done finally. I lost a few songs along the way but it was a good experience.

Back up people, back up.

[ATTACH]90790[/ATTACH]

Thanks for the encouragement and help.

---

### Post by sdowney717 on 2008-11-02
external drive?
Well could the drive have been knocked, fallen, hit, tapped. or somehow banged around?

A German Shepard caught under the desk wrapped itself in the cords body slammed the PC and the drive was wiped out.

---

