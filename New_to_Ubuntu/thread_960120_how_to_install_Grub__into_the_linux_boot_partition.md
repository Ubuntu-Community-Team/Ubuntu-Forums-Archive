---
title: "how to install Grub  into the linux boot partition ?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by victimoflinux on 2008-10-27
Hi ! I have also problem with grub, i did find instruction for installing grub from live CD on your site [http://ubuntuforums.org/showthread.php?t=224351&page=61](http://ubuntuforums.org/showthread.php?t=224351&page=61), the problem is that it writes itself to mbr, and i don't want to. I need the mbr clean from linux, i am using another progrm that wrights itself to mbr. Please explain step by step how to install Grub  into the linux boot partition
and not into the mbr, and please don't send me to google.I didn't find simple instruction so far.Thanks.

---

### Post by Nepherte on 2008-10-27
That guide you linked to, restores grub to the place you initially installed it on. If that was the mbr, it will be put in the mbr again.

I believe this should install it to the disk you want:
```
sudo grub
> root (hdx,y)
> setup (hdx)
> quit
```
Grub will be installed on to hdx (replace x with the number of the disk you want). hdx,y should be the place where you put linux on. hdx,y means disk x and partition y. Be very careful with hdx and hdx,y

---

### Post by louieb on 2008-10-27
Pretty  simple once you know how.
Start grub ```
sudo grub
```
find the grub program ```
find /boot/grub/stage2
```
tell grub where its files are ```
root (hd#,#)
```
install the grub ipl code to the boot sector of the partition ```
setup(hd#,#)
```
done ```
quit
```

---

### Post by victimoflinux on 2008-10-27
> **Nepherte said:**
> 
Grub will be installed on to hdx (replace x with the number of the disk you want). hdx,y should be the place where you put linux on. hdx,y means disk x and partition y. Be very careful with hdx and hdx,y
This is an another problem :) How can i know what i need to insert? 
:lol:

---

### Post by victimoflinux on 2008-10-27
> **louieb said:**
> ```
setup(hd#,#)
```
 
i need simple explanation how to know what i should insert instead #,# 
:popcorn:

---

### Post by bumanie on 2008-10-27
Post the output of > sudo fdisk -luThen someone can help with the correct numbers to insert in place of the x,x

---

### Post by caljohnsmith on 2008-10-27
Louieb's instructions will work, but he has a small typo in that it should be "setup (hd#,#)" with a space. Maybe this might make it a little clearer for you:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX,Y)
grub> quit
```
Please post the output of all the above commands so we can verify it worked OK.

---

### Post by victimoflinux on 2008-10-27
> **bumanie said:**
> Post the output of Then someone can help with the correct numbers to insert in place of the x,x

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef760361

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    49833629    24916783+   7  HPFS/NTFS
/dev/sda2        49833630   312576704   131371537+   5  Extended
/dev/sda5        49833696   112712602    31439453+   7  HPFS/NTFS
/dev/sda6       112728168   142930304    15101068+  83  Linux
/dev/sda7       142930368   145613159     1341396   82  Linux swap / Solaris
/dev/sda8       145613223   251095949    52741363+   7  HPFS/NTFS
/dev/sda9       251096018   281378474    15141228+  83  Linux
/dev/sda10      281378538   282808259      714861   82  Linux swap / Solaris
/dev/sda11      282808323   312576704    14884191   bc  Unknown
```
sda9 and sda10 i want to format, what is easy way to do it? 
 sda11- it is from acronis.

---

### Post by caljohnsmith on 2008-10-27
> **victimoflinux said:**
> 
sda9 and sda10 i want to format, what is easy way to do it? 
 sda11- it is from acronis.
I would boot up your Live CD and run:
```
gksudo gparted
```
And then you can format sda9 and sda10 if you want. And by the way, which other boot loader are you using in your MBR?

---

### Post by victimoflinux on 2008-10-27
> **caljohnsmith said:**
> I would boot up your Live CD and run:
```
gksudo gparted
```


And then you can format sda9 and sda10 if you want. And by the way, which other boot loader are you using in your MBR?
And i will should to insert somewhere sda9 and sda10  or it will just will read my mind ? :)
I am wonder, it is possible from linux to add those empty disks to my disk, for example to my sda5 ( it is  from windows, in ntfs )?
Can you  guide me?
About my loader, i am using acronis true image system restore, it using mbr - in order to  restore my disk, before any operational system will start up.

---

### Post by caljohnsmith on 2008-10-27
> **victimoflinux said:**
> And i will should to insert somewhere sda9 and sda10  or it will just will read my mind ? :)
I am wonder, it is possible from linux to add those empty disks to my disk, for example to my sda5 ( it is  from windows, in ntfs )?
Can you  guide me?
About my loader, i am using acronis true image system restore, it using mbr - in order to  restore my disk, before any operational system will start up.
"gparted" won't read your mind, but it is a nice GUI partition editor that is relatively easy to use. :) sda9 and sda10 both come right after sda8 as far as the physical layout of your HDD goes, so if you get rid of them, you could expand sda8 to use that space. If you want to give that space to some other partition like sda5, you'll have to shift things around a bit; you could move sda6, sda7 and sda8 towards the end of your drive (once you delete sda9 and sda10) so that sda5 will have room to expand.

I would highly recommend backing up any important data you have before doing any repartitioning. Also, when you run gparted, if any of the swap partitions show a "lock" icon, right-click them and select "swapoff". And also, keep in mind that gparted doesn't do anything to your HDD until you hit the "apply" button, so that is your only insurance against mistakes. So you can fiddle with your partition layout in gparted as much as you want until you hit the "apply" button, and that's when gparted goes to work. Let me know how it goes. :)

---

### Post by issih on 2008-10-27
Ok, time to be careful..grub uses a different naming scheme to the linux kernel for the hard disks. kernal uses sda,sdb,etc and grub hd0,etc.

Secondly I think that there is no absolute guarantee that the sda sdb bit always refers to the same disk in the kernel any more, that is why most files use the uuid instead.

Anyway, ignore that for now.

You have had the right advice, but also some confusing stuff too:

This is what you need to do, boot from an ubuntu live cd, then open a terminal and do the following:
 
```
sudo grub
grub> find /boot/grub/stage1
```
that command should return a response something like hdX,Y, telling you that ubuntu is installed on partition Y of disk X
You then need to install grub, you do that with the following commands:
```
grub> root (hdX,Y)
grub> setup (hdX,Y)
grub> quit
```

Using X and Y from the previous output. This will install grub into the exact partition of the ubuntu install rather than the mbr of the disk. If you want to install into the mbr of the disk you just use the X part in the final commmand and leave out the partition number, e.g.:

```
setup (hdX)
```

Hope that helps

P.S. as for deleting and resizing the partitions CalJohnSmith is giving you good advice, just use gparted from the livecd environment it can delete and resize partitions relatively well. Its worth defragging any ntfs volumes from within windows first though, oh and if you use vista, I believe its better to use vista's own tools to change the partition table, as vista stupidly keeps a seperate record and can get confused if you use gparted.

---

### Post by louieb on 2008-10-27
> **victimoflinux said:**
> i need simple explanation how to know what i should insert instead #,# 
:popcorn:

You use the output of the **find /boot/grub/stage2** command.

---

