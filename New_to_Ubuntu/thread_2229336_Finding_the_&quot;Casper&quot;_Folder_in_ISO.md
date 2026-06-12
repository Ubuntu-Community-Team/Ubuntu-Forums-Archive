---
title: "Finding the &quot;Casper&quot; Folder in ISO"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by michael176 on 2014-06-12
Hi there-
I am obviously doing something wrong and I am a complete noob when it comes to Linux. I downloaded an Ubuntu ISO and all of the directions I can find tell me that the vmlinuz and initrd are contained within a folder called Casper. When I mount the ISO, all I see is the following:
dr-xr-xr-x 1 root root   2048 Apr 16 15:12 boot
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 .disk
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 dists
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 doc
dr-xr-xr-x 1 root root   2048 Apr 16 15:12 EFI
dr-xr-xr-x 1 root root   2048 Apr 16 15:12 install
dr-xr-xr-x 1 root root  18432 Apr 16 15:12 isolinux
-r--r--r-- 1 root root 162102 Apr 16 15:12 md5sum.txt
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 pics
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 pool
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 preseed
-r--r--r-- 1 root root    236 Apr 16 15:11 README.diskdefines
lr-xr-xr-x 1 root root      1 Apr 16 15:11 ubuntu -> .

Where the heck is the folder casper so I can get the kernel and initrd for a project I need them for?

Thanks!

---

### Post by sudodus on 2014-06-12
Welcome to the Ubuntu Forums :-)

```
[COLOR=#0000ff]sudo mount -o loop ubuntu-14.04-desktop-amd64.iso /mnt[/COLOR]
mount: blockenhet /media/multimed-2/CD/ubuntu/14.04/ubuntu-14.04-desktop-amd64.iso är skrivskyddad, monterar som endast läsbar
[COLOR=#0000ff]ls -l /mnt[/COLOR]
totalt 2548
dr-xr-xr-x 1 root root    2048 apr 17 03:35 boot
[COLOR=#ff0000]dr-xr-xr-x 1 root root    2048 apr 17 03:35 casper[/COLOR]
dr-xr-xr-x 1 root root    2048 apr 17 03:34 dists
dr-xr-xr-x 1 root root    2048 apr 17 03:35 EFI
dr-xr-xr-x 1 root root    2048 apr 17 03:35 install
dr-xr-xr-x 1 root root   18432 apr 17 03:35 isolinux
dr-xr-xr-x 1 root root    2048 apr 17 03:34 pics
dr-xr-xr-x 1 root root    2048 apr 17 03:34 pool
dr-xr-xr-x 1 root root    2048 apr 17 03:34 preseed
-r--r--r-- 1 root root     134 apr 17 03:34 autorun.inf
-r--r--r-- 1 root root   21396 apr 17 03:35 md5sum.txt
-r--r--r-- 1 root root     229 apr 17 03:34 README.diskdefines
lr-xr-xr-x 1 root root       1 apr 17 03:34 ubuntu -> .
-r--r--r-- 1 root root 2551408 apr 14 18:04 wubi.exe
```

```
[COLOR=#0000cd]ls -l /mnt/casper[/COLOR]
totalt 970024
-r--r--r-- 1 root root     58068 apr 17 03:31 filesystem.manifest
-r--r--r-- 1 root root      1046 apr 17 03:31 filesystem.manifest-remove
-r--r--r-- 1 root root        11 apr 17 03:31 filesystem.size
-r--r--r-- 1 root root 966815744 apr 17 03:31 filesystem.squashfs
-r--r--r-- 1 root root  20648481 apr 17 03:31 initrd.lz
-r--r--r-- 1 root root   5778968 apr 17 03:31 vmlinuz.efi
```


I can see it. What did you download? I got my iso file via torrent from the [official Ubuntu web-site]("http://www.ubuntu.com/download/alternative-downloads") and checked it with md5sum from
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by michael176 on 2014-06-12
ISO Downloaded from Ubuntu directly: ubuntu-14.04-server-amd64.iso
/mnt/loop (Directory I created previously)
I ran the command "sudo mount -o loop ubuntu-14.04-server-amd64.iso /mnt/loop"

This is all I see in that directory (ls -la):
dr-xr-xr-x 1 root root   2048 Apr 16 15:12 .
drwxr-xr-x 3 root root   4096 Jun  5 14:58 ..
dr-xr-xr-x 1 root root   2048 Apr 16 15:12 boot
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 .disk
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 dists
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 doc
dr-xr-xr-x 1 root root   2048 Apr 16 15:12 EFI
dr-xr-xr-x 1 root root   2048 Apr 16 15:12 install
dr-xr-xr-x 1 root root  18432 Apr 16 15:12 isolinux
-r--r--r-- 1 root root 162102 Apr 16 15:12 md5sum.txt
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 pics
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 pool
dr-xr-xr-x 1 root root   2048 Apr 16 15:11 preseed
-r--r--r-- 1 root root    236 Apr 16 15:11 README.diskdefines
lr-xr-xr-x 1 root root      1 Apr 16 15:11 ubuntu -> .

I am using the server version for a special project I am doing. Maybe that has something to do with it? The md5sums match as well. I just checked.

---

### Post by sudodus on 2014-06-12
Yes, obviously the server and desktop versions have different layouts. I guess you can find the files you want in some other directory. I haven't got that iso file, so it's not easy for me to check. I suggest that you search for the files you want with the find command

```
sudo find /mnt -name "vmlinuz*"

sudo find /mnt -name "initrd*"
```

---

### Post by ajgreeny on 2014-06-12
Surely the casper folder will only be in a live CD/DVD, therefore not in the server version, just as it was not in the Alternate Install .iso image, when such things existed.

---

### Post by sudodus on 2014-06-13
I'm not very familiar with the server installer.

*ajgreeny*, do you know if the vmlinuz and initrd files that the OP is looking for come with the server iso file, and if not, where to find them? Or are they created during the installation?

---

### Post by ajgreeny on 2014-06-13
> **sudodus said:**
> I'm not very familiar with the server installer.

*ajgreeny*, do you know if the vmlinuz and initrd files that the OP is looking for come with the server iso file, and if not, where to find them? Or are they created during the installation?

Not sure about the server, but in the alternate install CD of Lubuntu 14.04, the vmlinuz and initrd.gz both sit in a folder named install.
See screenshot of archive-manager with Lubuntu 14.04 alternate iso showing

---

