---
title: "On 8.04 installation grub didn't detect windows in 2nd hdd"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Infinity-al on 2008-04-25
I just installed ubuntu on my primary 40gb hdd after installing first windows on my secondary 20gb hdd.

What do i have to write in munu.lst to make windows boot up too through grub?

This is the output of "sudo fdisk -l"

```
infinity@willy:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc457b704

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245    10000431   83  Linux
/dev/sda2            1246        4728    27977197+  83  Linux
/dev/sda3            4729        4852      996030   82  Linux swap / Solaris
/dev/sda4   *        4853        4864       96390   83  Linux

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14a8e441

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2433    19543041    7  HPFS/NTFS
infinity@willy:~$ 

```

Thanks in advance.

---

### Post by bluefrog on 2008-04-25
uncomment the windows part in your existing menu.lst and change (hd0,0) with (hd1,0)

---

### Post by Xiong Chiamiov on 2008-04-25
```

title		Windows NT/2000/XP (loader)
root		(hd1,0)
#savedefault
makeactive
chainloader	+1

```

---

### Post by Infinity-al on 2008-04-25
> **Xiong Chiamiov said:**
> ```

title		Windows NT/2000/XP (loader)
root		(hd1,0)
#savedefault
makeactive
chainloader	+1

```

Adding this its stuck at: "starting up..."

I'm trying to boot windows xp pro sp 2.

---

### Post by bluefrog on 2008-04-25
change the order of your disks.

attach your windows disk so that it is master or first disk if sata (change menu.lst accordingly)

---

### Post by Xiong Chiamiov on 2008-04-25
> **Infinity-al said:**
> Adding this its stuck at: "starting up..."

I'm trying to boot windows xp pro sp 2.
Hmm.  Mine actually has another two lines in it before the chainloader:
```

#map		(hd0) (hd1)
#map		(hd1) (hd0)

```
which I am not altogether sure if they are supposed to do anything, especially since they're commented out.  I can't test it out, since I did some reformatting this weekend and haven't put XP back on, but that's what I had before (aside from different maps).
What about if you disable your 40 gig in the bios and tell it to boot directly off the 20 gig?

---

### Post by Infinity-al on 2008-04-25
I have to go to school now... WIll try later

---

### Post by Infinity-al on 2008-04-25
I selected from boot menu the 2nd hdd with win xp and when booting i get a:

NTLDR is missing
Press CTRL + ALT + DEL to restart

i get also the same error when adding and uncommenting xiong's 'map' lines

---

### Post by Infinity-al on 2008-04-25
BUMP...

Please help :(

---

