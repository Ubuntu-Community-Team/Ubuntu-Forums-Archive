---
title: "Can You Keep What You Unmount?"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by stone3 on 2014-05-08
Situation:
I have my drive partitioned with Ubuntu 12.04 on one partition, XP on another, and the boot partition. 
Initially, I wanted to nuke XP and go all Ubuntu all the time, but I cannot resolve a connection issue with the printer when attempting to print while in Ubuntu. Also, there are other minor reasons that just make it simpler for now to keep XP for the moment.

Plan:
What I would like to do is reduce the size of the XP partition to its absolute minimum size that will allow me to work on some documents and print (unless someone has a solution for this also). I would like to add this space to Ubuntu. I am an excellent driver but alas, I am a less-than-nominal mechanic.  Any clear step-by-step instruction would be greatly appreciated. (*,)

Thanks.

---

### Post by sydney2 on 2014-05-08
Could be more specific on what are U exactly planning

---

### Post by deadflowr on 2014-05-08
What's the printer?
And what is the setup?
(Is it directly connected to the machine, or is it networked?)

And what kind of documents would you be working on?

Apart from that, the bare minimum for XP would somewhere around 10GB, I would assume.
It's probably less, but if you need a certain document editor, then at least 10GB sounds good.

On top of this you would also need some headroom for the documents themselves, as Windows XP can't see linux partitions, and so trying to save them on the linux side won't work. Or at least would take some considerable effort.

---

### Post by Impavidus on 2014-05-08
Could you show us your current partitions? Use```
sudo parted -l
```in a terminal and post the output.

---

### Post by vanadium on 2014-05-08
You may want to keep your documents, data etc. on an ntfs partition, so these remain accessible both from within Windows and Ubuntu. In your current setup, this may mean that you just leave your documents on the Windows partition. In Ubuntu, you could easily replace the document folder by a link that brings you to the location where your documents are. Links are created by dragging a folder to where the link needs to be created, while keeping Ctrl+Shift pressed.

---

### Post by stone3 on 2014-05-08
To Sydney2, Deadflowr: I was initially planning to go completely XP free and fully Ubuntu, but I cannot get my Lexmark Pro900 to print, cannot edit Acrobat or Photoshop files like I do in XP, I cannot I get iTunes to work, or arrange my music files when I am in Ubuntu.

Regarding the printer, I followed directions (from Ubuntu forums) regarding downloading the appropriate drivers and set up, but still have not had success in getting the Lexmark to work while in Ubuntu. Perhaps there was error on my part but I am uncertain.  It is directly connected to my computer.  The documents that I need to compose, edit, and print are primarily Word, Excel, Acrobat, Photoshop, and some graphics files (jpg, eps, tif, etc).  

So, I thought the simplest route would be to keep the XP partition along with the Ubuntu partition I have, just reduce the XP partition to its absolute minimum size that will allow it to function adequately (printing, editing).  According to the information online, I should unmount the partition that I want to resize. I was curious as to what will happen if a mounted partition is unmounted.  However, if you can answer any of the previous issues I stated then that would be great.

I also read that it may be possible to access files cross-partition (from Ubuntu to XP and vice-versa).  Is this so?

----------

To Impavidus: When I entered "sudo parted -l" into a terminal, I got "[sudo] password for stone:" 

----------

To Vanadium: What is the process to do the following?
"[COLOR=#000000]You may want to keep your documents, data etc. on an ntfs partition, so these remain accessible both from within Windows and Ubuntu. In your current setup, this may mean that you just leave your documents on the Windows partition. In Ubuntu, you could easily replace the document folder by a link that brings you to the location where your documents are. Links are created by dragging a folder to where the link needs to be created, while keeping Ctrl+Shift pressed.[/COLOR]"

Thanks to all. Please let me know if more data is needed. Again, I really appreciate the guidance!

---

### Post by deadflowr on 2014-05-08
Is this the printer?
[http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=2](http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=2)

As well, did you input your password when you ran the sudo parted -l command?

Or do you have a general idea of how big a hard drive you have.
with all the stuff you want to do, you will probably need at least 20GB space for XP.
More, depending on the documents themselves.

---

