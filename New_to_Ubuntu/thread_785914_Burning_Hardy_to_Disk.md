---
title: "Burning Hardy to Disk"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by spacefreak86 on 2008-05-07
I am trying to burn the Hardy Desktop .iso file to a disk, but it is saying that the file is too large to burn to the disk. Its off by about 30 MB. Is there a way to unpack and repack the file without losing content so that it can burn to a standard 700 MB disk?

---

### Post by Monicker on 2008-05-07
Odd. My iso file shows as being right at 700mb in size
```

ls -lh ../ubuntu-8.04-desktop-i386.iso

-rw-r--r-- 1 username username 700M Apr 24 13:55 ../ubuntu-8.04-desktop-i386.iso
```


I didn't have any warnings or errors when burning it.

---

### Post by gn2 on 2008-05-07
What OS and burning app are you using and what size is the .iso file you have?
It should be 699.1mb.

---

### Post by NightwishFan on 2008-05-07
Are you trying to burn a daily image? Because the hardy CD is like 680MB for me. Tell me which one you want (ubuntu kubuntu 32bit 64bit?) and I will link you to it. If you can torrent that would be excellent since it is more efficient than the direct download.

---

### Post by spacefreak86 on 2008-05-07
I've got the Kubuntu 32-bit edition. The download file was 697.5 MB, but it is showing up on Windows XP as 731.28 MB using the NTI CD & DVD-Maker program. 

I tried burning it earlier on the Hardy that I do have (I am going to reformat and try again, hope that I don't get as many errors as I do right now), but it kept popping out corrupt disks. I am using Memorex 52x 700MB CD-R disks.

---

### Post by gn2 on 2008-05-07
Use imgburn, it should get the job done: [http://www.imgburn.com/](http://www.imgburn.com/)

If you unpack or browse through the .iso in Windows it will be corrupted and you will require to download it again.

---

### Post by NightwishFan on 2008-05-07
I advise Infrarecoder as well.

---

### Post by Sealbhach on 2008-05-07
I got that message too. If you have Windows Vista you can burn it onto a DVD, that's what I did.


.

---

### Post by spacefreak86 on 2008-05-07
> **Sealbhach said:**
> I got that message too. If you have Windows Vista you can burn it onto a DVD, that's what I did.


.

Two problems: I don' have a DVD burner, and I refuse to put Vista on my computer. Which is why I went to Linux....

---

### Post by NightwishFan on 2008-05-07
> **spacefreak86 said:**
> Two problems: I don' have a DVD burner, and I refuse to put Vista on my computer. Which is why I went to Linux....

Thats the spirit! Try imgburn or infrarecorder, if in your file browser the .iso is less than 700mb than it should burn on a cd.

---

### Post by Sef on 2008-05-07
Here are two good links:

[How to Write (Burn) ISO files to CD]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm")

[ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm")  (an excellent iso burning tool)

---

### Post by NightwishFan on 2008-05-07
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by spacefreak86 on 2008-05-07
Okay, I got it, and a mostly-functional version of Hardy working now! Basically I had to double click on the file and have it automatically start in NTI, rather than opening the file inside of NTI..... don't ask, Windows is wierd.

---

