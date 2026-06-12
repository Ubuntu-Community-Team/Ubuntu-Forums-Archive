---
title: "problems setting up execute permision to a file"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by puigar on 2012-07-09
Hi,

I have installed Ubuntu 11.10 recently to my  computer in order to use fortran 90.
I have installed succesfully gfortran compiler but it seems that I cannot execute the output that comes out from the compilation. it is a "**a.out**" file and  the matter is that I amb not capable to change the permision of the executable. I cannot do it with the graphic interface and neither with command line. 

when I do it with "chmod +x a.out", I just type enter and it reads the command correctly. but when I look  with ll -l it does not appear the "x" on the rights of the file...

Why is this happening??

Thanks in advanced

Albert

---

### Post by NikTh on 2012-07-09
Maybe you must change the owner . I am not sure but try it.. \
```
chown yourusername:yourusername a.out
```
Its possible to not let you , if not then run with sudo . 

Then you can try to change again the execution rights with chmod.

---

### Post by SeijiSensei on 2012-07-09
You need to use sudo if you're not the owner of the a.out file:

```
sudo chmod a+x /path/to/a.out
```

---

### Post by spjackson on 2012-07-09
> **puigar said:**
> 
when I do it with "chmod +x a.out", I just type enter and it reads the command correctly. but when I look  with ll -l it does not appear the "x" on the rights of the file...

Why is this happening??

Is a.out located on a non-linux filesystem, e.g. a FAT32 USB flash drive? If so,  try building on a linux partition instead.

---

### Post by puigar on 2012-07-11
it is located in a ntfs partition... and actually this was the problem.


So it is not possible in any way to execute any file in a ntfs partition????

I try to put the executable permission on the linux partition, but the executable right disapears when it is copied in the ntfs partition.

---

### Post by spjackson on 2012-07-11
> **puigar said:**
> it is located in a ntfs partition... and actually this was the problem.


So it is not possible in any way to execute any file in a ntfs partition????

I try to put the executable permission on the linux partition, but the executable right disapears when it is copied in the ntfs partition.
It is possible, but it is not straight-forward. There are options to specify when the partition is mounted. If you search the forums for ntfs and execute, you will find lots of answers.

I have never found the need to do this, so I am sketchy about the details.

---

### Post by puigar on 2012-07-11
thanks, I have managed to set up executable files for the device at the fstab file. even I do not what I have really done it worked eventually. 

Thanks!

---

