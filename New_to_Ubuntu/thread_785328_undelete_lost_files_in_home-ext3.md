---
title: "undelete lost files in home-ext3"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by lusisto on 2008-05-07
Hello, i have lost some files and need help. Please forgive my poor English.

The files were lost after moving directories between different locations inside my home folder (ext3). I put some folders outside my user folder but in the /home partition and after a hardy clean install (without formating /home) put that folders in my new user folder. But somewere the files were deleted. 
They are not in the .Trash folder, BUT if i look the disk usage in System monitor, i can see the space is still used (because i have only 15GB free in a 30GB home partition). how can I recover these files? Or maybe they are in some place that i cant find?

Thanks

---

### Post by glennric on 2008-05-07
If you didn't format the home partition did you set up the original home partition to be your new home partition?  If you didn't then that partition is probably still there, and is probably being mounted somewhere in the /media directory.  Post the output of the following commands
```
sudo fdisk -l
```
and 
```
mount
```

---

### Post by lusisto on 2008-05-07
yes, i have set the same partition (dev/sda7) to be the new home partition, and it was the same in my old gutsy. I know because it is a 30 GB partition

fdisk -l output:

alejandro@alejandro-laptop:~$ sudo fdisk -l
[sudo] password for alejandro: 

Disco /dev/sda: 100.0 GB, 100030242816 bytes
255 cabezas, 63 sectores/pista, 12161 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x5ea4f703

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2053    16482690    7  HPFS/NTFS
/dev/sda2            2563        6818    34186320    7  HPFS/NTFS
/dev/sda3            6819       12161    42917647+   5  Extendida
/dev/sda4            2054        2562     4088542+   b  W95 FAT32
/dev/sda5            6819        8034     9767488+  83  Linux
/dev/sda6           11913       12161     2000061   82  Linux swap / Solaris
/dev/sda7            8035       11912    31150003+  83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 2041 MB, 2041577472 bytes
61 cabezas, 60 sectores/pista, 1089 cilindros
Unidades = cilindros de 3660 * 512 = 1873920 bytes
Identificador de disco: 0x04030201

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        1090     1993608    b  W95 FAT32
alejandro@alejandro-laptop:~$ 


and mount:

alejandro@alejandro-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda4 on /DATOS2 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/alejandro/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alejandro)
/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
alejandro@alejandro-laptop:~$

---

### Post by glennric on 2008-05-07
Ok, so how about the output of the following commands:
```
ls -al /home
```
and 
```
ls -al ~
```
Don't post the output for these.  Just look through the output yourself and see if you see any of the folders that you are looking for.  Also, if you know the name of any of the folders or files that seem to be missing try
```
find /home -name "file-or-folder-name"
```
This should give you the absolute path of the file if it finds it.

---

### Post by mister_pink on 2008-05-07
Bear in mind hardy no longer uses the .Trash folder, its now in ~/.local/share/Trash/files

---

### Post by lusisto on 2008-05-07
ok, we are closer now. I ran those ls comands and a "sudo du" in "alejandro@alejandro-laptop:/home$" and I they are in a folder named "/home/.Trash-0" that is invisible on nautilus (even on a nautilus started with sudo).

I am trying to copy to another location and check if everithing is Ok and then I will come back and edit tis post to confirm. 
Thank you very much glenricc and mister_pink! Your help was useful and apreciated!

EDIT: Yes, I have found all files and folders, and have copied them to my user folder. Thanks again

---

### Post by davey_mac on 2008-05-26
Thanks very much for this thread.  i managed to find and recover files I didn't back up before a  new install.  Once again thanks.

Oh and it shows before you do anything make sure you've**_[SIZE="6"] BACKED UP[/SIZE]_** your important files.

A lesson well learned.:)

---

