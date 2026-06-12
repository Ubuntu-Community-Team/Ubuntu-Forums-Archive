---
title: "[SOLVED] Converting my storage drive to ext3"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-11-25
I have two drives. One for OS and programs, one for multimedia and the like.

When I switched to Ubuntu I just reformatted the OS drive to ext3 on install. Since then my storage drive has remained NTFS so I cant delete things to the trash or see remaining times for file transfers, etc...

I don't have any backup solution large enough to backup the entire disk, but I can make enough space on my OS disk to backup half of it at a time.

So here's the point of all this. Can I dump as much of my storage drive into a folder on my OS disk, then convert the free space on the storage drive to an ext3 partition then copy the backed up info back to the newly created ext3 partition.

*deep breath*

THEN copy the remaining files from whats left of the NTFS partition to the backup folder on my OS drive, and have the new ext3 partition take over the NTFS partition to create two whole ext3 disks? And all this done without any serious risk of losing data?

I've got a few thousand songs, a decent video library and a few hundred thousand pictures that I would rather not lose along with some more important business related documents and I really dont have the cash on hand for a backup system right now.

If anyone can actually follow what I just said, I would love some feedback as to whether or not this will work, or if there is an easier way. As I understand it there is no way to convert a file system and keep data in tact.

---

### Post by handydan918 on 2008-11-25
I think what you propose should work. It is obviously not "plan A", but given that you can't afford a "backup solution", it may be the best you can do. 
The other possibility is to look into a compressed archive ( see man tar...)

However, if there is no major heartburn with the system you have now, you could just hold off until you can buy another drive. Internal would work, and they are getting really cheap.
Alternatively, what about the possibility of borrowing an external? you wouldn't need it for long.....

---

### Post by bodhi.zazen on 2008-11-25
I was going to say, you need to move your data off the disk, reformat, and the move it back on.

Move as much as you can, hopefully a little over half, off the disk. Then use Gparted and resize the partition. Make an ext3 partition in the new free space (you will need to do this in two steps).

Move as much data back as possible.

Then repeat ...

---

### Post by HittingSmoke on 2008-11-25
> **bodhi.zazen said:**
> I was going to say, you need to move your data off the disk, reformat, and the move it back on.

Move as much as you can, hopefully a little over half, off the disk. Then use Gparted and resize the partition. Make an ext3 partition in the new free space (you will need to do this in two steps).

Move as much data back as possible.

Then repeat ...

Thanks to both of you, this is exactly what I was hoping would work.

Unfortunately, I'm the only geek i know. Most of my friends would hand me car keys if I asked to borrow a drive.

---

