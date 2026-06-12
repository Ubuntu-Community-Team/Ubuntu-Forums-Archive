---
title: "If I install Ubuntu on my system..."
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Kataangel on 2008-08-20
It says I have to partition my hard disk and there are some messages about formatting my hard disk drive.  Is there a safe way I can avoid this and if I partition my HDD, will I be able to reverse it?

Thanks!

---

### Post by aysiu on 2008-08-20
> **Kataangel said:**
> It says I have to partition my hard disk and there are some messages about formatting my hard disk drive.  Is there a safe way I can avoid this and if I partition my HDD, will I be able to reverse it?

Thanks!
Yes, the safe ways are to install Ubuntu as a virtual machine inside Windows or to install a dual-boot within Windows (otherwise known as Wubi):
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[http://wubi-installer.org/](http://wubi-installer.org/)

You can undo partitioning, but it is a process, and you should always back up *everything* before repartitioning.

---

### Post by perlluver on 2008-08-20
To install Ubuntu, unless you want to install it from Windows, through Wubi, then yes it has to format, the partitions you create.  You can also tell it to use free space, after the Windows install, unless you don't have Windows.  Not sure what your situation is, but that is the best explanation I can give.

---

### Post by sandysandy on 2008-08-20
there are various options during installation like guided, manual etc.

 ubuntu will require its own partition to dual boot, though with wubi u can install within windows. 

from Ubuntu 8.04 onwards u can install directly within windows.

see these links on dual boot

[http://apcmag.com/how_to_dual_boot_w...lled_first.htm](http://apcmag.com/how_to_dual_boot_w...lled_first.htm)

[http://www.howtoforge.com/dual_boot_..._ubuntu_feisty](http://www.howtoforge.com/dual_boot_..._ubuntu_feisty)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by Paqman on 2008-08-20
If you're nervous about partitioning then Wubi is definitely the way to go. Just boot into Windows, put your LiveCD in and select "install from within Windows".

---

### Post by Kataangel on 2008-08-20
Windows is corrupted on my system.  Is there a way to install Ubuntu without Windows and without reformatting my hard disk?

---

### Post by aysiu on 2008-08-20
> **Kataangel said:**
> Windows is corrupted on my system.  Is there a way to install Ubuntu without Windows and without reformatting my hard disk?
Yes, but there is a very slim possibility that resizing the corrupted Windows partition to make room for a new Ubuntu partition will corrupt the Windows partition even further.

---

### Post by markjensen on 2008-08-20
> **Kataangel said:**
> Windows is corrupted on my system.  Is there a way to install Ubuntu without Windows and without reformatting my hard disk?

If Windows is corrupted, I can assume that there is a good probability that your NTFS filesystem may also be damaged.  In that case, it would be risky to your data to try to create a wubi file.  Also risky to mess with (resize, etc) your partitions.

Boot Ubuntu as a LiveCD and see if you can poke around without making changes.

Alternatively, the Windows CD generally does a good job with its "repair" option.  I would give that a try, too.

---

### Post by nynoah on 2008-08-20
If you are trying to recover files from your windows system.  Use the live CD to mount your hard drive.  Copy the files you want to keep to an external hard drive.  Since your windows is corrupt my advice is to get back the files you want to keep that way and reload windows from scratch.  Once that is done put Ubuntu in there too, but do it the partition way.  This way if you screw up, oh well, you already have your files you need.  You already started with a messed up windows system, so you have to wipe it clean anyways.

---

### Post by SuperSonic4 on 2008-08-20
I'd try the windows repair CD/DVD first and see if that works. If it does (it did for me when my windows wouldn't boot).

Then use vista's partion editor ```
start -> right click on *computer* and select manage -> storage -> local disk
```(assuming vista, if not use gparted from the ubuntu live cd although you can use gparted with vista.) to shrink windows enough to get ubuntu on (min 5-10gb)

---

