---
title: "Bash script is faster on Live CD"
date: 2007-09-16
forum: Programming Talk
---

### Post by cisk4me on 2007-09-16
I have a script which runs a program multiple times, sorting the output files for further processing. These output files are deleted at the end of the job.
I have a speed-step processor and see that for much of the time it is only running at 600MHz instead of 1.5GHz because of the slowdown caused by all these disk accesses.
I've copied the script and program to a tar file on a USB drive, booted my computer with a Live CD and untarred the archive to /home/ubuntu. When I run the script, all the disk accesses are now to RAM and the processor speed is permanently at 1.5GHz. The job time is reduced from 250 minutes to 145 minutes.
When I run the script with my installed Ubuntu, how can I get the files written to RAM instead of disk, and thus enjoy the job times seen with the Live CD?

---

### Post by pxwpxw on 2007-09-16
** cisk4me**

I can use /dev/ram0.../dev/ram15 here, I hope this explains it:
Your ramdisk size may vary.

```

x@bigmac:~$ dmesg | grep RAM
[    0.000000] Top of RAM: 0x110000000, Total RAM: 0x90000000
[   21.567928] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

x@bigmac:~$ ls -l /dev/ram*
brw-rw---- 1 root disk 1,  0 2007-09-16 22:09 /dev/ram0
...
brw-rw---- 1 root disk 1,  9 2007-09-16 20:29 /dev/ram15

x@bigmac:~$ sudo mke2fs /dev/ram0

x@bigmac:~$ sudo mount /dev/ram0 ramdir0

x@bigmac:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/ram0                63461      1289     58896   3% /home/x/ramdir0

x@bigmac:~$ mount
/dev/ram0 on /home/x/ramdir0 type ext2 (rw)
x@bigmac:~$ 

```

This is xubuntu in an Applemac G5, using 2.5GB ram. I dont know how that affects the ramdisk availability, and I dont know how to control the size or number of ramdisks.

---

### Post by cisk4me on 2007-09-17
Thanx for the info about ramdisks. I didn't know that.
I found good help at
[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html]("http://www.vanemery.com/Linux/Ramdisk/ramdisk.html")

and adapted it to my needs. I want a single ramdisk of 384MB which has to be changed from the default 64MB by modifying the parameters for grub. This is done by editing [FONT="Courier New"]/boot/grub/menu.lst[/FONT], adding the ramdisk size and rebooting.
```
$ sudo gedit /boot/grub/menu.lst
$ more /boot/grub/menu.lst
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=17e83647-9ad5-487b-b659-81d04109ba66 ro quiet splash ramdisk=393216
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```
After the reboot, as in your post:
```
$ sudo mke2fs /dev/ram0
mke2fs 1.40-WIP (14-Nov-2006)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
98304 inodes, 393216 blocks
19660 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=67633152
48 block groups
8192 blocks per group, 8192 fragments per group
2048 inodes per group
Superblock backups stored on blocks: 
        8193, 24577, 40961, 57345, 73729, 204801, 221185

Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 36 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
$ sudo mount /dev/ram0 /home/ramdisk
$ sudo chown -R graham:users /home/ramdisk
```
User data and jobs can now be copied to [FONT="Courier New"]/home/ramdisk[/FONT] where they run much more quickly if there are frequent disk accesses:)

---

### Post by pxwpxw on 2007-09-17
Thanks for that, very useful.:)

---

### Post by avik on 2007-09-17
Wow!  That really is nifty.  This is a great example of how the "everything is a file" mentality really pays off.

---

### Post by cisk4me on 2007-09-17
Not really so nifty. What would be better is say a command different from bash, say rambash, which would start the job in RAM and keep it there while there was sufficient memory, swapping it to disk automatically when the memory was exhausted. This is a bit like the old Apple "multitasking" where you had to manually allocate each jobs memory in advance.
Still, it is certainly better than not having the facility at all and I'm now using it every day :)

---

