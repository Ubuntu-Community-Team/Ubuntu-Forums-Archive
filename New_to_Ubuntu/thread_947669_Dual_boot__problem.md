---
title: "Dual boot  problem"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by the rocketray on 2008-10-14
:guitar::guitar:Hi everybody,
            This is my first post and im a complete newbie so please be patent with me,if this post is inapropriate in some way i appologise in advance.
                            so ive got two hard drives on my computer my main(C)drive on which ive got windows XP running.Its on a SATA drive 200gb.On my second drive (an 80gb ide drive)ive installed UBUNTU 8.040(the latest one)after the install i cant get ubuntu or xp to boot.so after some searching and reading i started the live disk,opened the terminal and typed "sudo  grub"then "find /boot/grub/stage1" to which i got the reply(hd1,0)so then i typed "root (hd1,0" followed by "setup (hd1)" and "quit".And everthing seemed good.shut down Ubuntu and restarted.now i get GRUB Loading stage1.5. then GRUB loading,please wait and then GRUB (no curser) so i assume from that that Grub has Loaded.But what now,i cant help feeling that ive missed something so obvious that i'll be embarassed when i look back. PLEASE help me get umbuntu up and running or do i need to reinstall xp and ubuntu in a different way?
                  Thanks for your Help

---

### Post by LowSky on 2008-10-14
sounds like grub is messed up. go to Google type Super Grub, download the SuperGrub CD and use it to fix the install

---

### Post by kansasnoob on 2008-10-14
Please post the output of:

```
sudo fdisk -l
```

That's a lower case L.

And also:

```
 cat /boot/grub/menu.lst
```

Once again, that's a lower case L.

---

### Post by the rocketray on 2008-10-14
> **kansasnoob said:**
> Please post the output of:

```
sudo fdisk -l
```

That's a lower case L.

And also:

```
 cat /boot/grub/menu.lst
```

Once again, that's a lower case L.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c211c20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS
/dev/sda2           24321       24321        8032+   f  W95 Ext'd (LBA)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18cbb1a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / 
Solaris


ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory


I copied and pasted the above command cuz i thought i had input it wrong.anyway does it help?

---

### Post by caljohnsmith on 2008-10-14
Are you sure you have your BIOS set so that the Ubuntu drive boots first on start up?

Please post the output of the following:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump

```

---

