---
title: "Create MountPoints AllPartitions"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by avnd on 2012-04-19
Hello!

I have just installed Crunchbang Linux. The file manager used is Thunar. By default, Thunar does not auto-detect partitions and create mount points for them. 

I'm not really sure what Nautilus does in Ubuntu behind the scenes. But I've been spoilt in the sense that Nautilus always shows me whatever partitions are available. To mount those partitions, all I had to do was click the icons in Nautilus.

I've been having trouble accessing my many partitions. With a bit of reading, I came up with 2 options. 

1. udisks -

```
sudo udisks --mount /dev/sdx
```the command automatically creates a temporary folder in the /media folder. The key word here is 'temporary'. Because when I delete that partition I don't see that folder in /media anymore. (I guess this is how Nautilus does it in Ubuntu. Because I repartition a lot and I don't see junk folders in /media that were used as mount-points for the previous partitions).

2. fstab

Making entries for the partitions in fstab means creating mount-points for the partitions. But when I delete that partition, the mount-point that I created is going to remain as junk. That is not so elegant.

Can someone tell me what goes on behind the scenes in Ubuntu. 

WHAT exactly detects the partitions that are existing on the system and WHAT exactly creates the temporary folders in the /media folder. I've been searching the web for quite some time for this and all I've stumbled on is 'udisks' and 'fstab'.

Many thanks.

---

### Post by Cheesemill on 2012-04-19
[GVFS]("http://en.wikipedia.org/wiki/GVFS")

Although I use #! a fair bit and it always mounts partitions for me the same way that Ubuntu does.

---

### Post by Morbius1 on 2012-04-19
Thunar works the same way Nautilus does. Thunar will show unmounted partitions in the side panel and when you select it will automatically mount to /media/label-name or /media/UUID-number just like Nautilus.

If Thunar is broken on your system, you don't want to have things in fstab, and you don't want to use the udisk command to mount them then use gigolo. It will mount them exactly the same way to exactly the same mount point that both Thunar and Nautilus does.

---

### Post by cortman on 2012-04-19
Crunchbang is one of my favorite distros. I wasn't happy when it wouldn't run on my netbook.
For mounting partitions the very best tool I've found is Disk Manager.

```
sudo apt-get install disk-manager
```

It's in the Debian repos, but not Ubuntu. It's basically a GUI for fstab.

---

### Post by Morbius1 on 2012-04-19
fstab is not an option:
> Making entries for the partitions in fstab means creating mount-points  for the partitions. But when I delete that partition, the mount-point  that I created is going to remain as junk. That is not so elegant.If you read through his post again when he says "delete" he means delete not unmount:
> Because I repartition a lot and I .....

---

### Post by audiomick on 2012-04-19
> **avnd said:**
> Hello!
2. fstab

Making entries for the partitions in fstab means creating mount-points for the partitions. But when I delete that partition, the mount-point that I created is going to remain as junk. That is not so elegant.


It is not elegant in as much as you have to go and delete the mount point by hand, but the mount point is just a folder, and can be deleted like any other folder as far as I know.

---

### Post by jerome1232 on 2012-04-19
Open a Thunar window, go to edit-preferences, click the advanced tab, search for an "enable volume management" option.

Took this from archwiki with a quick search of "thunar autodetect mount partition"

Link to source: [https://wiki.archlinux.org/index.php/Thunar#Thunar_Volume_Manager](https://wiki.archlinux.org/index.php/Thunar#Thunar_Volume_Manager)

---

### Post by cortman on 2012-04-19
> **Morbius1 said:**
> fstab is not an option:
If you read through his post again when he says "delete" he means delete not unmount:

My mistake. I read too hastily and not enough.

---

### Post by Cheesemill on 2012-04-19
> **jerome1232 said:**
> Open a Thunar window, go to edit-preferences, click the advanced tab, search for an "enable volume management" option.

Took this from archwiki with a quick search of "thunar autodetect mount partition"

Link to source: [https://wiki.archlinux.org/index.php/Thunar#Thunar_Volume_Manager](https://wiki.archlinux.org/index.php/Thunar#Thunar_Volume_Manager)

No need to do this, it's enabled by default in Crunchbang.

I'm a long time Arch user, one of the things you'll soon realize using Arch is how much is done automatically for you in other distros. As Arch uses unpatched upstream source you have to enable options and edit configuration files that you would never usually learn about otherwise :)

---

### Post by avnd on 2012-04-22
@Cheesemill, cortman, jerome1232, audiomick & Morbius1: Thanks for your replies.

> Open a Thunar window, go to edit-preferences, click the advanced tab, search for an "enable volume management" option.

The volume management feature only deals with removable storage, mate. There are no options there for me to deal with partitions on the internal hard disk.

> It is not elegant in as much as you have to go and delete the mount  point by hand, but the mount point is just a folder, and can be deleted  like any other folder as far as I know. 	

That is true, audiomick. I will eventually fall back to fstab if I cannot achieve what I'm trying to do. But since I know that what I'm trying to is not impossible (eg. Ubuntu has what I want by default), I thought I'd try and learn something on the way.

> For mounting partitions the very best tool I've found is Disk Manager.


I tried installing disk-manager using apt-get, cortman. But I don't see it anywhere on my menu lists. I know the install was successful because 

```
sudo apt-cache policy disk-manager
```

shows the current version installed. Can someone tell me how else I can start it?

> Thunar works the same way Nautilus does. Thunar will show unmounted  partitions in the side panel and when you select it will automatically  mount to /media/label-name or /media/UUID-number just like Nautilus.

> Although I use #! a fair bit and it always mounts partitions for me the same way that Ubuntu does. 	

Thunar somehow doesn't show the available partitions for me. And from what I've read in the crunchbang forums and some other thunar articles, I guess that is how Thunar actually behaves. I might be mistaken, though.


From what I've read over the past 2 days, the following link comes closest to what I want. 

[https://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present](https://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present)

But the article only describes the method for "USB devices, external hard drives and sometimes SD cards". Can someone tell me how I can adapt it for my internal hard drive partitions?

Thanks.

---

### Post by Morbius1 on 2012-04-22
After reading through this post again:
> I have just installed Crunchbang Linux. The file manager used is Thunar.  By default, Thunar does not auto-detect partitions and create mount  points for them. > Thunar somehow doesn't show the available partitions for me. And from  what I've read in the crunchbang forums and some other thunar articles, I  guess that is how Thunar actually behaves. I might be mistaken, though.Like others that have posted earlier I also am running an xfce distro - Xubuntu. Thunar does not behave as you have described above. Perhaps this is a symantics problem. Thunar auto-detects the partitions. It will only mount them when selected however. In any event have you asked the question on the Crunchbang forum?

---

