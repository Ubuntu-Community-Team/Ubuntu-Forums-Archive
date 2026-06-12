---
title: "Dell Inspiron 1525 dual boot installation"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by jjfourtwenty on 2008-06-12
Hi,

I'm trying to install Ubuntu on a Dell Inspiron 1525 alongside an existing Windows XP installation.

Everything runs find up to the disk partition stage whereby I am given an undefined error. Running the supergrub live cd tells me to run chkdsk in windows, reboot twice, then try again. Unfortunatley this has failed to work.

I have successfully installed Ubuntu on this machine previously when deleting the XP Partition of the disc. The probelm seems to be when the NTFS partition is re-sized to make way for ubuntu.

I hope this is a clear enough description.

Thanks in advance!

---

### Post by UltraMathMan on 2008-06-24
I remember reading that if you don't defrag before attempting to install next to XP, you can run into these sorts of issues, where the partitioner can't resize the XP partition since files are scattered all over the disk - this may be the cause of the problems you're running into.

Unfortunately the defrag included with XP can't move certain files, ie. ones in use by the system. You'll need to use some third-party app to defrag - a google search yielded [http://searchwincomputing.techtarget.com/tip/0,289483,sid68_gci1266344,00.html]("http://searchwincomputing.techtarget.com/tip/0,289483,sid68_gci1266344,00.html"). Try running this sort of defrag then installing again.

-Hope this helps :)

---

