---
title: "unable to boot"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by g.voumvoulaki on 2013-11-15
Hi all!
I am very new to linux-I installed Lubuntu 3 months ago due to my windows laptop being stolen and having to make do with a 10 year old laptop with 512MB ram so I needed something really light.
Its been great getting to learn since I configuered everything by reading these forums and the community is awesome!

Well unfortunately 2 days ago I found my laptop being unable to boot ..

This time though I don't have much access to another one in order to do a lot of reading and searching on my own so I though I should get some help!I managed to try reboot-repair tool while booting Ubuntu 12.04 from a cd I had available(on try not install)

This is the bootinfo:
[http://paste.ubuntu.com/6423882/](http://paste.ubuntu.com/6423882/)

Your help will be greatly appreciated-thanks so much in advance!!

---

### Post by oldfred on 2013-11-16
I do not know LVM.

But you told Boot-Repair you had RAID, so it could not fix your system. Tell it you do not have RAID and see it it works. 
Boot-Repair has difficultly telling RAID from LVM as both mount with /dev/mapper

LVM is an advanced partitioning used more by servers. Has both advantages if you resize partitions a lot but add another level of complexity.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)

---

### Post by g.voumvoulaki on 2013-11-16
Hi , thanks for your answer.

I tried by telling boot-repair I  have no RAID , I got a message saying that my /dev/mapper/lubuntu-root  is full and I needed to use the opened-up file browser to free-up some  space. I did move a lot of my personal files from home to the trash but  then it said it was still full.


This is my df -k

```
ubuntu@ubuntu:~$ df -k
df: `/root/.gvfs': Permission denied
Filesystem               1K-blocks     Used Available Use% Mounted on
/cow                       1028580   193796    834784  19% /
udev                       1019960       12   1019948   1% /dev
tmpfs                       411432      808    410624   1% /run
/dev/sr0                    771372   771372         0 100% /cdrom
/dev/loop0                  739712   739712         0 100% /rofs
tmpfs                      1028580      700   1027880   1% /tmp
none                          5120        4      5116   1% /run/lock
none                       1028580      208   1028372   1% /run/shm
none                        102400       76    102324   1% /run/user
[U]/dev/sda1                   233191   227333         0 100% /mnt/boot-sav/sda1
/dev/mapper/lubuntu-root  76166224 72967796         0 100% /mnt/boot-sav/mapper/lubuntu-root[/U]
```

I also read another thread about removing old kernels from /boot but I don't think I have old kernels to remove

 ```
ubuntu@ubuntu:~$ ls /boot/
abi-3.5.0-17-generic     grub            memtest86+_multiboot.bin
config-3.5.0-17-generic  memtest86+.bin  System.map-3.5.0-17-generic

```

I also tried 'sudo apt-get autoremove'but nothing

```
ubuntu@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 470 not upgraded.


```

---

### Post by heir4c on 2013-11-16
Trow away the files in the trash makes no different if you don't empty the trash after you dump the files onto.
But beside that:
You have used the LVM option when you installed Lubuntu. That is not recommend and not nessesary. That's good for server, raid and ... Not for a normal setup of a Laptop or Desktop.
Do a new install. (Take Lubuntu 13.10) Boot up from a Live-cd/usb and backup your personal data on a extern HD (or usb).
You need 2 partitions.1 for the root partition and 1 for a swap partition.
In the installing proces you can choose to use the hole disk and than the installer make automaticly the 2 partitions.

---

### Post by g.voumvoulaki on 2013-11-16
Yes I thought so but I am unable to access the trash bin for some reason when I see the file browser through the boot-repair..

I understand  that I would be better in general if I had not installed the LMV as it is unnecessary but this does not  cause my current problem right?From what I understand I am unable to  boot because lubuntu-root is full...

---

### Post by Allavona on 2013-11-16
Are you able to use a Live system to chroot into your install? From there you can do what you need to do. I'm in no way knowledgeable about LVM and won't pretend to be so I can't offer too much help. At least in a chroot environment you'll have access to programs and and can remove and uninstall things to clear space up. You could also use gparted to do some resizing if your thinking thats the cause.

What changes did you make 2 days ago that may have caused this?

In any regards, if you get this cleared up and get your files off, I would go with the others and wipe and do a standard default install with / and /swap. Or at the very most a root, home, and swap.

---

### Post by oldfred on 2013-11-16
I have this in my notes, while it is for encrypted LVM, you can skip the encryption part. 
It shows mounting the LVM and then chrooting into it.

[http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/](http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/)

---

