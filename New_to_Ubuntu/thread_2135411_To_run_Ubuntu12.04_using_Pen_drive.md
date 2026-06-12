---
title: "To run Ubuntu12.04 using Pen drive"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by Aks1 on 2013-04-14
I need to know that does running the Ubuntu 12.04 from USB port[pen drive] provides the full support as after installing it.Or i have to install ubuntu first to get its full support? 
And one thing more i want to know that does after installing ubuntu on my HDD, it removes the full HDD of windows including files, softwares and documents because right now i dont have a win Os as its bootmgr gets compressed(win7 requires cd or bootable pd, which i dont have) so, im currently running the Ubuntu os on my pen drive rather installing it.Im currently able to open my win7 data in ubuntu using pen drive.
what should i do so that my previous win7 data can't removed or recoverable?

---

### Post by Toxic64 on 2013-04-14
Do you mean live from USB?
I don't see why it wouldn't be fully supported.

If you install on a hard drive and want to keep your windows system aside, you have to go for a dual boot setup in which you will be able to choose whether you want to boot windows OR Ubuntu. this way, you'll have both systems and files (you can choose that option during the installation).

If you want to be sure your datas won't be recoverable (not even by you) do a low level format of your hard drive with the appropriate software 

:!: if you do it wrong, this can kill your hard drive so just don't do it if you don't know how to.

---

### Post by cheatos on 2013-04-14
Using ubuntu from pen drive does limit application if you did not choose to use a persistent file system on your USB.
Then all changes will be deleted after you shut down the computer.
If you choose the persistent filesystem mode during the installation process of ubuntu to your USB drive changes will be saved.

---

### Post by C.S.Cameron on 2013-04-14
A Full install to pendrive is the same as an install to internal HDD, (USB2 is a little slower than SATA though).

A persistent install can not be upgraded and should not be updated due to the max 4GB size of the casper-rw file.

---

