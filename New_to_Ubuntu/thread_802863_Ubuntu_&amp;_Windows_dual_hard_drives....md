---
title: "Ubuntu &amp; Windows dual hard drives..."
date: 2008-05-21
forum: New to Ubuntu
---

### Post by BEND IT 7 on 2008-05-21
I have installed Ubuntu using Wubi in Windows Vista Home Premium. I really like the new OS (new for me!), and I am glad that I was able to so smoothly install it as an application.  My laptop also has two hard drives (C and D), so I installed Ubuntu to the D drive.  My problem is that I can access all of the Windows files in Ubuntu but zero Ubuntu files in Windows.  That is a problem in as much as I am in the process of setting up Ubuntu and file transferring and I would like to know where my files in Ubuntu are on my computer...I can not even really find a HD location for my documents, pictures, etc. in Ubuntu itself (the files saved in Ubuntu Documents, Pictures, and so forth).

Any advice would be appreciated.  Thank you.

---

### Post by diaa on 2008-05-21
To access Ubuntu drives(which use the ext3 filesystem) from Windows, you need to make windows able to read ext3 filesystems, this is possible by installing the [open-source Ext2 IFS driver]("http://www.fs-driver.org/"), I'm already using it and it allows reading and writing files to ext2/ext3 filesystems, it's great.

---

### Post by wolfen69 on 2008-05-21
i believe you want [THIS]("http://www.fs-driver.org/") it says it's for ext2, but will work for ext3 also.

---

### Post by BEND IT 7 on 2008-05-21
I will try what you both recommended and then see how it works...
thank you for the timely responses.

:)

---

