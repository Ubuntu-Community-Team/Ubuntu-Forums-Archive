---
title: "mount a .vhd in ubuntu guest"
date: 2013-12-17
forum: New to Ubuntu
---

### Post by souraklis on 2013-12-17
I had problem boot in ubuntu guest from virtualbox (due to guest updates). I am using as a host windows xp. I ve located the .vdi file of the ubuntu guest and  I ve decided to create a new machine and mount the virtual hard disk in order to access my files. I found fuse command in order to do so. I ve installed fuse with ```
sudo apt-get install virtualbox-fuse
```. Now I am trying to mount the .vhd file with the following command: ```
sudo vdfuse -a -f /path-to-vdi-file /mnt
```. In path_to_vdi_file I ve got to give the path of .vdi from my windows system??? For example I ve found that .vdi is in the following path: ```
C:\Documents and Settings\chrathan\VirtualBox VMs\ubuntu\ubuntu 12.04.vdi
```. I am trying to write sth like that

```
sudo vdfuse -a -f /C:\Documents and Settings\chrathan\VirtualBox VMs\ubuntu\ubuntu 12.04.vdi /mnt
```

What is the actual solution of mounting my virtual hard disk?

---

### Post by jones quest on 2013-12-17
The guest inside the virtual machine does not see anything outside of the box. That's kind of the whole point of virtualization. So you can safely mock about things and not break your host machine. You can however share folders with host and guest in the virtualbox settings (Shared folders). You need Guest Additions installed for the guest in order to use this functionality. Regular users might not be allowed to view/modify these shared folders unless you change the rules (create a group with access to shared folders and add yourself to this group). For now you can bypass this by using root.

So you have two guest images:
Image A which your trying to recover data from and
image B which running, and trying to mount image A on.
Is this correct?

So you share the folder with image A in your virtualbox settings for your new virtual machine (running image B). Just make sure you don't share the both image A and B, which could create a problematic loop scenario. Virtualbox will automatically mount this image A into /media/[sf_sharename] if you set shared folders to automount.

You can access this as root:
sudo su

In order to mount this image A. You need qemu-utils installed.
apt-get install qemu-utils

Create a new folder to mount the image A to:
mkdir /media/imageA

Remove nbd if already loaded and reload nbd kernel module with high enough settings:
rmmod nbd
modprobe nbd max_part=16

Mount image A with qemu-nbd:
qemu-nbd -c /dev/nbd0 /media/[sf_sharename]/[imageA.vdi]
mount /dev/nbd0p1 /media/imageA
(nbd0p1 assumes that your virtualbox image has your data on partition 1)

You can now view and copy the content of image A from /media/imageA to anywhere in image B.

---

