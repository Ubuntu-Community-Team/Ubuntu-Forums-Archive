---
title: "mbr error on boot"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Tim Silver on 2008-07-08
Hi,

I've been using the heron for a couple of months now with few problems other than those caused by me!

Went to boot last night and got 'MBR Error' and stop! - I really don't know what I've done this time. Was using laptop on battery and ran-out. I guess there was no proper shut-down (but what do I know).

I dual boot to an external USB HDD on a Dell Inspiron 9400 (XP on internal drive - rarely used since discovering the heron). Of course the GRUB is on the external drive, so I can't even get in to Windows.

I've booted using the livecd but cannot figure out how to get the important files off the drive before I reinstall.

Any help much appreciated as I would like to retrieve my work. Or must I just reinstall?

I have searched the forums, but haven't found anything that matches my situation.

---

### Post by Rocket2DMn on 2008-07-08
I would run a file system check from the LiveCD.  Boot it, check the device location with
```
sudo fdisk -l
```
Assuming /dev/sdb1 as your root partition, make sure it is unmounted
```
sudo umount /dev/sdb1
```
Then run fsck:
```
fsck /dev/sdb1
```
After that, I would try to reboot from the drive.  If that fails, try reinstalling GRUB with the Super Grub Disk - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Then if THAT fails, you can boot from the LiveCD, mount the partition manually, backup your files somewhere else (like to another external drive or to your windows drive).
```
sudo mkdir /media/external
sudo mount -t ext3 /dev/sdb1 /media/external
```
Then mount your windows partition (or other device)
```
sudo mkdir /media/backup
sudo mount -t ntfs-3g /dev/sda1 /media/backup
```
For /dev/sda1 substitue for whatever partition you are backing up to, and change the filesystem option (-t <filesystem>) accordingly.

---

### Post by iaculallad on 2008-07-08
I must assume that you're running the windoze OS when you're laptop run out of power? Sometimes, drive errors are left on drives when not properly shut down. Try to reinstall GRUB using the LiveCD, following the instructions in this [thread]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by Tim Silver on 2008-07-08
Thanks for replies - I'll not be able to do anything for a few hours as I'm at work at the moment - have to wait till lunch break.

Iaculallad, I'd like to be able to put the blame on XP but I can't. It was the heron that was running at the time - really took me by surprise and that's why I'm sure that I must have done something!

Having said that, my machine was built for Windows and I have had an unexplained 'white screen of death' a few times. Maybe the two coincided.

---

### Post by renzokuken on 2008-07-08
just putting in my (probably irrelevant) two-cents here, but could it be that the device boot order has changed in the bios, and so is looking for mbr on a disc that doesnt have one?

this sometimes happens randomly on my desktop (possibly due to flat cmos battery) and i have to reset the boot device order to boot up again

---

### Post by Tim Silver on 2008-07-08
Hi renzokuken,

