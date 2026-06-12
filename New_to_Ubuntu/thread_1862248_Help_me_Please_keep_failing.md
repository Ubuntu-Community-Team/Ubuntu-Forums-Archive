---
title: "Help me Please keep failing"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by Nabz23 on 2011-10-16
OK so I already had ubuntu 10.04 on my 32 bit laptop but now i have a 64 bit i3, and i created a partition that made all my drives dynamic disks and changed them all to simple volume. Everytime I try to install ubuntu 11.10 from wubi an error occurs and just to clearify I also tried the cd method but something happened with that...

I also downloaded the desktop i386 11.10 version.

Please help me, thanks.

---

### Post by Old_Grey_Wolf on 2011-10-16
You need to be more specific about the error you are getting.

---

### Post by Nabz23 on 2011-10-16
Alright, I'll post up a pic soon

---

### Post by westie457 on 2011-10-16
Hello, be prepared for bad news.

Back up everything you want to keep because there are no guarantees that your information can be kept while you re-convert the dynamic disk back to basic. your best chance to do the change is using the professional version _[here]("http://www.partitionwizard.com/products.html")_. More guidance if you want it will come when you have posted a screenshot or ```
fdisk -l
``` output. The l in the command is a lowercase L not a 1 or an 'i'.

---

### Post by Nabz23 on 2011-10-16
The erorr is about to come then I will show you guys, also this is a new laptop I don't have anything that I need

---

### Post by Nabz23 on 2011-10-16
[[img]http://www.freeimagehosting.net/t/e3e04.jpg[/img]](http://www.freeimagehosting.net/e3e04)

This is the error, also I don't even know how to convert back to basic disk and also the problem was when I was creating a new partition at the final step it makes it convert to dynamic and it warns me if I cancel it then I woudln't be able to make a partition.

---

### Post by westie457 on 2011-10-16
Dynamic Disk is a Windows proprietry thing a bit like RAID. Windows can work with it however nothing else can and Windows will not install normally.

First thing make a copy of the Factory Restore partition and/or your current Windows to a USB stick or DVDs it will be needed if you wish to keep Windows, after all you have paid for it so why not keep it. Also make a Windows Recovery Disc for future issues.
When you have the back up completed boot into the LiveCD in try mode and start Gparted. Then in Gparted go to Device and Create Partition table. **This will wipe the hard drive of all information.** Make sure you are working on the correct drive.

After that operation create a two partitions. The first one about 10GB or the same size as what the original was. This is for the Factory Restore. Format this as NTFS.

Reboot using the Restore DVDs and restore Windows to Factory default settings. 


That will keep you busy for a while. Re-post for the next steps when Windows has been restored. Could you post a picture of the Windows partitions.

To get to the screen that shows them click the Start Button then Right-click 'My Computer' and select 'Manage'. In the Window that opens select Storage in the left pane.

Good luck.

---

### Post by Nabz23 on 2011-10-16
[[img]http://s2.postimage.org/1534wazms/error.jpg[/img]](http://postimage.org/image/1534wazms/)

This is the pic of the drives.
Man this seems like a serious obstacle

---

### Post by Megaptera on 2011-10-16
> **Nabz23 said:**
> [[img]http://www.freeimagehosting.net/t/e3e04.jpg[/img]](http://www.freeimagehosting.net/e3e04)

This is the error, also I don't even know how to convert back to basic disk and also the problem was when I was creating a new partition at the final step it makes it convert to dynamic and it warns me if I cancel it then I woudln't be able to make a partition.

That looks like a Wubi install, is that correct?

---

### Post by Nabz23 on 2011-10-16
> **Megaptera said:**
> That looks like a Wubi install, is that correct?

Yup its a wubi install

---

