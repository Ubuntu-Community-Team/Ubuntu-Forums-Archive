---
title: "unallocated space - how to merge"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by tvor on 2012-05-22
Following my [fist post regarding the fstab]("http://ubuntuforums.org/showthread.php?t=1984847"), this is next issue I'm not sure how to resolve. 

I have two block of unallocated space on my SSD (raid). My [previous post]("http://ubuntuforums.org/showthread.php?t=1984847") shows the output of #sudo fdisk -l in live CD.

Using Gparted, on live CD does not allow me to resize the DATA (ntfs) or swap partition to accomodate the free space. I've tried deleting swap to merge the unallocated space, but it only created the small 1.12Mb space. I'm also unable to format 4.66Mb space -unable to create another primary partition(too many0 , no other option give (in Gpart). 

Same scenario when loading from Windows - unable to extend NTFS partition as it is not next. It seems the bottom unallocated space belong to the disk one (first three entries) not the extended partition.  Thank you for any sugestion

---

### Post by nm_geo on 2012-05-22
Be sure to turn off the swap file (right click) then swapoff.  I think you can then do some moving.

---

### Post by tvor on 2012-05-22
Thank you mn_geo > one right click the only option is swapon, which suggest the swap in not mounted or already swapoff (this is from live CD) .....

---

### Post by Ptero-4 on 2012-05-22
You need to somehow extend the extended partition to cover the "unallocated" space at the end (it's outside the extended partition). Then you can move things around.

---

### Post by tvor on 2012-05-22
I'm unable to to change, extent any partition to cover the unallocated space :-( resize/move gives me only option to make it smaller - not extent to unallocated space.....right click on swap gives me the option to "swapon"

---

