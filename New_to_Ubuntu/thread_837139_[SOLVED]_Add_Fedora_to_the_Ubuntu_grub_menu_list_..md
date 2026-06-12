---
title: "[SOLVED] Add Fedora to the Ubuntu grub menu list ..!!?? HELP"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Biggy on 2008-06-22
hi
i cannot boot Fedora . from Ubuntu grub can se windows xp and Ubuntu options for booting.

i use this command from ubuntu :

> sudo mkdir /mnt/fedora
sudo mount -t ext3 /dev/sda8 /mnt/fedora
cd /mnt/fedora/boot/grub/
ls -l

result :
> -rw-r--r--+ 1 root root     63 2008-06-22 02:51 device.map
-rw-r--r--+ 1 root root  11768 2008-06-22 17:10 e2fs_stage1_5
-rw-r--r--+ 1 root root  11528 2008-06-22 17:10 fat_stage1_5
-rw-r--r--+ 1 root root  10776 2008-06-22 17:10 ffs_stage1_5
-rw-------+ 1 root root    696 2008-06-22 02:51 grub.conf
-rw-r--r--+ 1 root root  10768 2008-06-22 17:10 iso9660_stage1_5
-rw-r--r--+ 1 root root  12440 2008-06-22 17:10 jfs_stage1_5
lrwxrwxrwx+ 1 root root     11 2008-06-22 02:51 menu.lst -> ./grub.conf
-rw-r--r--+ 1 root root  10984 2008-06-22 17:10 minix_stage1_5
-rw-r--r--+ 1 root root  13376 2008-06-22 17:10 reiserfs_stage1_5
-rw-r--r--+ 1 root root  66003 2008-04-11 23:02 splash.xpm.gz
-rw-r--r--+ 1 root root    512 2008-06-22 17:10 stage1
-rw-r--r--+ 1 root root 110532 2008-06-22 17:10 stage2
-rw-r--r--+ 1 root root  11040 2008-06-22 17:10 ufs2_stage1_5
-rw-r--r--+ 1 root root  10376 2008-06-22 17:10 vstafs_stage1_5
-rw-r--r--+ 1 root root  13016 2008-06-22 17:10 xfs_stage1_5


help me how to add fedora in ubuntu grub menu.lst ??

from Startup-Manager i cannot se fedora ! 

thanks

---

### Post by MasterSander on 2008-06-22
Edit /boot/grub/menu.lst
```
 sudo gedit /boot/grub/menu/lst 
```

add this to it:

```
 title Fedora 9
root (hd0,3)
kernel /boot/vmlinuz-2.6.25-14.fc9.i686 root=UUID=44018c8f-c46e-49de-a31f-b6a084c40be7 ro quiet splash
initrd /boot/initrd-2.6.25-14.fc9.i686.img
quiet

```

this is assuming fedora is on the second partition of the first hard drive, grub starts count from zero. You'll also have to edit the grub manually everytime the kernel changes. You can change this by creating a seperate /boot partition.
You also have to change the UUID to what UUID your partition is.

---

### Post by Biggy on 2008-06-22
Error 22 : No Such Partition

---

### Post by MasterSander on 2008-06-22
Adjust it to the right partition. Probably 4 cause you have xp and ubuntu already and fedora makes it standard an extendable partition.

---

### Post by PmDematagoda on 2008-06-22
Perhaps you could try chainloading it, this can be particularly useful since from what I've seen, Fedora does like to discard it's old kernels after a kernel update. In the case of chainloading, the entry should look like this(from the way I remember it! Corrections may be required):-
```
title Fedora 9
root (hd0,4)
chainloader +1
```

---

### Post by bodhi.zazen on 2008-06-22
You can either copy the stanzas from Fedora, but that is a bit of a hassle to maintain, or chaiload, or use a config file.

for a config file use :

```
title Fedora 9
        configfile (hd0,7)/boot/grub/menu.lst
```

See also : 

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by Biggy on 2008-06-22
thnx all for repay

problem solved from bodhi.zazen 

thanks

---

