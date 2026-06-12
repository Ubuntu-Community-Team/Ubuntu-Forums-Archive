---
title: "Lost Windows partition"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-06-27
Earlier I helped a friend install Ubuntu, and the Windows partition now seems to be lost.  Unfortunately I do not have his computer right now (I will be able to test out fixes and post command line output in a few hours), but I would really like to have some things to try when I have access to his computer soon.

We had tried to install with the first option in the Ubuntu LiveCD install menu, the one to resize the master partition and use free space, but that did not work.  Instead, we created some free space through Vista's partition manager, and in the Ubuntu install menu we used the 'use the largest continuous space" option.

The problems:

1) The windows partition does not appear in the initial boot list.
2) In Nautilus, there does seem to be a partition that may be home to Vista (not sure about this, how can I tell?).  However, clicking on it to mount it causes a short error message simply stating that the partition cannot be mounted.
3) In the Grub list from "sudo gedit /boot/grub/menu.lst", the windows partition does not show up.

Could the windows partition have been deleted?  How can I see if it is still there?  If it is, how can I boot into it?  Any help would be much appreciated; I was just finished telling my friend how effortless the Ubuntu install is, and then it goes wrong, so I'd really like to get this fixed.

Thanks in advance.

---

### Post by forger on 2008-06-27
I'm not sure, but I don't think largest continuous space means the largest **free** continuous space.

Check if the partition is still there, open up applications > accessories > terminal:
```
sudo fdisk -l
```

Post back the results of the output

---

### Post by forger on 2008-06-27
Also this:
```
df -h
```

---

### Post by bumanie on 2008-06-27
Sounds as though you have probably overwritten the windows partition. It's a bit hard when don't have access to the computer. When you do have access, > sudo apt-get install gparted open partition editor through System --> Administration --> Partition editor and you will be able to see if the windows partition still exists. If not you can either use testdisk to try to recover the windows partition or install ntfsprogs in ubuntu and use ntfsundelete. > sudo apt-get install ntfsprogs I think you use command sudo ntfsundelete /dev/sdx,x You will have to look up the documentation prior to using either of these tools.

---

### Post by ConMan318 on 2008-06-27
We got it working!  On installing gparted it looked like the Vista partition was still there, same with "fdisk -l".  So we manually edited "/boot/grub/lst" to allow the boot-loader to see the partition, and after 2 guesses at what number to put in the (hd0,x) part, he was able to boot into Vista!  (The magic number ended up being 2)

Thank you both for your help in restoring my friend's faith in Linux.

---

