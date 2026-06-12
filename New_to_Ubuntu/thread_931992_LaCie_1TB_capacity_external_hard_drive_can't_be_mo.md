---
title: "LaCie 1TB capacity external hard drive can't be mounted..."
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Qtips on 2008-09-27
Hi everyone,

I just bought a brand new LaCie 1TB extern hard drive for my laptop under Ubuntu. But when i turn it on, Ubuntu say that he can't mount it. I copy here the error code: 

[HTML]Cannot mount volume.
Unable to mount the volume 'LaCie'.
Details
$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1/': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shut down Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sdb1/media/LaCie -o force. Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1/media/LaCie ntfs -3g force 0 0.[/HTML]

Now, i don't have Windows installed, so i guess i need to go with the second choice...but i'm a newbie in Ubuntu and the term "your own responsability" give me a cold...

Anyone have this problem ?

Thanks !

---

### Post by unutbu on 2008-09-27
Do you have any data on the LaCie?

The "your responsibility" message is warning that using the command may cause you to lose data, but it will not cause physical harm to the drive.

---

### Post by Qtips on 2008-09-27
Hi,

I don't have any data, it's a brand new, just-plugged in...so i need to do the second choice ?

---

### Post by unutbu on 2008-09-27
Yes, you should be able to run
```

sudo mkdir /media/LaCie
sudo mount -t ntfs-3g /dev/sdb1 /media/LaCie -o force
```
safely.

If this gives you trouble for some reason, you could also use GParted (System>Administration>Partition Editor) to delete the partition and create a new one. Select the filesystem type, and format it.

---

### Post by Qtips on 2008-09-28
Ok, thanks, i managed to mount my LaCie external hard disk, but i have another problem yet...i can't create any folder in it via Nautilus...of course, i can create a folder with the command line interface, but i prefer with Nautilus ;), so how i can change the permission of the mounted hard drive so i can do whatever i want ?

Thanks !

---

### Post by unutbu on 2008-09-28
Do you hot-swap this drive, or is it plugged in at boot time and always connected?

If you hot-swap the drive, right-click on the drive's icon on your desktop. Select Properties (it should be the last item I). Click on the "Drive" tab. Click on the "Settings" triangle. Add to the "Mount Options:" defaults,user,uid=1000,dmask=027,fmask=137

If you have it plugged in a boot time, then please post the output of 
```

blkid
cat /etc/fstab
```

---

### Post by Excalibre on 2008-09-29
In case you're still reading this thread, if you're not planning to use this drive with Windows at all, I'd suggest you not leave it formatted NTFS. The problem is that Linux support for NTFS is pretty good normally, but if something goes wrong (like, say, it loses power while you're writing to it) you're going to get scary error messages like this and there aren't really tools available on Linux for fixing NTFS file systems that have errors on them. Whereas if something goes wrong on an EXT3 file system, you have utilities to fix it. Plus, EXT3 is generally a lot more robust than NTFS.

---

### Post by 4viking4 on 2010-11-12
Hi,

How do I undo these actions? It didn't work, and I was able to format my drive in gparted, however now 46.6 GB shows as used, i'm assuming from the media/lacie folder that those commands created.

Please help :)

---

### Post by 4viking4 on 2010-11-12
Just to be clear, I'm referring to this post. I now have 2 lacie folders under media and i obviously only want one. How do i undo the one created by the commands below?

Thanks!

> **unutbu said:**
> Yes, you should be able to run
```

sudo mkdir /media/LaCie
sudo mount -t ntfs-3g /dev/sdb1 /media/LaCie -o force
```
safely.

If this gives you trouble for some reason, you could also use GParted (System>Administration>Partition Editor) to delete the partition and create a new one. Select the filesystem type, and format it.

---

