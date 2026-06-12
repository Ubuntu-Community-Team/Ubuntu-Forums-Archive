---
title: "Using gparted app instead of live cd gparted in ubuntu 20.04 LTS"
date: 2020-09-19
forum: New to Ubuntu
---

### Post by imon57 on 2020-09-19
I have installed ubuntu 20.04 LTS without creating any partition. So, I have only a partition in my system. Now I want to shrink it and create a new partition. But I have formatted my bootable pendrive and I have no ubuntu iso file either. So, I want to know there is any difference between live cd gparted and gparted app. Is there any chance of data loss while creating new partition? If there is a chance, then how to create backup?
Thanks in advance.

---

### Post by keshavnrj on 2020-09-19
Hi @imon57 If you have installed [COLOR=#000000]ubuntu 20.04 LTS [/COLOR]already and want to create partition, you can do it using disk partition utilities. 
You can use gnome disks application that ships by default in 20.04 or install gparted to do the same.

If you use disks app,
- Open gnome-disks by searching for 'disks' in app launcher.
- Choose your disk on the left panel.
- Select the Unallocated partition you want to make partition of.
- Click on the (+) button to create partition.
- Choose partition type and mount point if applicable.
- Click on the create button to finalize your choice and create partition.

---

### Post by MoebusNet on 2020-09-19
Yes, there is a difference. To create/modify/delete partitions, the drive needs to be unmounted. What that means in your case is that if you were able to use gparted from your operatng partition, you would wipe out everything including your data. _Do not do this!_ You should instead, as you mentioned, back up your data _then_  use gparted live to modify your partitions.

---

### Post by MoebusNet on 2020-09-19
@imon57 - Backup practices vary. My personal routine is to use Grsync to copy my Home folder to my backup external hard drive. If I have to reinstall my Operating System, I will still have my data (Documents, Pictures, Music, Downloads, etc.) and most configuration settings. If I have to reinstall my OS, I can install the Grsync app to the new OS then synchronize my data from my external hard drive to my new Operating System Home folder or partition as desired.

---

### Post by grahammechanical on 2020-09-19
There is always the possibility of loosing data when we resize and move partitions. In fact, GParted will warn you of the danger. The utility will create a list of ordered operations and work its way through the list. Which can take some time. I prefer to complete one operation at a time. I think it lessens the risk of something going wrong. Over the years I have resized and moved many partitions as I like to have more than one installation of Ubuntu and its flavours on my machine. I have never lost any data. But there is always the risk of data lost.

GParted does not let us resize a mounted partition. You have only one partition on that hard drive. Installing GParted in Ubuntu will not let you do what you want.

>        Editing partitions has the potential to cause LOSS of DATA.       
       The gparted application is       designed to enable you to edit partitions while       reducing the risk of data loss.       The application is carefully tested and is used       by the GParted project team.       However, loss of data might occur due to software bugs,       hardware problems, or power failure.       
       
You can help to reduce the risk of data loss by       not mounting or unmounting partitions outside of       the gparted application while       gparted is running.       

       
You are advised to BACKUP your DATA before using       the gparted application.

> Partition operations such as delete, move, copy, format,           check, label, and often resize require the partition to be           unmounted

>            If           Partition &#8594; Unmount           does not succeed, then the partition is probably in use.           



those are quotes from the GParted manual

[https://gparted.org/display-doc.php?name=help-manual](https://gparted.org/display-doc.php?name=help-manual)

If you backup your data where do you intend to store it? On that single partition that is on your hard drive? Will you store it in your Ubuntu home folder? Break ubuntu then you lose it all.

 I think that you need to do the very two things that you say you cannot do.

Regards

---

### Post by Impavidus on 2020-09-20
As stated above, if you want to use gpared to modify the partition of your installed system, you have to use a live disk. But a live disk is a great tool to have anyway, as it allows you to fix your system if broken. It rarely happens, but if your system breaks and you've got no live disk, you've a big problem. Last time I had a flat tire on my bike was 18 megametres ago. Still I always go cycling with a tire repair set. Similar with backups. You want to have those at all times, just in case something unlikely happens.

---

### Post by imon57 on 2020-09-20
[COLOR=#DD4814][COLOR=#000000]@[keshavnrj]("https://ubuntuforums.org/member.php?u=2032310")
[/COLOR][COLOR=#DD4814][COLOR=#000000]@[MoebusNet]("https://ubuntuforums.org/member.php?u=150834")
[/COLOR][/COLOR][/COLOR][COLOR=#DD4814][COLOR=#000000]@[grahammechanical]("https://ubuntuforums.org/member.php?u=1087323")[/COLOR][/COLOR][COLOR=#DD4814][COLOR=#DD4814][COLOR=#000000]
[/COLOR][COLOR=#DD4814][COLOR=#000000]@[Impavidus]("https://ubuntuforums.org/member.php?u=1417721")

Thanks to all. Your replies have helped me to clear my doubts and I have got the exact idea which I wanted.[/COLOR][/COLOR][/COLOR][/COLOR]

---

