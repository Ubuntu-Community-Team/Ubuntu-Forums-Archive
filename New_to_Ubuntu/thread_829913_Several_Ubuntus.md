---
title: "Several Ubuntus"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by RokyFromGoky on 2008-06-15
When I started with Ubuntu, is installed it a couple of times, because it wasn't working as I wanted. As I understand it, all these installations are still present on my machine. How can I remove them and will I lose any data? 

I expect this question to be  already asked, but i couldn't find it.

---

### Post by drs305 on 2008-06-15
Just because you installed it more than once does not mean there are multiple copies on your machine. Did you allow the setup to automatically partition the drive? It more than likely overwrote your earlier attempt unless you took specific actions to install it to a different partition. You can check System, Administration, Users and Groups to see if there is more than one user listed on the machine. You can also run the following command to see what kind of partitions you have on your disk:
```
sudo fdisk -l
```
If you see only 1 "Linux swap" it is *probably* only installed once.

You may see several different versions of the kernel on the startup (boot) menu. This is normal - each time a new kernel is introduced it is added to the boot menu. Seeing multiple kernels is not the same as having multiple installations of the system. What you see is controlled by the /boot/grub/menu.lst file.

The easiest way to modify what you see on boot is to use StartUp-Manager (System, Admin, StartUp-Manager). For more information on this, refer to:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by rraj.be on 2008-06-15
> **RokyFromGoky said:**
> When I started with Ubuntu, is installed it a couple of times, 

Be clear in what partition's you have installed ubuntu's.


> 
 How can I remove them and will I lose any data? 




The best solution is to back up data's in some other good partition and then formate that partition.

---

### Post by RokyFromGoky on 2008-06-15
I've got an 7.10 on sda1 and one on sda3. There are also 3 different 8.04's, but they don't show a location.

---

### Post by rraj.be on 2008-06-15
Just as i said just copy the complete data files tthat you need and Formate it with gparted.

Go here for more info on gparted.

```
[http://howtoforge.com/partitioning_with_gparted]("http://howtoforge.com/partitioning_with_gparted")
```

```
[http://http://www.psychocats.net/ubuntu/separatehome]("http://http://www.psychocats.net/ubuntu/separatehome")
```

---

### Post by drs305 on 2008-06-15
> **RokyFromGoky said:**
> I've got an 7.10 on sda1 and one on sda3. There are also 3 different 8.04's, but they don't show a location.

When you say you have 3 different 8.04's, are you saying that when you boot you see something like this:
```

Ubuntu 8.04, kernel 2.6.24-18-generic
Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-17-generic
Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)

```

Please run this command and tell us which version runs by default:
```
uname -a
```

If you post your fdisk and fstab results, along with the results from uname, we can confirm which system you are using and suggest how to get rid of the remaining one(s).
```
sudo fdisk -l
cat/etc/fstab
```

---

### Post by RokyFromGoky on 2008-06-15
W> hen you say you have 3 different 8.04's, are you saying that when you boot you see something like this:
Code:

Ubuntu 8.04, kernel 2.6.24-18-generic
Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-17-generic
Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)


That is exactly what I see.


THis is the version i use:
```
2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux
```


And this are all my devices. I'm not sure if i understand it, but it looks like a lot to me.
```
Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd68fd68f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7562    60741733+  83  Linux
/dev/sda2           14493       15017     4217062+   5  Extended
/dev/sda3            7563       11162    28917000   83  Linux
/dev/sda4   *       11163       14492    26748225   83  Linux
/dev/sda5           14831       15017     1502046   82  Linux swap / Solaris
/dev/sda6           14643       14830     1510047   82  Linux swap / Solaris
/dev/sda7           14493       14642     1204812   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by drs305 on 2008-06-15
Ok, the 3 8.04's you are seeing are just the 3 available kernels available for you to use (kernels 16,17, and 18 ). You have only 1 installation of 8.04. You are using kernel 18, which is the latest available in the normal repositories. It is generally best to keep the current kernel and at least one backup should you have problems. You can remove kernel 16 by various methods I described in the link to the HOWTO Kernel link in my first post. If you want to know what a kernel is, this link explains it: [kernel]("http://en.wikipedia.org/wiki/Kernel_%28computer_science%29") Think of it as ubuntu being the car and the kernel being the engine.

You do have 3 different swap partitions. You really only need one of them. We do need to look at your fstab file to see which one is actually being used, so please run this and let us take a look. 

And confirm that you want to get rid of 7.10 and just run 8.04?

```
cat /etc/fstab
```

---

### Post by pmlxuser on 2008-06-15
what happens if you select an entry than the default one, if you are able to boot from any entry you choose then possibly remove some of the entrys fron /boot/grub/menu.lst
do 
$sudo cp /boot/grub/menu.lst menu.lst.bck (backing up incase) then
$sudo gedit /boot/grub/menu.lst
delete some of the entrys possiblu you could do with

Ubuntu 8.04, kernel 2.6.24-18-generic
Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
(the reason being these were the last keneral installed to your system and possibly work perfect if your answere to my first question is that all work ok)

Anyway which partition do you mount as /

---

### Post by lswest on 2008-06-15
To see which partition you use as root either post the output of ```
cat /etc/fstab
``` or ```
df -h
``` (I'd say the fstab one will be more useful).  once you know which is your root partition, just back up the files you need to keep (copy them to your root partition/home folder) and then delete them using GParted, then to add that space to your root partition boot to the Ubuntu LiveCD and use GParted from there (you can't resize a partition that's in use).

About the extra kernels: I recommend the newest one and then the one prior to it (so -18 and -17) just in case something goes wrong in an update.

---

