---
title: "Slow DVD-ROM copying"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by allokirk on 2008-05-09
I am having trouble when I copy a file from a dvd disc to the hard drive. The copy is extremely slow. Also, while copying, the computer basically freezes. I cannot move the mouse, continue listening to music, or open anything else.

I read other posts and they suggest enabling dma. I am not sure if this would fix the problem, or how I would go about doing this. I am using 8.04. Please let me know if you need any additional information. Thanks.

Here is the output from dmesg | grep -i dvd

```

[   24.362657] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-L532M, HR08, max MWDMA2
[   24.605500] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L532M HR08 PQ: 0 ANSI: 5

```

---

### Post by allokirk on 2008-05-11
This thread has solved the problem for me:

[http://ubuntuforums.org/showthread.php?p=4615284]("http://ubuntuforums.org/showthread.php?p=4615284")

---

