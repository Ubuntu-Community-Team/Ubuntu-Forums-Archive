---
title: "Noob using testdisk and confused_ Noob at Ubuntu too"
date: 2017-12-16
forum: New to Ubuntu
---

### Post by trevgauth on 2017-12-16
So I did a dumb thing #-o and here's some back-story. So frustrated with windows 10, I finally decided to try Ubuntu. I used a USB to give it a try, and I really liked it. So I wanted to dual boot, because even though I hate windows 10, there are some programs that just wont work blah blah blah..... anyways. I was going to use the partition wizard in 16.04 LTS. When I clicked on the partition, I didn't realize the format box wasn't "unchecked" and I accidentally did that. After realizing what I had done, I went no further then the next screen. I at least know not to further save over my data. However now, of course, widows is not bootable now, because Ubuntu partially saved over it. 

There are quite a bit of things I should have done but didn't. Like I really should have bought a backup HDD "before" I did this. I really should have used that drive to backup my important files "first" and I tried over and over to get windows to make a recovery disk, but it kept failing, so yeah that is not done either. I do however have another computer using widows 10 in the living room, bu that HDD is almost full.

I can't figure out how to get testdisk to work. I did figure out Photorec, and recovered and it saved most of my data, but it is all unorganized, the file names are all changes, there are only folders with 500 files in them, with any file in them. there are images and mp3 along with dll files. So finding specific files in around 300,000 files is a bit daunting, so I'm hoping to recover things a bit better.

I have read that testdisk can recover file systems? like My camera raw file folders that I had organized? For instance: Photos -> 2017 -> July -> Image5009.cr2, mycat.jpg (lol) etc.
or am I wrong about the capabilities.

So I have done a clean install of ubuntu 16.04 64bit on a new 2TB HDD, and have around 600Gb of data on the old drive. So I should have plenty of room on the new drive. However I just don't know what I am doing. I'm still a noob, I was hoping to learn Linux gradually, and wean myself off of windows, now I am having to do a crash course on Linux whether I like it or not. I _somewhat_ have and understanding of using terminal, but there are quite a few things I just  do not understand yet. So if anyone wouldn't mind helping me, you have my permission to walk me through this like a child (ok actually a child would be better at this) or better yet, like a caveman lol.

I would really appreciate some help. For now I haven't been dumb enough to touch any of the data on the HDD in question, so whatever might be recoverable, is still (hopefully) recoverable. I realize I did a series of really dumb things, but what is done is done, so lets not dwell on that please. Thank you in advance.

---

### Post by oldfred on 2017-12-16
Not sure what you overwrote.
Was all you data in one very large partition, making it more difficult to recover.

Testdisk has deeper search and that will recover full file names. But when that does not work, you do use photorec.
If NTFS, some have posted that Windows tools may work better.

       An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam. 

Always best to use Windows tools for Windows & Linux tools for Linux.
And then only use Windows to shrink the NTFS partition.
And backups before any system change are required. But hard drives do fail, so good backups are always required.

---

### Post by yancek on 2017-12-16
The testdisk site at the link below has a lot of documentation including a Step By Step tutorial including recovering files from an ntfs partition.

 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by trevgauth on 2017-12-16
[IMG]https://i.imgur.com/rEPJLBV.png[/IMG]


Would the old windows partition be the one highlighted?


I don't even want windows back per say, just my old file structure if possible.

---

### Post by yancek on 2017-12-16
> Would the old windows partition be the one highlighted?]

I would think so as you only have two windows (ntfs) partition and the other is much smaller.  Good luck!

---

### Post by oldfred on 2017-12-16
Did you install with the LVM or LVM with encryption install options?
Those are full drive or entire hard drive is erased as LVM then takes over. You only have as physical partitions /boot and a partition for rest of drive as container for the LVM. If UEFI, you also have an ESP (FAT32) partition for UEFI.

I consider the LVM an advanced option that should only be used by those knowledgeable with Linux as different partition tools are required. But if you want full drive encryption, you have to jump into the deep end of the pool & sink or swim (learn LVM quickly).

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

---

### Post by trevgauth on 2017-12-17
> Did you install with the LVM or LVM with encryption install options?

No I did not, but I think I got it figured out.

> I would think so as you only have two windows (ntfs) partition and the other is much smaller.  Good luck!         

I think it did the trick.

There are some corrupted/unrecoverable files. However, I think I'm at a conservitive 80-90% it's funny how some folders are intact yet every file in them are gone, but considering I thought I might never see them again, I'm happy with the results. 

Thank you, yancek! and oldfred! :)

---

