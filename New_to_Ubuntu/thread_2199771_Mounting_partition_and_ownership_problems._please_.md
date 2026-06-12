---
title: "Mounting partition and ownership problems. please help!"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by hornbutu on 2014-01-15
Good day everyone!

I"m having issues taking ownership of a mounted partition and network drive. I have edited my fstab to automount them when I reboot and it is working for me. The problem is, is that I cannot unmount them it will not let me citing that "only system administrators have permission to do this". I checked in my user settings and I am indeed an admin. When I did this with my last ubuntu based system (lxle 12.04 based off lubuntu 12.04 LTS) I was able to do this with no problem. Ive now moved on to lxle 12.04.4 and the issue arose. Not sure if thats the cause or  if its something else Ive affected while tinkering. My "storage" (sda2) mounts to /media/data, and my network drive mounts to /media/wdtv.

I was able to take ownership before by doing this:
"[COLOR=#666666][FONT=Lucida Grande]/media [/FONT][/COLOR][COLOR=#666666][FONT=Lucida Grande]and doing a ls -la[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]Second, do the following, replacing &#8220;yourPartition&#8221; with the name of the partition (e.g. /sdb1).[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]sudo chown -R **username**:**username** /yourPartition
sudo chmod -R 755 /yourPartition[/FONT][/COLOR]

Now it returns "will@toymaker:~$ sudo chown -R will:will /media/data
chown: invalid option -- '&#65533;'
Try `chown --help' for more information."


Regardless this is my fdisk -l
"will@toymaker:~$ sudo fdisk -l[sudo] password for will: 


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003bb21


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     8394751     4196352   82  Linux swap / Solaris
/dev/sda2       134221824   625141759   245459968    7  HPFS/NTFS/exFAT
/dev/sda3   *     8394752    71309311    31457280   83  Linux
/dev/sda4        71309312   134221823    31456256   83  Linux"

"will@toymaker:~$ sudo parted -l
[sudo] password for will: 
Model: ATA TOSHIBA MK3265GS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system     Flags
 1      1049kB  4298MB  4297MB  primary  linux-swap(v1)
 3      4298MB  36.5GB  32.2GB  primary  ext4            boot
 4      36.5GB  68.7GB  32.2GB  primary  ext4
 2      68.7GB  320GB   251GB   primary  ntfs"

my fstab:

"# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d207b797-8fd3-468b-a2db-66e9b7cef9e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=bc55089d-2519-4ee5-a780-353b2cd05538 none            swap    sw              0       0
//192.168.1.18/WDTVLIVEHUB /media/wdtv cifs auto,iocharset=utf8,uid=will,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
LABEL=storage /media/data ntfs defaults 0 0"

and this:
"will@toymaker:/media$ ls -la
total 20
drwxr-xr-x  6 root root  4096 Jan 15 12:33 .
drwxr-xr-x 24 root root  4096 Jan 14 20:02 ..
drwxr-x---  2 root root  4096 Jan 12 11:59 apt
drwxr-xr-x  2 root root  4096 Jan 10 04:16 cdrom
drwxrwxrwx  1 root root  4096 Jan 15 16:08 data
drwxrwxrwx  1 will users    0 Jan 13 20:51 wdtv
will@toymaker:/media$ "

Anyone have any suggestions? I want to own my sda2 and my network storage. 

Thank you!

edit- these are the places that allowed me to figure this out before:
[http://amazingrando.wordpress.com/2007/04/05/changing-permissions-of-a-partition-its-easy/](http://amazingrando.wordpress.com/2007/04/05/changing-permissions-of-a-partition-its-easy/)
[http://ubuntuforums.org/showthread.php?t=2080463&page=2](http://ubuntuforums.org/showthread.php?t=2080463&page=2)
[http://ubuntuforums.org/showthread.php?t=1806455](http://ubuntuforums.org/showthread.php?t=1806455)

---

### Post by oldfred on 2014-01-15
Do not know about network mounts.

But you cannot change NTFS. All ownership & permissions are set with your fstab as defaults, since NTFS does not support ownership & permissions.

       Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

 
    

Also:
 I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod -R 777  /mnt/data

---

### Post by chkneater on 2014-01-16
Could you log out and log back in as somone else that can unmount them?  I know that's kind of a duct tape way but...

---

### Post by vanadium on 2014-01-16
Add the "user" or "users" option to the line in /etc/fstab. With "user", only the same user that mounted the volume can unmount it again. With "users", any user can unmount a volume, regardless of who mounted it.

---

