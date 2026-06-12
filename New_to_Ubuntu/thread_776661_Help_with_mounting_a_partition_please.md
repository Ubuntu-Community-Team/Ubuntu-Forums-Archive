---
title: "Help with mounting a partition please"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by ComeGetSome on 2008-04-30
Hello to all, 

Anyways I am a little good with Linux but as how to the what I am going to ask for I am a total newb.

Anyways I recently made a dual boot set-up running Xubuntu (Hardy) and Windows XP, Both of these partitions are fine except that I have another third Partition that's formatted as FAT32, I made this as a storage partition so that I can have store music and movies in there so that both OS's can acess them. My problem is how do I mount this third partition?

Here's the output of fdisk -l

```
Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ab66cfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        2127     6843690   83  Linux
/dev/sda3            2551        7476    39568095    b  W95 FAT32
/dev/sda4            2128        2550     3397747+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

SDA3 is the one I am trying to mount.

Please help me solve this, and If you can please make any instructions as newby friendly as possible since I suck at this sort of thing.

---

### Post by Het Irv on 2008-04-30
You need to edit your fstab file so that it will mount.

```
sudo cp /etc/fstab ~/.fstab
```
create a backup just in case, it will be located in your home folder.

```
sudo mkdir /mnt/media
```
Make a mount point for the drive, media can be replace with whatever you want to name the drive

```
sudo gedit /etc/fstab
```
open your fstab file for editing

```
dev/sda3 /mnt/media FAT32 0 0
```
add this line to the bottom of fstab, making sure that the '/mnt/media' is typed exactly as you did in step two.

```
sudo mount -a
```
Remount your drives.

Just copy and paste and you should be fine

---

### Post by ComeGetSome on 2008-04-30
Ok so I tried everything you told me yet I am getting a bit of an error.

this is the output of when I try to mount it.

```
carlos@carlos-desktop:~$ sudo mount -a /mnt/media
mount: unknown filesystem type 'FAT32'

```


It seems that everything would work if I can figure this part out,Whats the name that ubuntu uses for FAT 32 partitions?


I also tried changing FAT32 for "vfat" and it triggered this error when I tried to mount it.
```
sudo mount -a /mnt/media
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

So I am guessing vfat is not it.

---

### Post by santaslittlehelper on 2008-04-30
I don't have any vfat partitions at the moment but I think something like this did it for me in the past.
```
dev/sda3 /mnt/media vfat auto,iocharset=utf8,rw,noexec,umask=000  0 0
```

---

### Post by qpieus on 2008-04-30
First try to manually mount it from a terminal window. Here's the correct syntax:```
sudo mount -t vfat /dev/sda3 /mnt/media
```

santaslittlehelper's fstab line looks like it should work too.

---

### Post by Het Irv on 2008-05-01
That was the part I wasn't sure about, I figure someone would correct me if I was wrong.

---

### Post by turezky on 2008-05-01
About 10 mins ago I learned about this app [PySDM]("http://pysdm.sourceforge.net/"). You don't have to worry about any fstab anymore :). Use this app to configure the partition of your interest only. Works great on my machine.
I also would advise you to use NTFS instead of FAT32 for sharing partition. Though there are some small flaws with deleting files from NTFS under Ubuntu, it has less errors during work. I had some FAT32 partition on my old HD on desktop computer, and it gave me plenty of head ache. Everytime there were this harddisk checks on startup. Nevertheless, if you still like FAT32 there was some way to disable this checks...

---

### Post by ComeGetSome on 2008-05-01
Thank you all for your help, with all your help I was able to get it to mount,But it only has read access not write. Anyone know how to fix this? If not I might switch the partition to ex2 and get the ex2 read and write drivers for windows XP which supposedly work, Anyone have an idea as to what I should do?

---

### Post by santaslittlehelper on 2008-05-02
I got Hardy Heon installed on a old computer with a second harddrive that is unallocated so I created a small vfat partition.

Then I double clicked the vfat partition, a pop-up came with policy changes and I was asked for password.
[[IMG]http://img120.imageshack.us/img120/5581/fstab1ai0.th.png[/IMG]](http://img120.imageshack.us/my.php?image=fstab1ai0.png)
The vfat partition now mounts to /media/disk at every boot and I got full rw access, I am guessing it's a hal and gnome-mount thing.

It's now added to - Administration > Authorizations > hal/storage > Mount internal drives.
[[IMG]http://img120.imageshack.us/img120/6919/fstab2eh9.th.png[/IMG]](http://img120.imageshack.us/my.php?image=fstab2eh9.png)
No entry was made to fstab.

So my suggestion is to comment out the vfat entry you made in fstab. 
Then umount the vfat drive and see if the above works for you.

I was however able to mount /sdb1 to /mnt with full rw -
```
/dev/sdb1 /mnt/vfat vfat auto,utf8=true,umask=0000  0 0
```
[http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_%28DOS%2C_FAT%2C_NTFS%29](http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_%28DOS%2C_FAT%2C_NTFS%29))

The drive didn't show under Computer but is was there, I really think your suppose the mount in /media.

Finally fat32 is not that great for many reasons so going with something else might be the thing to do anyway.

Just to add,
you would probably only need a fstab entry if you wanted to bypass the defaults.

```
/dev/sdb1 /media/vfat vfat users,noauto,uid=1000,gid=1000,utf8=true,umask=000  0 0
```
to not auto mount but be able to mount as user.

opps! Come to think of it you are running xubuntu so you might be missing out on some gnome features. ;)
If that's the case,
```
/dev/sda3 /mnt/disk vfat users,auto,utf8=true,umask=000  0 0
```
should work.

---

