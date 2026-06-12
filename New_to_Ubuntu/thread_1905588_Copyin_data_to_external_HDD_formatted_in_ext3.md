---
title: "Copyin data to external HDD formatted in ext3"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by alfi76 on 2012-01-07
Hi guys,

im currently working on a project for my final year at university which invoilves evaluating different techniques in wiping and recovering data using Windows and Ubuntu.

My sample data which will be copied on the external HDD (formatted in ext3) has been created on Windows7 and so far i have managed to copy it onto my Ubuntu machine.

The problem is now to get the same data onto the external HDD. 
Either if i drag and drop or copy and paste the data from my home folder onto the external ext3 drive i get the the message:

Error while copying
The folder "name of the folder" cannot be copied because you do not have permission to create it in the destination.

I am new to linux/ubuntu and the only thing i have managed to understand is that you need to be in root in order to copy data to an external drive, but i do not really know what it means.

I was wondering if someone could briefly explain to me what it means and what to do in order to avoid this problem or fix it.

As i cannot go on with the project i would really appreciate any help at all!

Many thanks!!

---

### Post by ajgreeny on 2012-01-07
The problem is because an ext3 formatted partition, ie, your external disk, follows Linux permissions, and the mountpoint folder for that partition, /media/*disk* is owned by root, not by you as user.

The easiest way to solve this is for you to give the external disk/partition a label so it will always mount in the same folder in the filesystem with the command ```
sudo tune2fs -L <labelname> /dev/sdx#
``` having first found the dev name with ```
sudo fdisk -l
```

Now with the disk attached run the command ```
sudo chown user:user /media/label
``` replacing "user" with your username and "label" with your chosen label name.

I hope that is clear to you, but if not come back again for more help.

---

