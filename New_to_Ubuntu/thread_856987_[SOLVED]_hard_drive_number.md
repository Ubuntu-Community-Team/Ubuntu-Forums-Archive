---
title: "[SOLVED] hard drive number"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by SILLAT on 2008-07-12
is there a command i can use to see my hard drive partion numbers like:
(hd0,0) or (hd0,1)
i want to create a splsh image at grub but i cant seem to get my mount drive number right to display the screen.. keeps failing. .

---

### Post by PmDematagoda on 2008-07-12
Perhaps device.map can show you:-
```
cat /boot/grub/device.map
```

---

### Post by cdtech on 2008-07-12
sudo fdisk -l will list the drives, the following is the structure of how Linux/Grub determines the output.

1st Physical Hard Drive:
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hda1 ----(hd0,0)----- /dev/sda1-------(hd0,0)
/dev/hda2 ----(hd0,1)----- /dev/sda2-------(hd0,1)
/dev/hda3 ----(hd0,2)----- /dev/sda1-------(hd0,2)
/dev/hda4 ----(hd0,3)------/dev/sda2-------(hd0,3)

2nd Physical Hard Drive:
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hdb1---- (hd1,0)----- /dev/sdb1------ (hd1,0)
/dev/hdb2---- (hd1,1)----- /dev/sdb2------ (hd1,1)
/dev/hdb3---- (hd1,2)----- /dev/sdb1------ (hd1,2)
/dev/hdb4---- (hd1,3)----- /dev/sdb2-------(hd1,3)


Hope this helps..........

---

### Post by SILLAT on 2008-07-12
when i ru the  cat /boot/grub/device.map command this is wat i get 
(hd0)	/dev/sda
(hd1)	/dev/sdb

need a little more details like hd0, 0 or hd0 1

thanks anyway man

---

### Post by PmDematagoda on 2008-07-12
Since you now know the required entry for the drives, all you now need is to know the proper partition number, which is as follows:-
1st partition on sda1 >> (hd0,0)
2nd partition on sda1 >> (hd0,1)
In a way it is like what cdtech posted.

---

### Post by SILLAT on 2008-07-12
can u tell which number is normally the mount i hav a seperate mount with partions string out like this /mount  /root /usr /tmp /var /home

---

### Post by PmDematagoda on 2008-07-12
If you didn't specify a separate partition for /boot, then / is what you want.

---

### Post by SILLAT on 2008-07-12
i specified a different partition for my  /boot from /root they are seperate so i guess it will be hd0, 1

thanks ya'll

---

