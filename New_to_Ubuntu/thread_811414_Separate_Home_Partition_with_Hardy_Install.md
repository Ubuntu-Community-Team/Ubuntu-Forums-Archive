---
title: "Separate Home Partition with Hardy Install"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by myst1c on 2008-05-29
im doing a clean install of hardy, and i have my home folder backed up on an external drive so i can restore it... now what i want to do is format my drives and have one drive as a home partition, and the other drive for my system partition... how would i go about doing this?

---

### Post by Rinzwind on 2008-05-29
You can do that during install (watch for the partitioner).
Choose 'MANUAL' and here you can add/delete/change partitions.

An image can be found here: [http://apcmag.com/system/files/images/vista_ubuntu_09.article-width.jpg](http://apcmag.com/system/files/images/vista_ubuntu_09.article-width.jpg)

By the way what I did was:
a / with about 10 Gb.
a /home with 20 Gb.
a /files with the rest

On a next install I have several options:
complete wipe + reinstall: format all partitions;
reinstall with all setttings gone: format / and home;
reinstall with all settings kept: format /.

---

### Post by forestpixie on 2008-05-29
Make the partitions using the partition editor before you start the install, it's in the sys-admin menu.

Create the partitions you want - one for root one for home and a swap, give them the right filetypes.

When you start the install and get to the partition part - use manual; pick the partition you created for root  - edit it and pick a mountpoint of / . Do the same for the partition you created for home and give it a mountpoint of /home . Swap will deal with itself.

If you want to copy the original /home files across I think you need to make sure you use the same username as before.

---

