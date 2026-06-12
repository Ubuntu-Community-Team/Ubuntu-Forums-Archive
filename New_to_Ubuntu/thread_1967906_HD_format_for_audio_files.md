---
title: "HD format for audio files?"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by smcrossman on 2012-04-28
First off no I haven't really searched on this. I'm in midst of multpile projects and this is a bit of a side line.

I am currently wiping & formatiing an external hard drive to back up my network storage since I'm having issues with networking and may have to go back to factory specs.  Anyway....I will have a decent portion left over that I thought would be a good place to save my audio files until I'm sure everything is stable.

What I'm wondering is what is the best format for the partition that will be storing my audio files?  At some point in the future I will be looking to clean up some older bad rips of CDs as well as adding LP and cassette recordings to it so the format of the files themselves isn't overly important to me right now. BUT I'd like to at least get the disk formatted so that as I go through the future steps it is a good medium for storing and organizing.

I use iTunes, iPhone, Android, and various things here in Linux. I really try to avoid the Windows products, but a lot of my older things were burned using Media Player. I'm just not sure which to go with: FAT or NTFS or EXT2,3,4.  Anyone know anything about this and willing to give me a little guidance?

---

### Post by Cheesemill on 2012-04-28
It doesn't make any difference if you are storing audio files or not, the filesystem has no impact on the quality of the files.

If you need the disk to be readable by Windows then go for NTFS, if you only use Linux then go for ext4.

---

### Post by SeijiSensei on 2012-04-28
Unless you need to access the drive from Windows I'd go with ext4.  If you do need Windows access, your best bet is ext2 for which the Windows driver is quite stable.  ext3 can be used, but it's [not fully supported]("http://www.fs-driver.org/faq.html#acc_ext3").  ext4 is right out.

If the drive is large, say > 40GB, the absence of a journal in ext2 means that checking the disk for errors will take a long time.  With an external device that means you need to be very careful to unmount the device before disconnecting it to insure that the filesystem won't become corrupted and require running fsck when brought back on line.  

The fact that the files you intend to store are music files is pretty irrelevant to all of this except for the fact that they aren't very large.  Large files that run into the gigabytes like videos are handled better by ext3/4.

I would definitely not use XFS on an external device. I had an external device with XFS, and it would become corrupted any time it experienced a loss of power without being completely unmounted first.  Unless the drive is connected to a UPS, I'd definitely use ext4 over XFS.

If you want to use a Windows format, you should definitely choose NTFS over FAT32 since the latter has a limit on file sizes of 2 GB, which isn't very large by today's standards.  Most movies are considerably larger than that unless they're heavily compressed.

---

### Post by JC Cheloven on 2012-04-28
> **cheesemill said:**
> it doesn't make any difference if you are storing audio files or not, the filesystem has no impact on the quality of the files.

If you need the disk to be readable by windows then go for ntfs, if you only use linux then go for ext4.

+1

---

### Post by smcrossman on 2012-04-28
Thanks folks!  With the exception of the fact that my iTunes is on my Win 7 drive I don't expect to be using this with Windows.  I'm using my NAS to back up my Windows partitions and my Linux partitions so my iTunes files should be accessible from it if I were to need to copy them out separate, but most of my music is from personally owned CDs, LPs & cassettes. 

My NAS is actually formatted in EXT2 (per manufacturer) which is what I did the "backup" portion in. And I'm planning on moving most things over to it or into my Home partition for use so the extra copies on the external will be coming from those two places. So I guess I'll use EXT3 or 4 since journaling can't hurt with a lot of littler files with metadata/tags involved!

---

