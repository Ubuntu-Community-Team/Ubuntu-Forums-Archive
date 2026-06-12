---
title: "Is Ubuntu Plug n' Play for hard drives"
date: 2017-03-10
forum: New to Ubuntu
---

### Post by robertzito on 2017-03-10
I just purchased a second hard drive for my laptop that I will be using strictly for storage, when I install the drive will it auto discover or do I need to do something to make the drive automatically mount or will it act just as if I plugged an external drive in like the USB stick?

---

### Post by Irihapeti on 2017-03-10
Ubuntu certainly can autodiscover internal drives, but you may find it more convenient to mount it using an entry in /etc/fstab.

If it's an external drive, it should behave like a USB stick.

---

### Post by Bucky Ball on 2017-03-10
Yes, with a caveat. You will generally need to connect the drive, launch Gparted, choose the new drive from the drop-down menu in the top right of the Gparted GUI, go to 'Device> Create new partition table'. Once that's done, partition the drive how you want it (right click the free space and 'new') then you're good to go.

Irihapeti is right in as much as the system will recognise you have a new drive in there, but there's nothing on it, including partitions, so you need to put some partitions on it. But yes, plug it in, it will be recognised, but not usable until you format it.

(Just to add: there is nothing to 'automatically mount' on a new drive. It will recognise the drive, but mount what? There's no partitions on it *to* mount until you create some and then mountpoints for them, generally in /media or /mnt. You will then need to edit the /etc/fstab file to get them mounting at boot ... if that's what you want. :))

---

