---
title: "[SOLVED] how do you dual boot hardy and intrepid?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Zieg30CT on 2008-10-30
I plan to install the new Intrepid release in a few minutes, however I don't want to give up KDE 3.5 so I'd like to dual boot with my older Kubuntu install. I know the basics of dual booting and such when it comes to dual booting Linux and Windows, but how exactly do I do it with two Linux distros? I know a mount point is needed but since Kubuntu is already mounted on / what exactly should I choose for the mount point?

---

### Post by JECHO on 2008-10-30
i believe its the same with 2 linux distros as it is with linux and windows... i would say if mounting both at / doesnt work then try mounting the new os in /home or something.

---

### Post by jbrown96 on 2008-10-30
The installation will take care of adding hardy to your grub menu. When partitioning, don't delete your hardy partition. Most likely resize it, but you should post your partition configuration. Post the output of these two commands, and I can help you partition. ```
cat /etc/fstab
``` ```
sudo fdisk -l
```

---

### Post by Zieg30CT on 2008-10-30
this is the output of the first command:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d7cae86a-74e4-4971-924f-1f812f3a14bd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=1257d29f-f605-4330-9c04-a3df75a26642 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


this is the output of the second command:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2363eab2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97659103+   7  HPFS/NTFS
/dev/sda2           12159       12340     1461915   82  Linux swap / Solaris
/dev/sda3           12341       24321    96237382+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ef3c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb3             192       10199    80389260    7  HPFS/NTFS


I'm not too worried about resizing my hardy partition as I still have over 90GB left that I've yet to partition (this is what I planned to let Intrepid use). As for my bootloader I thought I should mention that I'm relying on Windows Vista/Longhorn loader and modifying it via EasyBCD.

---

### Post by jbrown96 on 2008-10-30
Just partition the 90GB for Intrepid, and then choose not to install the Grub bootloader (I would imagine you did this for Hardy as well). I have never messed with Windows' bootloader, so I can't help you there. I would imagine it would be the exact same as adding hardy to it.

---

### Post by bodhi.zazen on 2008-10-30
See this thread for a few tips :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by Zieg30CT on 2008-10-30
What about the mount point? The last time I tried a dual boot (I guess I should say triple boot but I don't really use Windows unless its for games) between two Linux distros (Mandriva and Kubuntu) every mount point I chose just refused to work when I attempted to install Mandriva after Kubuntu. I'm kind of concerned as I'd like to keep that from happening with the Intrepid install.

---

### Post by OrangeCrate on 2008-10-30
I have 8.04 and 8.10 on separate partitions. Use a Live CD of the version you are installing, and it'll partition it automatically (it'll recognize the other OS, and will split the hard drive in half). Just don't choose the option to use the whole hard drive for the new OS.

Edit:

Then, if you'd like, you can use Startup Manager (startupmanager) from Synaptic, to manage which kernel boots first. (Install it on the **last** OS you installed.)

---

### Post by OrangeCrate on 2008-10-30
<deleted duplicate post>

---

### Post by jbrown96 on 2008-10-30
> **Zieg30CT said:**
> What about the mount point? The last time I tried a dual boot (I guess I should say triple boot but I don't really use Windows unless its for games) between two Linux distros (Mandriva and Kubuntu) every mount point I chose just refused to work when I attempted to install Mandriva after Kubuntu. I'm kind of concerned as I'd like to keep that from happening with the Intrepid install.
Not quite sure what you mean, but I think you are getting confused about how you want the two distros mounted. You don't need to specify a mount point for the hardy partition (when you are installing Intrepid); you can if you want to be able to share files (although, mounting within Gnome is usually easier), choose the mount point for the hardy partition as /media/hardy or some other name within /media. Only the new Intrepid partition needs to (and can have) a mount point of / . Hope this helps

---

### Post by Zieg30CT on 2008-10-30
that helps. I'll post back if I still have trouble.

edit:

no trouble with the install, thanks for the help :popcorn:

---

