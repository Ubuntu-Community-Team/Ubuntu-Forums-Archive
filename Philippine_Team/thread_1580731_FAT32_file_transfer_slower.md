---
title: "FAT32 file transfer slower"
date: 2010-09-23
forum: Philippine Team
---

### Post by nirvblakr on 2010-09-23
Gud day!  I just reformatted my USB flash drive to FAT32 from NTFS so I can transfer files from my Linux machine to a Macbook.  The problem I noticed is when I am transferring files in Linux to the flash drive, it seems that the rate is slower.  When I was using the FD in the NTFS format the file transfer is 20-22mbps but now with the FAT32 format it goes down from 10mbps or even less.  Is this normal?  Is there any format that I can use so I can transfer files from Linux to MAC?  TIA

---

### Post by angheloko on 2010-09-23
Yes, FAT32 will definitely be more slower than NTFS since FAT32 is relatively old. If you want, you can use NTFS. Mac can read NTFS but cannot write. There are programs for Mac that will allow you to write to NTFS disks (I'm not familiar with them though).

---

### Post by nirvblakr on 2010-09-24
Thanks sir for the response. :) Oh btw, how about EXT3 being used in Windows and MAC? Possible?

---

### Post by angheloko on 2010-09-25
> **nirvblakr said:**
> Thanks sir for the response. :) Oh btw, how about EXT3 being used in Windows and MAC? Possible?

Yeah, possible. 

For Windows, there are tons, try:

[LIST]
[*][http://www.paragon-software.com/de/downloads/free_downloads/home.html](http://www.paragon-software.com/de/downloads/free_downloads/home.html)
[*][http://web.archive.org/web/20080211120420/http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://web.archive.org/web/20080211120420/http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)
[*][http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)
[*][http://www.fs-driver.org/](http://www.fs-driver.org/)
[*][http://ext2read.sourceforge.net/](http://ext2read.sourceforge.net/)
[/LIST]
For Mac, you can try (haven't tested):

[LIST]
[*][http://sourceforge.net/projects/fuse-ext2/](http://sourceforge.net/projects/fuse-ext2/)
[/LIST]
You can partition your USB, say 5-10% (depending on the size of the FS driver of your choice), and format that 5-10% in FAT32, then format the remaining to NTFS. This way, kung meron kang ibang paggamitan na PC, you have the module/driver with you.

IMO though, just stick with FAT32. Then kung magka-copy ka just use rsync.

---

### Post by nirvblakr on 2010-10-07
> **angheloko said:**
> Yeah, possible. 

For Windows, there are tons, try:

[LIST]
[*][http://www.paragon-software.com/de/downloads/free_downloads/home.html](http://www.paragon-software.com/de/downloads/free_downloads/home.html)
[*][http://web.archive.org/web/20080211120420/http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://web.archive.org/web/20080211120420/http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)
[*][http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)
[*][http://www.fs-driver.org/](http://www.fs-driver.org/)
[*][http://ext2read.sourceforge.net/](http://ext2read.sourceforge.net/)
[/LIST]
For Mac, you can try (haven't tested):

[LIST]
[*][http://sourceforge.net/projects/fuse-ext2/](http://sourceforge.net/projects/fuse-ext2/)
[/LIST]
You can partition your USB, say 5-10% (depending on the size of the FS driver of your choice), and format that 5-10% in FAT32, then format the remaining to NTFS. This way, kung meron kang ibang paggamitan na PC, you have the module/driver with you.

IMO though, just stick with FAT32. Then kung magka-copy ka just use rsync.

OK. Thanks for the help!

---

