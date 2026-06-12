---
title: "Resize root partition"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by gopukrishnan on 2014-04-09
Hi all,

Is there anyway to resize the root partition ? I have a test cloud server in Rackspace and I have created it using the image of my working server. I want to resize (reduce the size) my root partition and create a new partition for with that free size. Please help me.

root@555555:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/xvda1             40G   18G   20G  47% /
none                  492M  128K  492M   1% /dev
none                  498M     0  498M   0% /dev/shm
none                  498M   64K  498M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw

As you can see, /dev/xvda1 is using 40 G. I need to resize it into 20 G and create a new partition /dev/xvda2 with the remaining 20G. Is that possible ? Since it is a cloud server, I cant use live disk.

Thanks,

---

### Post by slickymaster on 2014-04-09
I think you'll manage to find a few good pointers here: [How can I resize an ext root partition at runtime]("http://askubuntu.com/questions/24027/how-can-i-resize-an-ext-root-partition-at-runtime")

---

### Post by gopukrishnan on 2014-04-09
Hi slickymaster,

I checked the link but many of them are talking about resizing (Increasing the disk space) but I want to **shrink** the **root** partition **online**. Please provide me if any good links are there. I shall check for the same.

Thanks

---

### Post by slickymaster on 2014-04-09
Sorry for not noticing in your original post that you wanted to shrink the partition, not extended it.

But, and being that the case, I'm afraid that you're kind of stucked into a corner since online shrinking is not allowed with **resize2fs** and the only way I see to do it would be booting into a live environment either off of a CD/DVD or a USB drive, which isn't applicable to your case, since we're speaking about a cloud server.

---

### Post by gopukrishnan on 2014-04-09
Hmm I understand. Thank you for your help.

---

