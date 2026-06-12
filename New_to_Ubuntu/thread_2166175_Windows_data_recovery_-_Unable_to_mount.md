---
title: "Windows data recovery - Unable to mount"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by alind2 on 2013-08-08
Dear All!
This is my first thread here, I hope that I will get the required assistance.

Last night and for no apparent reason, my laptop couldn't start. I tried all possible methods and it was always going back to the black screen with the cursor. 
My laptop is Windows 7 Home Premium, X64 - AMD A8. The problem appears to be either with corrupted files or faulty hard drive. The only big issue is that I need some data (few GBs) very badly.

Although the reason is not very clear, I think that Automate 9 contributed to the problem + too many big downloads without any disk Defragmentation. I know it was a very bad idea not to backup earlier, but I need to deal with the problem now.

As I am writing this post, I am running chkdsk /r on my harddrive from a different computer as I couldn't open it as external hard drive. The process will probably take a little while. Thus, I thought sharing it with you could help me save sometime if the chkdsk doesn't work.

I tried to solve the problem with the amazing Ubuntu. I am seriously thinking of converting my system afterwards. Anyways, I plugged the live USB to the laptop, and was able to boot up with "try mode". The hard disk appears, but is not accessible. When I access it from the drive tool, I can see three partitions. I can access two, one is system files or so and the other is the recovery but can't access the big part which has my data. 8 sectors out of 21 are determined as bad and this is bad indicator, however the harddrive passes all the SMART tests unless N/A.

If I try to open it from the computer window, first I get this:
```
Opening "GB Hard Disk: TI106412W0C"
You can stop this operation by clicking cancel.

```

and then I get this error:
```
Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

If I try to open it from the same computer window, but from the left panel, it takes minute or so and then I directly get:

```

Unable to mount TI106412W0C

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

I tried to force mount but got into this error:
```
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda2 /media/PRELOAD -o force

ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ubuntu@ubuntu:~$ 

```

Additional info:

With > mount:
```
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

With > sudo fdisk -l:
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes

255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeeda3836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2         3074048  1222303743   609614848    7  HPFS/NTFS/exFAT
/dev/sda3      1222303744  1250260991    13978624   17  Hidden HPFS/NTFS

Disk /dev/sdb: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15633407     7816688    b  W95 FAT32

```


Any help is really appreciated.
All best//
AliND

---

### Post by Cheesemill on 2013-08-08
Have you done as the error message asked and run *chkdsk /f* on the drive from Windows?

---

### Post by alind2 on 2013-08-08
Hi Cheesemill+

Yeah I am doing it now, but I started directly with *[FONT=Thread-00000488-Id-00000080]/r[/FONT]* trying to recover the bad sectors as indicated by Ubuntu. But it has been more than hour and a half already and I think it is going to take some more. Maybe, I should used *[FONT=Thread-00000488-Id-00000080]/f[/FONT]* as indicated by the error message, but I just thought a repair could be better than fix. Hopefully, it is not another mistake!

Kindly note that on my laptop, there was no way to pass the black screen except in the full recovery case; thus, I am doing it now from another PC.

Thanks\\
AliND

---

### Post by Mark Phelps on 2013-08-08
Unfortunately, there are no NTFS repair tools that work in Linux to the degree that the Windows tools work in Windows.  CHKDSK is still the NTFS repair tool of choice.

Also, while some of us CAN give you advice on Win7 problems, you would really do better posting on a Win7 forum -- suggest sevenforums.com, as they have tutorials about fixing these kinds of problems.

---

### Post by alind2 on 2013-08-09
Dear Mark,
Many - many thanks for your suggestions. I am sorry I couldn't reply earlier as I was offline one+ hour after my last post. I think you are totally right, however, Ubuntu was very helpful to let me know that I had bad sectors and it was also suggesting the solution :KS

The *chkdsk /r*, which was running when I posted the first thread, took considerable time (6+ hours) but everything finally worked like a charm. I am writing this post using my laptop (Windows) now.

I am really glad that this problem happened, so that I could know about Ubuntu. I always thought Linux is very technical and not user friendly, but God - the interface is unbelievably good, ways better than the others.

For future users, if the same problem happens to you, follow these steps and your problem will be probably solved.

> 1- Get a harddisk adapter (you can borrow if a friend has one, but anyways it is cheap).
2- Take your harddisk off your laptop (very easy) and connect it to another computer or laptop (follow the instructions on the adapter; usually you connect it to the computer and then turn the power on). Note that a PC with good specifications is always preferred as it will save time; besides, a fast USB port is better for the same reason.
3- The computer should recognize it immediately or in few seconds, but probably you won't be able to access it from the "computer window" or so. Try it, if it asks you to format, of course click no. The important thing is that you lookup the letter assigned to the drive. Suppose it is E; then:
4- Open the command window (in Windows seven: type "cmd" in the Start box), and type [FONT=arial]*[COLOR=#444444]**CHKDSK E**[/COLOR][COLOR=#444444]: **/r  **[/COLOR]*[COLOR=#444444](note that *r* stands for repair, *f* for fix and so on. I used *r* because I had 8 bad sectors as it was indicated by Ubuntu, but Ubuntu was advising to run /*f*. /*f *might also work but I didn't try it as my problem was solved with the /*r* command).
[/COLOR][/FONT][FONT=arial]5- Now, you just wait! It will probably take a while to finish depending on your harddrive size and the PC you are working with. In my case (640 GB hard drive), and as I stated above, it took 6+ hours.
6- Once it finishes, you will be able to see the contents of your harddrive. However, you might not be able to access a user's folder. If this is the case, you can take control of the folder (requires some work - you can look it up over the internet) or just safely remove (disconnect) the harddrive and plug it back into your computer. Everything should be working perfectly now.[/FONT][FONT=arial]

Hope this helps someone, but as a very beginner advise, Check Ubuntu. It is simply amazing.

All Best//
AliND[/FONT]

---