That had indeed happened (I'd heard of that before somewhere). The BIOS had reset to 'internal' HDD (I had set it to USB HDD which is where the GRUB resides).

When I first tried to boot I got an Error 17 message. After reseting the BIOS to USB HDD, that error message disapeared and I got the MBR Error message. Does that make sense?

---

### Post by renzokuken on 2008-07-08
yeah perfectly......well we can rule that out then.

how exactly are your drives partitioned? i.e. from what i understand, windows (and hence the MBR) is on your laptop harddrive, and ubuntu (including grub) is on your external drive?

one option may be to run fixmbr on your internal hardrive, then use Super Grub CD to reinstate grub on the external

---

### Post by Tim Silver on 2008-07-08
Yup, my internal is XP - just as it came from Dell. The heron is exclusive to the USB drive. (I didn't want to compromise either through alcohol induced stupidity:lolflag:).

I think my MBR also resides on the external drive because when I boot into the heron, there is no sign of activity on the internal drive. However, on the odd occasion that I boot to XP, the external drive is being read and I think for longer than just reading the GRUB (I read somewhere that this is a very small file).

Does this make it better or worse?

---

### Post by Tim Silver on 2008-07-08
Iaculallad,

If you're still following this thread, I started with the how-to you pointed me to - but stumbled at first hurdle!

grub> find /boot/grub/stage1 gets me Error 15: File not found

Does this mean I have to do the 'mkdir' and 'mount' stuff as in the edit of the how-to?

---

### Post by Bucky Ball on 2008-07-08
My holy grail for working out grub probs, if it is that ...

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Good luck ...

---

### Post by unutbu on 2008-07-08
Could you post

```
sudo fdisk -l
```

and also try
```

sudo grub
grub> find /grub/stage1
```

I don't know if I can fix your problem, but I can tell you that Error 15 means
> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 
(See [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting))

---

### Post by Tim Silver on 2008-07-08
OK anyone,

I'm really in the 'cack' now!

Just downloaded supergrub iso, burned cd, inserted in to drive, set BIOS to read from cd drive and guess what... MBR Error!

Can still boot from livecd though. What now please.

---

### Post by Bucky Ball on 2008-07-08
?

That is odd, but supergrub should have booted? Sure it is right version for your machine (probably a silly question)?

As it says on the site, SupergrubDisk is good, but not perfect! But might be proof you no longer have a grub or mbr anywhere!

As Unutbu says, maybe locate the /grub/stage1.

---

### Post by Tim Silver on 2008-07-08
Output of fdisk -l

Well, there's load of stuff - if you don't need to see it verbatim essentially it's seeing two HDD's.

Disk /dev/sda: 78.5 GB (gen. info stuff)
comprising
/dev/sda1 Dell utility
/dev/sda2 HPFS/NTFS
/dev/sda3 HPFS/NTFS
/dev/sda4 CP/M / CTOS / ...

Disk /dev/sdb: 40.0 GB
comprising
/dev/sdb1 Linux
/dev/sdb2 Extended
/dev/sdb3 Linux swap / Solaris

Hope you don't mind me missing stuff out, but would have been loads of typing and hence plenty of room for errors!

As for find /grub/stage1 - Error 15: File not found.

---

### Post by Bucky Ball on 2008-07-08
sorry, see what you find here and if it looks anything like mine;

> cd /boot/grub
dir

This is mine for comparison;

> default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5	  reiserfs_stage1_5
e2fs_stage1_5  menu.lst		  stage1
fat_stage1_5   menu.lst~	  stage2

No doubt it won't look exactly the same but the important thing for you is the stage1 and stage2.

If you can't cd to the /boot/grub directory in the first place that is bad, but if the stage1 file is missing there will be no boot.

---

### Post by unutbu on 2008-07-08
Tim, I'm going to assume that when you installed Ubuntu, that you installed GRUB on the MBR of /dev/sda  (your internal drive). If that is not correct, stop and please post. If you are not sure, post -- there is a way to find that out as well.

Boot from the LiveCD.
Open a terminal and type
```
sudo grub
root (hd1,0)
setup (hd0)
quit

```
Reboot. Watch carefully and try to remember any words that come up on the screen.

If it doesn't work, post back here and describe what you saw.

Edit: To follow Bucky Ball's advice, you'll need to mount your Linux partition first:
[http://ubuntuforums.org/showpost.php?p=5343818&postcount=3](http://ubuntuforums.org/showpost.php?p=5343818&postcount=3)
This is a good idea; you will at least feel a lot more secure knowing (hopefully) that your data is still there.

---

### Post by Tim Silver on 2008-07-08
I'm too old for this! :-)

Right, re above code, the first two lines were OK but when I entered 'setup (hd0)' I get - Error 17: Cannot mount selected partition

Regarding other thread you pointed me to, when I entered 'mount /dev/sdb1 /Ubuntu' I got the message 'mount: you must specify the filesystem type'

---

### Post by unutbu on 2008-07-08
What happens when you type
```

sudo mount -t ext3 /dev/sdb1 /Ubuntu
```

---

### Post by Tim Silver on 2008-07-08
Looks like bad news!
```
sudo mount -t ext3 /dev/sdb1 /Ubuntu
```
gets me -

mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so

I entered 'dmesg' and got several screens-full of output - did notice a couple of disturbing lines - one read 'apm: BIOS not found' and another (the last) read 'VFS: Can't find ext3 filesystem on /dev/sdb1.

---

### Post by unutbu on 2008-07-08
I am really just repeating Rocket2DMn's post #2:

What do you get when you type
```
fsck /dev/sdb1
```

fsck is meant to fix any filesystem errors.

---

### Post by Tim Silver on 2008-07-08
Well, I'm afraid that I focused on one theme and forgot Rocket2DMn's post - sorry Rocket, no offence meant.

Just did fsck - if only I knew what I was doing!

After typing 'y' about 80 times regarding stuff about 'Inodes' (- I mean, the heron was suggesting I respond with 'y') I now have -

File /home/tim/.local/share/tracker/data/common.db (inode #230522, mod time Mon Jul 7 17:20:28 2008)
  has multiply-claimed block(s), shared with 1 file(s):
       /home/tim/.nautilus/saved-session-9Y9IDU (inode #231074, mod time Mon Jul 7 17:20:28 2008)
Clone multiply-claimed blocks<y>?

Should I enter 'y' to this?

Those smileys shouldn't be there - 2008 )

---

### Post by unutbu on 2008-07-08
I think it is okay to say yes to all the questions. You are at the mercy of fsck to choose the right thing. There may be some damage and some files may be missing. 

You would have to be a unix wizard of a calibre way beyond me to know when to say no.

At least the files fsck is talking about are not very important. They are config files used by tracker and nautilus and can be regenerated:
> 
home/tim/.local/share/tracker/data/common.db 
/home/tim/.nautilus/saved-session-9Y9IDU

---

### Post by Tim Silver on 2008-07-08
Well, just spent the last +40 minutes clicking the 'y' key! Rebooted. Got the dual boot options screen. Clicked on Ubuntu (1st option) and am now stuck with the following message - 

init: /etc/event.d/documents/README:1: Unknown stanza

Now what? Should I forget my family tree database and just re-install?

---

### Post by Bucky Ball on 2008-07-08
Perhaps the "README:1" file in the directory "/etc/event.d/documents" is corrupt or shouldn't be there. Try opening it if you can and having a look.

I just had a look at my /event.d/ directory and there is no /documents/ directory and no /README:1 file. That is what is locking you up. I did a search and I have a lot of tty entries in there. People seemed to be getting the message you are getting with Feisty; boot stopping at /etc/event.d/tty directory. It was a bug that seems to have been fixed.

Did you have a directory called 'documents', exactly the same as the one that it is halting on? Cos it shouldn't be there I don't think. Hopefully some wiser heads might enlighten us, you could try moving the directory and rebooting, see if that shoves it. :) Good luck ...

---

### Post by unutbu on 2008-07-08
My guess is that you didn't have a /etc/event.d/documents directory before the battery ran out. fsck tried to put the filesystem back together again, but got the documents directory wrong. 

If fsck made this mistake, there are probably going to be others, so I'm not very confident that making Ubuntu boot would be very easy.

So, let's try to copy your data from Ubuntu to Windows:

Boot from the LiveCD.
Open a terminal, and type

```
sudo mkdir /Ubuntu
sudo mount -t ext3 /dev/sdb1 /Ubuntu
```
(Hopefully, this works now)

```
sudo mkdir /Win
sudo mount -t ntfs-3g /dev/sda3 /Win
```
(Again, this is really just Rocket2DMn's advice in post #2). You can use either sda2 or sda3. I'm not familiar with what kind of filesystem you have on sda4 however. If you want to write there, I'll have to do some research if linux can mount and write to a CP/M / CTOS filesystem... (Edit: CP/M Concurrent DOS, CTOS is a hidden partition used to reinstall Windows, so you don't want to write there anyway.)

Your Ubuntu filesystem should all be located within /Ubuntu
and your entire Windows filesystem should all be located within /Win.
Now use nautilus to copy everything you want to save from /Ubuntu to /Win.

---

### Post by Tim Silver on 2008-07-09
Unutbu,

I cannot mount the directory Ubuntu -

```
sudo mount -t ext3 /dev/sdb1 /Ubuntu
```

returns a message - 

mount: mount point /Ubuntu does not exist.

Looking via the file browser, it does - with the correct date/time stamp.

I was exploring last night (with my best Windows reasoning ;-) ) and as far as I can make out the info I most want to recover is damaged anyway. Although the file browser would display the names of the files, when I looked at the properties tab, they were all 'unreadable'. I've got back-ups that are only about a week out of date so I think I'll go down the re-install road. Thanks all for bearing with me on this one - you'll be able to keep up with my progress as I post on how to configure my machine - seem to recall it wasn't that straight forward before. Once again, thanks all.

PS I'm not giving up on the heron though - I like it too much and the ethos of the open source community is brilliant!

---

### Post by Bucky Ball on 2008-07-09
Cheers Tim Silver and all the best in your endeavours.

Wipe the drive, load windows in a partition, make up some partitions (or not, once windows is up), load Hardy, which will ask you at the end of install if the Windows OS it is identifying for you is correct. When you say yes it will install grub onto the MBR and include both OS. Reboot and you should be looking at a grub giving you a selection of Hardy and Windows. That easy! lol

Incidentally, being an old Windows hack and a convert to a better computing world (!), I always load my windows on a seperate partition from anything else and avoid storing anything on that OS partition (personal data). Then if it crashes, all data remains, just windows partition screwed. That way, wipe the partition and reinstall windows, reboot and your data is all there. Nothing really changed. Also, if the disk crashes, there is a better chance of retrieving data from the other partitions; usually one bad sector on the entire disk ... therefore if the disk has 3 partitions, only one dead partition (in theory).

Hope it all goes smooth but each version of Ubuntu seems to get easier to setup.  Hardy is no exception ...

---

