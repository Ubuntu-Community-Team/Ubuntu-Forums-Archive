---
title: "Grub Load Error 17"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by tactx on 2008-06-21
I cannot boot the computer normally. It gives me a message ..something to the effect of Grub Loading and then Grub Error 17 and the infamous blinking cursor.

I was hoping to repair this without needing to re-install...any help would be appreciated.

FYI I had recently been upgraded to the kernel ver xx.19 and had rebooted after the upgrade without issue. Had also noticed an "serious" fire wall event directed at SSH previous to my failed reboot...not sure that that matters.

---

### Post by unutbu on 2008-06-21
Boot from a LiveCD. Open a terminal and type
```

sudo fdisk -l
```

You will see output something like this:

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         660     5245222+   b  W95 FAT32
/dev/sda3   *         661       38536   304238970   83  Linux
/dev/sda4           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris
```

Note the line that ends with "Linux" in the "System" column. This is your Linux partition.
In the example above, the device name of the Linux partition is /dev/sda3. Take note of the device name for your Linux partition. We'll be using it below.

Now convert the device name into GRUB terminology. Here is a table explaining the conversion through examples:
```

Linux device name      GRUB name      meaning
/dev/sda1    	       (hd0,0)	      first partition on the first hard drive
/dev/sda2    	       (hd0,1)	      second partition on the first hard drive
/dev/sda3    	       (hd0,2)	      third partition on the first hard drive  
...
/dev/sdb1	       (hd1,0)        first partition on the second hard drive  
/dev/sdb2	       (hd1,1)	      second partition on the second hard drive 
/dev/sdb3	       (hd1,2)	      third partition on the second hard drive  
...
```

The bottom line is that the GRUB name for a partition is always of the form (hdx,y) where x and y are integers. The partition number y in (hdx,y) is always one less than the device number as reported by "sudo fdisk -l". So if a partition is called /dev/sda3 by fdisk, then the partition is called (hd0,2) by GRUB. 

Then type
```

sudo mount /dev/sda3 /mnt
```
Of course, change /dev/sda3 to the correct device name for your root partition.
```

gksudo gedit /mnt/boot/grub/menu.lst
```

You'll find near the bottom a bunch of stanzas that look like
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		**(hd0,2)**
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Change (hd0,2) to the correct (hdx,y) that you found above. You may need to change it in a number of places since you are apt to have quite a few stanzas like the one above.  Change only the ones associated with linux, not Windows, if you happen to dual boot.
Also, you probably have a line in menu.lst
which looks like this:
```

# groot=(hd0,2)
```
Change (hd0,2) to (hdx,y) with the correct values of x and y here too. Whenever you update the linux kernel, update-grub is run and that program reads groot to update your boot stanzas. If groot is wrong, you end up getting Error 17 next time you boot.

Explanation: According to [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting), GRUB Error 17 means:
> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 
This is usually because the numbers x,y are wrong in (hdx,y) as they are used in /boot/grub/menu.lst.

If at any point you feel unsure or want clarification, post.

---

### Post by tactx on 2008-06-21
Thanks, Ill give it a go and report back..:D

---

### Post by tactx on 2008-06-22
As I started through you proscribed steps unutbu, I became very confused because the only partitions I saw comming up were two HPFS/NTFS and none of my ext3 or swap partitions.For whatever reason even thought bios saw all my drives, the drive containing my Ubuntu partitions appeared not to be functioning. After a simple powerdown and reseating of the sata cables, I was able to boot normally.....GO figure!!! I guess it was a "hardware" issue??? LOL... Anyway Thank you so much....You deserve a medal..:D I guess this can be marked as solved.

---

### Post by CFBauer on 2008-06-22
Thanks.  I actually just ran into this too.

---

### Post by CFBauer on 2008-06-22
Dang.  Just restarted and got a grub error 15.  I wonder if I chose the wrong hdx,y from above.  I get all my partitions confused sometimes.

---

### Post by CFBauer on 2008-06-22
I think I choose the wrong device name to mount /Ubuntu because the /Ubuntu/boot/grub/menu.lst file is empty.  Then I run:

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /Ubuntu
mount: /dev/sdb1 already mounted or /Ubuntu busy
mount: according to mtab, /dev/sda1 is already mounted on /Ubuntu

```

I'm assuming I have to unmount /dev/sda1 to try again, but I'm not having any luck.  Could someone point me in the right direction?  I'd appreciate it, thanks.

-Chris

---

### Post by CFBauer on 2008-06-22
Well there's good news and bad news.

The bad news is I didn't figure out exactly what I wanted to know.

The good news is I fixed the issue anyway.  I rebooted to grub, and hit 'e'.  Then I selected the 'hdx, y' line, and tried changing it to a few different permutations, receiving a couple errors.  One was error 17, the other was error 15.  After a few tries everything started up normally.

---

### Post by unutbu on 2008-06-22
CFBauer, the editing you do after you press 'e' in the GRUB menu is not permanent, so now that you've found the correct (hdx,y), be sure to edit your /boot/grub/menu.lst so you can boot smoothly next time.

Regarding the error you were getting:
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /Ubuntu
mount: /dev/sdb1 already mounted or /Ubuntu busy
mount: according to mtab, /dev/sda1 is already mounted on /Ubuntu
```
You are right -- the problem is /dev/sda1 or some other device was already mounted at /Ubuntu.
So to unmount the device:

```
sudo umount /Ubuntu
```

---

### Post by Dedoimedo on 2008-06-22
Hello,

Please remember that you cannot unmount a device if you are located in one of its directories.

For example, you cannot unmount /data if you are currently located in /data/files or something alike. You must be "outside" the device or directory you try to unmount.

Dedoimedo

---

### Post by CFBauer on 2008-06-22
You guys are the best.

---

