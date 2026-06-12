---
title: "[SOLVED] make grub to boot different partition"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by shodan on 2008-08-25
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12618   101354053+  83  Linux
/dev/sda3           12645       77825   523566382+   5  Extended
/dev/sda5           12646       64666   417858682+   7  HPFS/NTFS
/dev/sda6           64667       77284   101354053+  83  Linux
/dev/sda7           77285       77825     4345551   82  Linux swap / Solaris

```

Originally I had windows installed on /dev/sda1 and ubuntu on sda6.
I cloned sda6 to sda1.
How can i make grub to load sda1 as root partition?
Right now /dev/sda6 is mounted as root.

Since i have only one system now how can i hide boot menu?

---

### Post by caljohnsmith on 2008-08-25
You'll need to modify your Grub's /boot/grub/menu.lst file. If you can't boot into anything right now, boot a Live CD, mount your Ubuntu partition, and print the menu.lst:
```
mount /dev/sdaX /mnt
cat /mnt/boot/grub/menu.lst
```
Where X is the number for the Ubuntu partition. Please post the output of the commands above.

---

### Post by shodan on 2008-08-25
I fixed it.
Somehow grub never saved changes i made to manu.lst from live cd or my old ubuntu partition.

everytime i changed (hd0,5) to (hd0,0) it was back to 0,5 after boot.

I changed it from grub menu before system loads.
Now works fine + editing menu.lst works too :)

---

