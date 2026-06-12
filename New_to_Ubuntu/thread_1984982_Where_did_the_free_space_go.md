---
title: "Where did the free space go?"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by EB0V on 2012-05-22
When I upgrade from 11.10 to 12.04 do old system files get deleted or not?

I have a small partition for Ubuntu (20G) and when I upgraded to 12.04 it started telling me that I only have less than 1G of free space left, knowing that I only have few apps installed on Ubuntu (office, Gimp, Picasa and light stuff...)

What could be the problem?

Thanks!

---

### Post by Revolutionary101 on 2012-05-22
I would suggest running "Disk Usage Analyzer" and scan your file system. If the occupied space is mostly in non-/home/user folders then it is probably programs and you should run this in terminal:

```
sudo apt-get autoclean && sudo apt-get autoremove
```

That should clean an install files that were not removed automatically plus any programs that haven't been used.

If the space being taken up is in your home directory then it is probably your own files. I would suggest going through things and see what you need to keep. I hope it helps!

---

### Post by grahammechanical on 2012-05-22
An upgrade will remove certain system libraries that are being upgraded but the change from 11.10 to 12.04 is very great. In 11.10 there are certain libraries (i386) that make it easier for 32bit programs to run on 64bit Ubuntu. In 12.04 all those libraries have been replaced with libraries called multiarch that will be used in for this purpose in Ubuntu running on different CPU architectures.

I think the OS has got larger in the change over to 12.04. So, how much space is being taken up with your home folder?

20GB should be fine for the OS if you have your home folder on a separate partition. I am running an 11.10 upgraded to 12.04 and I do not have this issue. I do have a separate home partition.

Regards.

---

### Post by EB0V on 2012-05-23
I also have a separate partition but when I checked Disk Utility it showed me that I have 4 SWAP partitions of 2.1GB each. How is that even possible? I remember creating only one last year when I installed 11.04! 

**Screenshot:**
[IMG]http://s15.postimage.org/5r4a4ak6j/Selection_016.png[/IMG]

---

### Post by Revolutionary101 on 2012-05-23
I would suggest installing and then opening Gparted to see which of those swap partitions you can get rid of. Then you can resize your Ubuntu partition to take up the free space by booting from a liveCD or USB.

Although I would go through the resize process with caution because you will have to reconfigure GRUB to accommodate for the enlarged Ubuntu partition.

---

