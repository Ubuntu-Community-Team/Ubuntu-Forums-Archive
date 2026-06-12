---
title: "Installation was  a breeze. However, performance seems to be a bit sluggish overall."
date: 2008-11-21
forum: New to Ubuntu
---

### Post by dhuljev on 2008-11-21
I suspect the swap partition's lackluster size is the culprit. I am running on AMD 2600+ 512 MB PC 2700, NF7S mobo and x1600 Radeon video card. Clearly not cutting edge, but the Windows installation on this box is still chugging along just fine. 

In any event, upon installation of Ubuntu I made the mistake of only setting aside 238 MB for the swap partition, as I had limited space on the hard drive I was installing it to. Is there a freeware program out there similar to Partition magic that would allow me to modify the swap partition to a larger size? I am guessing 1 gig would be good enough, as I recall reading that setting it to twice the size of your physical memory is a good rule of thumb.

Thanks in advance. :D

---

### Post by Paqman on 2008-11-21
You want Gparted, it's really good.

However, you won't be able to modify any partitions that are mounted. When you start Gparted the swap partition will be locked. You should be able to issue the "swapoff" command from a right click in Gparted, which will allow you to expand it. This will mean stealing space from an adjacent partition, which obviously you can't do if that's mounted.

Easy way around all this is to boot into your LiveCD, which already has Gparted installed on it. In the LiveCD none of your partitions will be mounted, although your swap will be. So just swapoff, make your adjustments, then reboot into your normal install.

The other thing that could be causing sluggishness is your video card drivers. Try turning desktop effects off (System > Prefs > Appearance > Desktop Effects) and see if it gets snappier.

---

### Post by dhuljev on 2008-11-21
> **Paqman said:**
> You want Gparted, it's really good.

However, you won't be able to modify any partitions that are mounted. When you start Gparted the swap partition will be locked. You should be able to issue the "swapoff" command from a right click in Gparted, which will allow you to expand it. This will mean stealing space from an adjacent partition, which obviously you can't do if that's mounted.

Easy way around all this is to boot into your LiveCD, which already has Gparted installed on it.

The other thing that could be causing sluggishness is your video card drivers. Try turning desktop effects off (System > Prefs > Appearance > Desktop Effects) and see if it gets snappier.
Thanks, will look into that.

Would it also be possible to run Gparted from Windows XP? Or is it *nix only?

---

### Post by Paqman on 2008-11-21
> **dhuljev said:**
> Or is it *nix only?

Stands for Gnome Partition Editor, so strictly *nix.

---

### Post by dhuljev on 2008-11-21
Whoops, ignore that previous question, I didn't seem the notice the part about gpart being in the live cd.

Thanks!

---

### Post by glotz on 2008-11-21
I'm not sure adding swap will help there. Have you already killed some daemons? [http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

Here's how to add swap [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) If you specifically want to make a new swap partition, you can use [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by dhuljev on 2008-11-21
Well, I have already increased the size of my swap partition from 238 megabytes to a little over a gig. This consisted of deleting the old partition, shrinking the Linux installation partition, and merging and reformating the remaining unallocated space into a swap partition. The only problem is that upon booting, the swap partition isn't swapped on automatically, and I have to run gparted every time and swap it on myself. Would modifying the fstab file make it so it swaps automatically? Here are the current contents of my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=a33942b0-a2ec-42e3-971f-1da6b72f5a5c /               ext3    errors=remount-ro 0       1
# /dev/sdb5
UUID=e51c24d8-cd62-44a3-b072-4d46a729df98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Would editing it to the following make it so the swap mounts on boot? :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=a33942b0-a2ec-42e3-971f-1da6b72f5a5c /               ext3    errors=remount-ro 0       1
# /dev/sdb3
UUID=e51c24d8-cd62-44a3-b072-4d46a729df98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

My old swap partition was located on sdb5. My current one is located on sdb3. Would this be sufficient or is more required?

> **glotz said:**
> I'm not sure adding swap will help there. Have you already killed some daemons? [http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

Here's how to add swap [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) If you specifically want to make a new swap partition, you can use [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I'll definitely look into that, even though at the moment it seems a little bit overwhelming for a newbie like me...:(

---

### Post by louieb on 2008-11-21
> **dhuljev said:**
> as I recall reading that setting it to twice the size of your physical memory is a good rule of thumb.

That advice was given when 128MB of memory was a lot. Unless it a computer I want to hibernate I use a 1/4GB - 1/2GB swap partition  no matter how much ram it has.

I really think you should be fine with the 238MB swap. Just wondering if you noticed any performance improvement when you swapon the larger partition?
  
The key to getting better performance is #1 more ram. And #2 is not running services you don't need. 

I don't recommend this for those new to Linux but  heres a pretty good how to on [tailoring services that start on boot up. ]("http://ubuntuforums.org/showthread.php?t=89491")

[How to fstab - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=283131") 

as far a your fstab question You will need to change the UUID  to the UUID of the new swap partition. to find its UUID run```
 
sudo blkid
```

---

### Post by dhuljev on 2008-11-22
> **louieb said:**
> That advice was given when 128MB of memory was a lot. Unless it a computer I want to hibernate I use a 1/4GB - 1/2GB swap partition  no matter how much ram it has.

I really think you should be fine with the 238MB swap. Just wondering if you noticed any performance improvement when you swapon the larger partition?
  
The key to getting better performance is #1 more ram. And #2 is not running services you don't need. 

I don't recommend this for those new to Linux but  heres a pretty good how to on [tailoring services that start on boot up. ]("http://ubuntuforums.org/showthread.php?t=89491")

[How to fstab - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=283131") 

as far a your fstab question You will need to change the UUID  to the UUID of the new swap partition. to find its UUID run```
 
sudo blkid
```
After increasing the swap partitions size, I can't say that I have experienced a noticeable increase in performance. However, I did turn desktop effects off and for now, things seems a little faster. Which kind of pisses me off that I went through all the trouble of deleting my old partition and now have to learn how to edit fstab and remount the new one. However, it will provide for a good learning experience, so I'm happy about it I guess. :)

---

### Post by glotz on 2008-11-22
dang, louieb said it all above already

ignore

---

