---
title: "multiboot doesn't load vista"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by cool_looc on 2008-07-27
Hello there, I am new in this forum, so, glad to meet you guys.

Currently, I have some problem here,regarding boot loader.Here is my scenario.

1. I bought a new thinkpad x61 which has Vista already.
2. Then, I install ubuntu, after that, I install windows xp. You can see the following list which is my partition table.

> root@ubuntu:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x179bdd31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         723     5804032   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         723        4091    27050704    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            4091        7640    28508760    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4            7640        9729    16783200    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5            4091        5063     7809448+  83  Linux
/dev/sda6            5063        5209     1171768+  82  Linux swap / Solaris
/dev/sda7            5209        7640    19527448+   7  HPFS/NTFS

note that, /dev/sda7(primary) is where I put my XP, /dev/sda1(primary) is the vista recovery, /dev/sda2(primary) is where is the Vista.

The following is my grub loader..
> title		Debian GNU/Linux, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1cec403a-2f92-4a68-bb51-6fdf5c49d309 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-19-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1cec403a-2f92-4a68-bb51-6fdf5c49d309 ro single
initrd		/boot/initrd.img-2.6.24-19-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1cec403a-2f92-4a68-bb51-6fdf5c49d309 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-16-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1cec403a-2f92-4a68-bb51-6fdf5c49d309 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic
#boot
root            (hd0,1)
savedefault
makeactive
chainloader     +1

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Non Unix Operating System
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


The problem here, how do I load into Vista? the last entry which is Windows Vista/Longhorn which root(hd0,1) is booting into XP. Why? It should be root(hd0,6) right? since it is reside on /dev/sda7, am I right? 

Please guide me, I'm stuck on this for the whole week.. :(

---

### Post by koji042 on 2008-07-27
You installed XP after installing Ubuntu right? Normally, you would install XP first and then Ubuntu so that GRUB overwrites the XP boot loader rather than the other way around.

You should be able to fix it by using Super Grub Disk (reinstall GRUB to the Master Boot Record): [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

Hope that helps. :)

---

### Post by kansasnoob on 2008-07-27
You can restore the GRUB boot loader using the Ubuntu Live CD. Look here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

Note though that your partitions are different so where it says:

> To enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence:
- root (hd0,0)
- setup (hd0)
- quit
- exit 

you want to change the line, "root (hd0,0)" to "root (hd0,4)" because Ubuntu is on sda5.

And also where it says:

> Boot into Ubuntu and open up another Terminal session. Then, type in sudo gedit /boot/grub/menu.lst

Scroll down to the bottom of the file and type in the following text strings:

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

The line, "root (hd0,1)" needs to be changed to "root (hd0,6)" because XP is on sda7.

Clear as mud:confused:

---

### Post by cool_looc on 2008-07-27
koji042,
I am still in process understanding supergrubdisk. 

kansasnoob,
> To enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence:
- root (hd0,0)
- setup (hd0)
- quit
- exit These steps was successfully done from terminal.

but, 
> The line, "root (hd0,1)" needs to be changed to "root (hd0,6)" because XP is on sda7. give men an error, something like "filesystem type unknown partition type 0x7"

---

### Post by stevoo on 2008-07-27
try and change the last one this :
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1 

```
to this
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Xp
root (hd0,2)
savedefault
makeactive
chainloader +1 

```

i think it mistake cause you cannot have anything on 0,0 and i dont think that 0,7 holds an OS see if that fixes it

---

### Post by cool_looc on 2008-07-28
Stevoo, I already try your technique, but this is the output.

> root (hd0,02)
Filesystem type unknown partition type 0x5
save default
makeactive
Error 12:Invalind device request
Press any key to continue
So, how grub cannot detect this filesystem?

---

