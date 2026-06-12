---
title: "[SOLVED] opening windows formatted flash memory"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-06
hi
I have an elecom flash drive which is password protected and will not open in ubuntu
The other identical drive without password protection works fine
I have tried opening the lock.exe file with wine but nothing happens
I have also tried reformatting it using the windows partition
any ideas how I can open/ configure it for use in ubuntu?

---

### Post by Moridin333 on 2008-08-06
I doubt that you will get it to work if the encription itself is controled by an exe file.  your best bet would be to do some searches on google and the ubuntu forums to see if anybody has done this successfully.

---

### Post by LTFC2020 on 2008-08-06
I tried reformatting it in the terminal, as gparted would not let me do anything with it:

richard@richard-laptop:~$ sudo mkfs.ext3 /dev/sda1 (where /dev/sda1 is your usb drive)
bash: syntax error near unexpected token `('
richard@richard-laptop:~$ 
richard@richard-laptop:~$ sudo mkfs.ext3 /dev/sdb1
[sudo] password for richard:
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
384 inodes, 3052 blocks
152 blocks (4.98%) reserved for the super user
First data block=1
Maximum filesystem blocks=3145728
1 block group
8192 blocks per group, 8192 fragments per group
384 inodes per group

Writing inode tables: done                            
Creating journal (1024 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 29 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
richard@richard-laptop:~$ 

gparted will now allow access but only recognises the drive as having 2.98mb of storage?

---

