---
title: "how to format a cd-rw as fat32"
date: 2013-09-08
forum: New to Ubuntu
---

### Post by sam_baker2 on 2013-09-08
How do you format a rw-cd as fat32?
I don't see any application that will do it.
I need this to move files back and forth to an old Windows 98 box that 
will not let the USB card work.
I am using xubuntu 12.04 LTS

Thanks

---

### Post by sudodus on 2013-09-08
If nothing else works, you can take out the internal drive from the old Windows 98 box, and connect it to another computer (internally or with a USB to IDE & SATA adapter). Or floppy, if you have a second floppy drive (and the files are small enough).

Edit: Sorry, the obvious solution might the wired network! I guess the old computer has an ethernet connection.

---

### Post by sam_baker2 on 2013-09-08
I have thought about taking the HD out of the Win98 box and doing that ( I have a couple of external IDE/SATA enclosures ) but I did not
want to go to the trouble of taking the HD out. ( Only have a couple of files every now and then to move, I don't have a floppy on xubuntu box )

I think the Win98 box ( cica 2005 ) has an ethernet connector and I do have a 15 foot ethernet cable that is on the xubuntu box, that might work,
but I did not want to go to the trouble of pulling the ethernet cable off and on for just 1-2 files.

I think cd's are going the way of the dodo bird anyway.

---

### Post by whitesmith on 2013-09-08
Hold the phone! You can't format a CD as FAT or FAT32. CDs use a special file system that *nix calls CDFS. The TOSR (Toy Operating System from Redmond) implements a version of that FS with a device driver called mscdex. You'll need to get that kluge in your config.sys before a TOSR PC can read/write a CD. Don't forget to reboot after installing. You should read the Wikipedia article "ISO 9660."

---

### Post by sudodus on 2013-09-08
The easiest solution might be a dedicated ethernet cable, otherwise I suggest '[COLOR=#000000]pulling the ethernet cable off and on[/COLOR]'.

Is the computer really from circa 2005? Win98 is from 1998. I guess you want that system, because you have some software, that needs Win98 (like my son who has some old children's CDs).

---

### Post by carlwsnyder on 2013-09-08
Unless you are using legacy hardware, you are better off running Win98/Win98SE from a virtual machine to run legacy software, then disable the network interface in the virtual machine to keep it from ever connecting to the Internet.

---

### Post by sam_baker2 on 2013-09-09
I was able to finally get the CD-RW formated using my laptop with Win7 on it. Xubuntu can read/write to this cd,
and the Win98 box can read/write it.

I noticed that on the desktop of Xubuntu, the CD is noted as "UDF Volume", don't know what that means.

> "Is the computer really from circa 2005? Win98 is from 1998" 
The box was bought in 2005, I installed Win98 on it.
I have 4 file storage boxes for 3-1/2" floppys that are full of old files, utilities, programs I wrote, etc. that I use.
I have dosbox on Xubutu that runs alot of them, just need a way of getting them over to Xubuntu.
The Win98 box has a 3-1/2" floppy and a CD RW player, the Xubuntu box only has a CD RW player.

---

### Post by sudodus on 2013-09-09
Congratulations :KS

I'm reading and learning :-)

---

### Post by philinux on 2013-09-09
> **sam_baker2 said:**
> I was able to finally get the CD-RW formated using my laptop with Win7 on it. Xubuntu can read/write to this cd,
and the Win98 box can read/write it.

I noticed that on the desktop of Xubuntu, the CD is noted as "UDF Volume", don't know what that means.


Yes packet writing i've used in the past. The cd rw is basically seen like a usb stick with UDF formatting.

[http://en.wikipedia.org/wiki/Universal_Disk_Format](http://en.wikipedia.org/wiki/Universal_Disk_Format)

---

### Post by sudodus on 2013-09-09
> **philinux said:**
> Yes packet writing i've used in the past. The cd rw is basically seen like a usb stick with UDF formatting.

[http://en.wikipedia.org/wiki/Universal_Disk_Format](http://en.wikipedia.org/wiki/Universal_Disk_Format)

Do you think it would be possible to make a persistent live CD or DVD this way? I ask if *possible*, not efficient or long-life ;-)

---

### Post by philinux on 2013-09-09
> **sudodus said:**
> Do you think it would be possible to make a persistent live CD or DVD this way? I ask if *possible*, not efficient or long-life ;-)

Thinking about it I don't think UDF formatted cd rw's are bootable. 

[edit] Seems it could be done. [http://forum.imgburn.com/index.php?showtopic=5755](http://forum.imgburn.com/index.php?showtopic=5755)

---

### Post by sudodus on 2013-09-09
> **philinux said:**
> Thinking about it I don't think UDF formatted cd rw's are bootable. 

[edit] Seems it could be done. [http://forum.imgburn.com/index.php?showtopic=5755](http://forum.imgburn.com/index.php?showtopic=5755)

Interesting as an alternative to boot old computers :-)

Thank you

---

