---
title: "How to open some filetype directly?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by yangli on 2008-05-08
Every time I open a PS/EPS/TEX/HTML (and some other filetype) file, I get this message
[IMG]http://img.villagephotos.com/p/2007-7/1268314/ubuntu1.jpg[/IMG]

I already right-click the file -> Properties -> Open with -> and choose the "Document Viewer". But it didn't work. 

[IMG]http://img.villagephotos.com/p/2007-7/1268314/2.jpg[/IMG]

I don't want this "Do you want to run or display its contents" window to pop up every time. I need help! Thanks.

---

### Post by PeterJS on 2008-05-08
In the file's permissions tab remove the execute permission from the file. If the file is stored on a non-permission aware parition (FAT or NTFS) remount that parition using an fmask that doesn't include execute permission.

---

### Post by yangli on 2008-05-08
I will give a try. Now need to google "fmask". Thanks.

> **PeterJS said:**
> In the file's permissions tab remove the execute permission from the file. If the file is stored on a non-permission aware parition (FAT or NTFS) remount that parition using an fmask that doesn't include execute permission.

---

