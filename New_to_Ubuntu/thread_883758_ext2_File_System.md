---
title: "ext2 File System"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-08-08
I just formatted my new external hard drives to ext2. Is it normal for freshly formatted drives (With nothing on them) to have this much space not available?...I know that formatting does use up some space but this seems excessive:

250GB drive has 11.7GB Used
1TB=1000GB drive has more than 40 used!

Is this normal?

---

### Post by dje on 2008-08-08
my 250gb external formatted as ext3 has only about 238gb available, so yes :)

dje

---

### Post by LowSky on 2008-08-08
that seems about right a 250GB drive will loose abot 10GB when wiewed by any Operatiing System because of how they value the memory size, read this
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by JohnGalt131 on 2008-08-08
That's what mine was with fat (Before I formatted). but now it reports 219.3 GB Free. I'll try ext3 instead.

---

### Post by LowSky on 2008-08-08
Formatting a drive uses about a few kb, nothing crazy. this issue how the companies mis represent the hard drive size by using a 1000Mb=1GB when Operating Systems use 1024=1GB

Thoise extra 24MB add up

---

### Post by JohnGalt131 on 2008-08-08
It's weird.  It should say size=250, available=238. But it says size=238, available=219. It's like it's done the reduction twice. besides 250*(1000/1024)=244 not 219. So it isn't just the difference in units.

---

### Post by LowSky on 2008-08-08
what program are you using to format?
why not try doing it from the command line
[http://www.ehow.com/how_1000631_hard-drive-linux.html](http://www.ehow.com/how_1000631_hard-drive-linux.html)

---

### Post by JohnGalt131 on 2008-08-08
I used Gparted. I reformatted it in Virtual box using Acronis Disk Director and it said size=232, available 229. So, It's a little better.

---

### Post by JohnGalt131 on 2008-08-08
Might the problem be that I have "Round to cylinders" checked? Should that be off?

---

### Post by HermanAB on 2008-08-08
DON'T use Ext2.  It is not robust and WILL cause you to lose data sooner rather than later.  Rather use Ext3, JFS or XFS for some peace of mind.

---

### Post by articpenguin on 2008-08-08
normally a filesystem should only take at least 50-150MB of space at creation but ext2/ext3 has digusting code. At MKFS time ext2/3 will create inodes which you will probably only use 10% of them all. On my 500GB partition i lost 8GB thanks to the unused inodes that i will never use. Ext3 also has a HUGE journal. Its 128MB and that is large. 

JFS reiserfs XFS all use less space at mkfs time and have smaller journals.

---

### Post by LowSky on 2008-08-08
ZFS is one of my new favorite filesystems.
If only Sun would release it for Linux use.

---