### Post by stone3 on 2014-05-09
> **deadflowr said:**
> Is this the printer?
[http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=2](http://www.phoronix.com/scan.php?page=article&item=lexmark_linux&num=2)

As well, did you input your password when you ran the sudo parted -l command?

Or do you have a general idea of how big a hard drive you have.
with all the stuff you want to do, you will probably need at least 20GB space for XP.
More, depending on the documents themselves.

-----
To Deadflowr:
1) Yes, that is my printer (single paper tray only).

2) Tried "sudo parted -l" again. Here is the data:

Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start      End        Size     Type         File system  Flags
 1          32.3kB   210GB    210GB  primary     ntfs             boot
 2          210GB   1000GB   790GB  extended
 5          210GB   1000GB   790GB  logical       ext4

3) If I could live without Windows, I WOULD. However if not, minimizing its (Windows) influence would be acceptable.

---

### Post by deadflowr on 2014-05-09
Personally, I would keep it as is.
200(roughly)GB is a little big, but more than enough room to keep doing what you need to do in Windows.

If you did want to shrink it, then it's normally recommended to first defragment the partition using XPs disk management tools.
Then you can use gparted, or another partitioning tool to resize/shrink/reallocate.
Gparted comes with the Ubuntu liveCD, but isn't installed during installation. But you can install it from the software center.

---

### Post by vanadium on 2014-05-09
> **vanadium said:**
> You may want to keep your documents, data etc. on an ntfs partition, so these remain accessible both from within Windows and Ubuntu. In your current setup, this may mean that you just leave your documents on the Windows partition. In Ubuntu, you could easily replace the document folder by a link that brings you to the location where your documents are. Links are created by dragging a folder to where the link needs to be created, while keeping Ctrl+Shift pressed.

A symbolic link is like a shortcut in Windows. You create such a shortcut by dragging a folder to where the link needs to be created, while keeping Ctrl+Shift pressed.

The shortcut assures that you can easily navigate from your home folder to the actual data.

Yuo could reserve enough space for Ubuntu for the system and user configuration data, but not more, because you will be keeping your data on the Windows ntfs partition. For that, a partition of 10-15 GB is plenty. To that, add space for your swap partition slighly in excess of your system's memory. Say you have 8 GB of ram, then reserve 9. So you could reserve 20 - 22 GB for Ubuntu.

---

### Post by Impavidus on 2014-05-09
You could shrink the Windows partition to 20GB, which may be all you need. As a 90% reduction is size this is a significant change. But on the other side, you can expand the Ubuntu partition to 980GB, which is only a 24% increase. That isn't much. If you can fill a 790GB partition, you only need little more time to fill a 980GB partition. So there is little to gain from this change.

I find it remarkable how often people count on a linear scale where they should count on a logarithmic scale. Our brains work logarithmically.

---

### Post by sudodus on 2014-05-09
- It is risky to edit partitions. You should always have a good (tested) backup before doing it.

- If you decrease the size of the Windows partition too much, Windows will not work well. It needs at least 30% free space to avoid excessive file fragmentation. 50% will give you some margin for new files. And remember that Ubuntu can read files from NTFS file systems.

- I agree with the other people suggesting that you keep the Windows partition. But if you really want to shrink it, yes, it is possible, but check how much is used and how much is free, and leave enough free space, say 50% extra, so if you have 50 GB data, add 25 GB, so shrink it to 75 GB.

- Finally, remember that XP has passed end of life and will receive no security updates. It is a good idea to disconnect the computer from the internet, when running XP.

---

### Post by stone3 on 2014-05-09
To Impavidus, Sudodus: Thank you for the instruction regarding the Windows partition. I am clearer now regarding the implications of resizing it as per your explanations.
 
I avoid surfing the web when in Windows. I edit Acrobat files and copy to a Seagate external hardrive, or print to my Lexmark Pro900.  I still have Trend Micro Titanium installed in Windows.  It is a shame that Trend Micro provides no such protection for Linux.

From the info that I provided, it is possible to be XP free and print using a Lexmark Pro900, edit Acrobat files, install and use iTunes or something comparable (where I can arrange and or organize music files) use Ubuntu only?  If so, how for each?

If you will forgive my ignorance here understand that I am looking for simplicity if simplicity is possible. A single OS with all systems functioning nominally would be outstanding.  I should have done this years ago, but Microsoft's abandonment of XP has forced the issue for me.

---

