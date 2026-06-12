---
title: "can't delete files in flash drive"
date: 2018-07-29
forum: New to Ubuntu
---

### Post by hideri-chwan on 2018-07-29
edit. I can't also move files to the flash drive.

hello.

I'm new to this operating system(lubuntu 16.04) and I recently noticed that I can't delete the contents of my flash drive. I already tried hdparm command and set the read-only off. I also tried the flash drive in a different operating system like windows and deleting the contents works. I'm sure that the flash drive is not locked. 

First, I mounted the flash drive then turned the read-only off. It didn't work.
I also tried mounting the flash drive -> turning the read-only off -> unmounting the flash drive-> restarting the pc. Still doesn't work.

Oh. The pc isn't dual boot. There are two pc(laptop). The window's is a different pc.

---

### Post by yancek on 2018-07-29
> I also tried the flash drive in a different operating system like windows and deleting the contents works

If you can delete in windows then it is a windows filesystem on the flash drive.  Which windows version are you using?  If you are using 8/10, it will always be hibernated unless you as the user specifically turn it off and keep it off.  No Linux system will mount a hibernated filesystem.  You also need ntfs-3g installed to write to windows and you can check that with the command:  whereis ntfs-3g.  I suspect it is more likely to be hibernation or a corrupted filesystem on the flash drive.

---

### Post by Taylz on 2018-07-29
Hi hideri-chawn,

What format is your drive in? Have you tried changing the ownership of the drive when it's mounted in lubuntu?

Try running in the command line:

```
chown -R youruser:yourgroup /path/to/mounted/paritionorusbstick
```

Naturally change the "**youruser:yourgroup**" to your specific information and change the "**/path/to/mounted/partitionorusbstick**" to where your USB stick is mounted to.

E.g:

```
chown -R hideri-chwan@hideri-chwan /media/laptopname/USBstick1/
```

Regards,

Tayl.

---

### Post by Impavidus on 2018-07-29
When you plug the usb drive in, it should be mounted automatically in read-write mode. If that doesn't happen, there's something wrong, preventing the system from mounting it in read-write mode. As it all works on Windows, it's probably file system damage or unclean unmounting. After you use the usb drive, either in Windows or Linux, always make sure you safely remove the drive, not simply pull it out. And I'm not sure about Windows here, but it may be that you also have to safely remove it before shutting Windows down, because Windows may not properly unmount anything on its own.

---

### Post by hideri-chwan on 2018-07-29
Hello Tayl,

Thank you for the reply. Your instructions were neat and easy to understand, thank you. This is embarrassing but what does changing the ownership of the drive do?

Additional info: i can move file from the flash drive to the pc but not pc to flashdrive.

Hideri

---

### Post by hideri-chwan on 2018-07-29
Hello Impavidus,

Other flash drive's does automatically mount but I noticed that when the flashdo drive is 16 gb or higher, it doesn't mount automatically. So I mount them manually. 

Thanks for the reminder but I'm sure that the usb is not damaged. I always make sure to unmount them correctly.

Regards,

Hideri

---

### Post by hideri-chwan on 2018-07-29
Hi Yancek,

I'm sorry, your reply was Greek for me. I'll be sure to study on the points you pointed.

Hideri

---

### Post by Impavidus on 2018-07-30
Can you plug the drive in, run the **mount** command and show us the line relating to the usb drive? That will tell how it got mounted. Also run```
ls -l /path/to/mountpoint
```and show the output. Substitute the correct path.

There are two possible problems. One is that the drive was mounted read-only, in which case nobody (not even root) can write to the drive to create, delete or modify files or directories. That may happen when the filesystem is damaged or Linux doesn't know how to deal with it. The other possibility is that it was mounted read-write, but permissions were set such that only root can write to the drive. That may happen when you use the root user to mount the drive manually.

---

### Post by hideri-chwan on 2018-08-10
Hello Impavidus,

I tried running the command that you gave. These are the results:

      brw-rw---- 1 root disk 8, 17 Aug 11 10:24 /dev/sdb1

      /media/flashdrive:
      total 2246904
      -rwxr-xr-x 1 root root 45833414 Jun 26 21:27 (file name)
      -drxxr-xr-x 5 root root 8192 Aug 12 20:16 (file name)
       .
       .
       .

I hope this helps in solving the problem.
Thank you for your time.

Hideri

---

### Post by Impavidus on 2018-08-11
That's not the output from the mount command. When I run mount with an automatically mounted usb drive attached, I get (amongst others) this line:```
$ mount
...
/dev/sdb1 on /media/username/KINGSTON type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

```which shows it's mounted read-write, but when errors occur it's automatically remounted read-only.

I do see however that your flash drive is not mounted at it the normal location and it's owned by root. How do you mount it? What filesystem is on it? When you mount manually, you may have to set uid, gid, fmask and/or dmask.

---

### Post by hideri-chwan on 2018-08-24
When i mount i use this command

sudo mount /dev/sdb1 /media/flashdrive

---

### Post by Impavidus on 2018-08-25
That mounts the usb drive with only root access. You can try to set the correct user ID when mounting the usb drive:```
sudo mount -o uid=1000 /dev/sdb1 /media/flashdrive
```That's assuming you have user ID 1000, which would be the normal case for the first user of an Ubuntu system.

Or you can set the umask so that all users have read and write permissions:```
sudo mount -o fmask=0111,dmask=0000 /dev/sdb1 /media/flashdrive
```That gives read, write and execute permissions to all users on all directories, but only read and write permissions on the ordinary files.

Why you can't mount this usb drive by simply plugging it in and relying on the automatic features while you can rely on them for smaller drives, I don't know. Maybe it has something to do with the file system. You still haven't told us what file system is on the drive, but most commonly, smaller usb drives use fat32, large ones use ntfs.

---

### Post by hideri-chwan on 2018-08-25
hello Impavidus,

thank so much for your patience. i tried running the code you gave and it worked well. i can copy files to the usb now. thank you very much. also, im sorry if this is late but the file system of my usb is fat32. i tried the other usb and they are mounted automatically. its just this usb that is needed to be mounted manually.

once again, thank you for your help.

sincerely,
Hideri

---

