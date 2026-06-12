---
title: "Accessing Windows ?"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by n5050 on 2011-11-19
I want to customize my ubuntu so that there is no access to my harddisk drive. Is there a way to do it. I know on some other linux systems there is a nohd boot option. I am using ubuntu from livecd and the access to my windows partitions is really something I do not need and therefore it makes sense to customize ubuntu without it, as I am always accessing them accidently while using the file explorer. Any ideas?

---

### Post by CharlesA on 2011-11-19
If you boot from a livecd, the hard drive isn't mounted automatically.

If you don't want to access the hard drive, disconnect it or turn it off in the BIOS.

---

### Post by WasMeHere on 2011-11-19
Hi n5050,

You can mount the partitions of your hard drive read only, but it is not anything people would do running a live system. If you intend to use it for a longer period and make it persistent, then you might think of mounting the hard drive read only. But at that stage you might be prepared to install Ubuntu instead, maybe as a dual boot system with Windows and Ubuntu.

If you do not want Ubuntu to touch the hard drives at all, you could switch them off electrically (no connection).

But in the standard set-up, the partitions found are not mounted. They will only be mounted if you click on their icons. If you notice that the icon in the left panel has an ***eject symbol*** (in the file browser), it is mounted. Then you can unmount it by clicking on that eject symbol.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by roger_1960 on 2011-11-19
Hi

You could unmount the windows partitions.  In the "file manager", nautilus, select View>sidebar>places then right click on the windows filesystem which should appear at the top left, and click "unmount".  This should diable access to it until mounted again (by selecting it)  If you normally use nautilus with the "tree" menu, you are unlikely to select it by accident.

---

### Post by Mark Phelps on 2011-11-19
You're going to have a hard time customizing Ubuntu if you intend to keep using it from a LiveCD.  Also, the performance when running from CD is really poor due to frequent CD reads.

---

### Post by WasMeHere on 2011-11-19
> **n5050 said:**
> ...I am using ubuntu from livecd ...
I saw that you are using a live system, but did not notice it is from a CD. I was thinking of USB when replying. You can run a live USB drive in persistent mode (because the USB is writable) but the CD is read-only and hence not possible to customize unless you want something very advanced.

Persistent mode means that you can write changes to your system and store personal files on a read/write file system on the USB drive.

---

### Post by n5050 on 2011-11-19
Have tried all these suggestions but they are not helping me.
My laptop Dell n5050 doesn't have a harddrive option in bios.

Physically removing the harddrive is not possible with this model.

As to the idea of simply not to mount these partitions, 
if I go over them with the cursor they mount anyway.

Is there no blacklisting rule which could be added to the bootup
process?

---

### Post by WasMeHere on 2011-11-19
I don't know your laptop, but my laptops have a special opening for the hard drive, so it is not necessary to unmount everything.

Let us hope someone reading this knows a way to disconnect or blacklist the hard drive. If not, please consider getting a second-hand computer and dedicate it to learning Ubuntu! That way you will have peace of mind until you can rely it, and run it on a computer with valuable personal files.

---

