---
title: "[SOLVED] error17 cannot mount partition?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-22
i installed slackware awhile ago and it took over my mbr.i couldnt edit lilo to include ubuntu so i installed slack without lilo,and re installed ubuntu.heres the problem i changed the /boot/grub/menu.lst to include slack
but i get error17,heres how i have it written;

### END DEBIAN AUTOMAGIC KERNELS LIST



title           Slackware 12.1, kernel 2.6.24-5
root            (hd0,3)
kernel          /vmlinuz root=/dev/sda3 ro

is this not right?,do i have to do a chainloader?
Rick

---

### Post by Patb on 2008-08-22
Rick, first try reinstalling Grub using Catlett's [How to restore Grub from a Live Ubuntu CD]("http://ubuntuforums.org/showthread.php?t=224351").  If that doesn't work post the output of each of these three commands:
```
sudo fdisk -l
sudo blkid
tail -40 /boot/grub/menu.lst

```
Cheers, Pat

---

### Post by pauper on 2008-08-22
Does your /sbin/init is on (hd0,2)? Your "root=" statement corresponds to that.
Shouldn't it be as root=/dev/sda4??? You might need to specify path to initrd
as well.

Check if your filesystem isn't become corrupted with "fsck" or "e2fsck". Make
sure it's unmounted.

---

### Post by Patb on 2008-08-22
Rick, Pauper is right. The notations for grub and linux partitions are different. Grub starts at zero, Ubuntu at 1.  

So assuming your Slackware is on grub's (hd0,3) that will equate to /dev/sda4 (or possibly /dev/hda4 if it is an IDE drive).  Similarly (hd0,2) would equate to /dev/sda3 or /dev/hda3.  You can edit your menu.lst file and try. 

Cheers, Pat

---

### Post by rixtr66 on 2008-08-22
ok i changed the (hd0,3)to (hd0,2) and went with sda3 now i get error 15,dont forget i dont have lilo installed on slack i dont know why that would matter as grub should do the job.here are the outputs you asked for in order;

rick@ubuntu1:~$ sudo fdisk -l
[sudo] password for rick: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8a1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4664    37463548+  83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda3            4665        9047    35206447+  83  Linux
/dev/sda4            9048        9327     2249100   82  Linux swap / Solaris
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Partition table entries are not in disk order
rick@ubuntu1:~$ 

rick@ubuntu1:~$ sudo blkid
/dev/sda1: UUID="97bef854-d5ea-4b88-8372-8a337670af46" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ef4561a3-6dac-4cab-a378-8b071ceb1dd4" 
/dev/sda3: UUID="b9d064cb-59d4-4d48-8927-bd8c852ccb9d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="a57231f1-3e70-4028-9426-6a8cdd6aa4ec" 
rick@ubuntu1:~$ 

rick@ubuntu1:~$ sudo tail -40 /boot/grub/menu.lst
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=97bef854-d5ea-4b88-8372-8a337670af46 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=97bef854-d5ea-4b88-8372-8a337670af46 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=97bef854-d5ea-4b88-8372-8a337670af46 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=97bef854-d5ea-4b88-8372-8a337670af46 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



title           Slackware 12.1, kernel 2.6.24-5
root            (hd0,2)
kernel          /vmlinuz root=/dev/sda3 ro
initrd          /boot/initrid.img-2.6.24-5-smp
rick@ubuntu1:~$ 

hope this helps!
Rick

---

### Post by caljohnsmith on 2008-08-22
I just wanted to mention, Rick, that a really easy way to boot Slackware (or any other distro) from Ubuntu is if you can install Slackware's LILO boot loader *to the boot sector of the Slackware partition* (sda3), and not to the MBR. That way all you have to do to boot it is add in your menu.lst:
```
title    Slackware
root (hd0,2)
chainloader   +1
```
No fuss, no hassle. I'm not sure how the LILO installer works, but with Grub, you just tell it to install itself in (hd0,2), or the boot sector of sda3, instead of (hd0) which would be the MBR.

---

### Post by rixtr66 on 2008-08-22
caljohnsmith;thanks ill give that a shot,although i dont know much about lilo,i was hoping to use grub.it makes sense though!
Rick

---

### Post by caljohnsmith on 2008-08-22
Rixtr66, I think you might have misunderstood; you would still be using Grub on startup, because you would leave Grub in the MBR. But if you can install your Slackware's boot loader LILO to the boot sector of its own partition (and not the MBR), then to boot slackware from Grub is as simple as doing the "chainload" notation I gave. So you're not giving up Grub, you're just making it really simple to boot Slackware from Grub. If you need any more help/details about it let me know. :)

---

### Post by rixtr66 on 2008-08-22
Thanks a bunch!!! turns out lilo wasnt that hard!i didnt want to give up my favorite distro ubuntu,to try slack but isee slack as a challenge.ive learned a ton about ubuntu here thanks to guys like you!
it worked like a charm!
Thanks again.
Rick:)

---

### Post by Patb on 2008-08-22
Hi Rick. A possible explanation: The reason your Grub menu gave error 15 is because it could not find a file specified. That was probably in the line "kernel /vmlinuz root=/dev/sda3 ro" where I am guessing there was no such file as "/vmlinuz" on /dev/sda3.  The line should perhaps read something like:
```
kernel /boot/vmlinuz-2.6.24-5-smp root=/dev/sda3 ro
```
assuming that the file "/boot/vmlinuz-2.6.24-5-smp" is actually the correct path and name (ie on /dev/sda3 not /dev/sda1). 

This is just an explanation and not to lessen Caljohnsmith's solution. 

Cheers, Pat.

---

### Post by pauper on 2008-08-22
/vmlinuz is a symbolic link to the most recent compressed kernel in /boot
directory.

Though it's never a bad idea to provide the absolute path:
/boot/vmlinuz-`uname -r`, for example.

---

