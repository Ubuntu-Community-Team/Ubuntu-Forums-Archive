---
title: "Removing Ubuntu - help!!"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Edd257 on 2008-08-06
Hi,
I'm giving my computer to my brother and need to remove Ubuntu so there's only Vista.

In Windows I removed the 30GB partition I created for Ubuntu, it worked.. so I turned off my computer to see if GRUB loader was still there, 

All I can get is this when trying to boot Windows is this:

''GRUB loading

GRUB loading, please wait...
Error 17''.

I'm running Ubuntu from a live CD to post this, my question is how can I remove GRUB loader?

Any help appriciated!
Thanks

---

### Post by Alpha_Cluster on 2008-08-06
Grub ran off the partition that ubuntu was installed on that is why your getting the error. What you need to do is reinstall the windows vista bootloader. I dont know if there is any way to do this other then by trying to recover windows Vista and crossing your fingers and hopping it works in finding the partition and adding it to the boot loader.

---

### Post by Hyper Tails on 2008-08-06
Try deleting the partition that you installed ubuntu on in vista

start>right click computer>manage>continue>Disk management> right click the ubuntu partition>delete volume

try it..
hope this helps you. 
:) :) :)

---

### Post by Edd257 on 2008-08-06
> **Hyper Tails said:**
> Try deleting the partition that you installed ubuntu on in vista

start>right click computer>manage>continue>Disk management> right click the ubuntu partition>delete volume

try it..
hope this helps you. 
:) :) :)

Hi,
I can't access Windows, when I turn my computer on I just get the error from GRUB.. :(

I would reinstall windows and remove all the partitions but there is some stuff I need to copy from my computer..

---

### Post by arpanaut on 2008-08-06
Take a shot with this: [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Tried it recently on a test machine and it worked just fine. 
Make sure you are pointing the program to the correct partition.

---

### Post by kansasnoob on 2008-08-06
You'll need to restore Vista's mbr. If you have no disc you can get one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You want to "fix boot" and "fix mbr"!

---

### Post by Ptero-4 on 2008-08-06
Install ms-sys on the liveCD (yes you can do that, there´s no password for the liveCD user) and type
```
ms-sys -m /dev/sda
```
Note that I read it on a tutorial but haven´t tried myself. You should consult the man page for that command before running it. And you run it on the root of the drive containing your bootloader (usually sda, but might be sdb, look on fdisk, the correct drive is the one with the windoze partition).

---

