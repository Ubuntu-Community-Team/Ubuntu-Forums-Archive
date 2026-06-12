---
title: "Yet another grub problem..."
date: 2008-10-28
forum: New to Ubuntu
---

### Post by wrybread on 2008-10-28
I see from Googling that there are lots of issues with getting grub installed. I just had my first one, and haven't been able to solve it. 

The computer I'm installing Ubuntu 8.04 to has 5 harddrives. When I run gparted, it lists my target harddrive as the 4th harddrive, or /dev/sdd. Its partitions are /dev/sdd1 (ext3), /dev/sdd2 (extended) and /dev/sdd5 (linux-swap).

After installing, Grub didn't load at all and I got the error "boot device not found". 

I followed the steps on this page:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Now Grub successfully loads, but I get the error "Error 17: Cannot mount selected partition" when I try to load Ubuntu.

The Ubuntu files are there, I can read them just fine when I boot to the live CD and mount the partition with:

mount -t ext3 /dev/sdd1 /mnt/newshare

My menu.lst file is approximately as follows (I'm typing from a different computer so can't cut and paste):

```
title   Ubuntu
root    (hd3,0)
kernel  /boot/vmlinuz-2.6.24-16-generic root=UUID=7d619a55-5cf8-435f-8275-0820bf3aa91e ro quiet splash
initrd  /boot/initrd.img-2.6.24-16-generic
quiet

```

Can anyone think of something that may be wrong?

---

### Post by meierfra. on 2008-10-28
At the grub menu at boot up, press "c".

At the new screen type 


```
find /boot/grub/stage2

find /grub/stage2

```

One of these commands will return "(hdX,Y)", where X and Y are some numbers, for example "(hd2,0)". The other command will return "file not found".

Press "Esc" to get back to the grub  menu.

Select ubuntu, but do not press "enter", press "e" instead. At the new screen, type "e" again. Change "root (hd0,3)"  to "root (hdX,Y)", where X and Y are the numbers you got from "find".

Press enter and then "b" to boot.

Hopefully this will boot you into ubuntu.

These changes still have to be made permanent. Open a terminal and type

```
gksudo gedit /boot/grub/menu.lst
```

Look for the line 

#groot=(hd0,3) 

(should be around line 74). Change it to 

#groot=(hdX,Y)


Save the file. In the terminal type

```
sudo update-grub
```

That should be it. If this did not work, please post the output of

```
sudo fdisk -lu
```

---

### Post by wrybread on 2008-10-28
Awesome and thanks! That did it.

I was previously booting from the live CD, and typing the command "find /boot/grub/stage1", which returns a different HD than when doing it from the grub loader. When I type it from the Live CD or from my newly accessible Ubuntu install, it returns (hd3,0). 

When I type it from Grub during bootup, it returns (hd0,0).

I changed it to (hd0,0) and now all is well in the world.

---

