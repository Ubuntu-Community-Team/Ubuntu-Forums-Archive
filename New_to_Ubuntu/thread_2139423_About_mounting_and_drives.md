---
title: "About mounting and drives"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by pianist16 on 2013-04-26
Hello there, I'm new to linux and running xubuntu on my Desktop.
So, I had two HDs, the first with Windows and Xubuntu dual boot, working. The second I have only for data and backup.
I had the two working normally til yesterday, but everytime I wanted to use the second one I had to right click > mount.
I googled for a solution and found about a program, ntfs-config. I installed it, but after trying dealing with it apparently I messed up something here.

Now my HD isn't appearing as it was before, he's in the /media/user/ folder. How I can move it back to where it was?

---

### Post by DuckHook on 2013-04-26
Just what, exactly, did you do? To help us help you, you must provide precise steps that you took in as much detail as you can recall. If you cannot recall exact steps, then provide link to the instructions that you followed. Also, you must define what you consider "working normal" and "back to where it was", as these phrases are meaningless to anyone but you.

---

### Post by oldfred on 2013-04-27
The NTFS config program has not been maintained so it often does not add good parameters or mount by UUID.

And the default mount from Nautilus has changed from a system only mount to a system/user mount or from /media/folder to /media/fred/folder.

Often best just to do it manually by editing fstab. You can use the template and instructions from this:
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

### Post by pianist16 on 2013-04-27
Ok, I understand I haven't provided enough details. So, when I open file manager, on the left of the screen, I can see the folders and drives which I can acess (Like "user", "Desktop", "File System") and along with them there are the HDs and removable drives, like "123GB Volume" (my windows partition), "Data" (which is my other HD, labelled Data) and any pendrive I plugged in there.

My first issue is that whenever I had to acess that "Data" drive I had to right click > mount it. Beyond that little thing, everything was fine. Them I searched a bit and found about that NTFS config program. Installed it and he shows a screen with 2 checkbox options and displayed my drives bellow, to check it or not. I didn't understand it quietly well, so I just tried checking what supposed to be right.
After I did it, my "Data", which was previously being show along by the left in File Manager, has gone. After looking for it, I realized that it was in /media/user/Data/. It's ok, I still can browse the files there, but I can't save anything there (at least not without root, which is annoying). I tried unchecking the boxes in NTFS config program, but nothing happened. I also noticed, whenever I try booting Xubuntu, it displays an error about an error when trying to mount something, specifically, /dev/sdb2

So, my question is, how I can make my Data HD appears again in the left of the File Manager screen, like if it was a pendrive plugged in? I already read something about editing this fstab file, but I'm afraid of trying it by my own and messing things up even more. Is there a chance on anyone guiding me through that?

I'm posting the result of fdisk -l here, because I think it may be helpful:

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00023017


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953523711   976760832    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bf03e03


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   239812509   119802831    7  HPFS/NTFS/exFAT
/dev/sdb3       239812606   488396799   124292097    5  Extended
/dev/sdb5       480012288   488396799     4192256   82  Linux swap / Solaris
/dev/sdb6       239812608   480012287   120099840   83  Linux


Partition table entries are not in disk order


Disk /dev/sdc: 8016 MB, 8016363520 bytes
154 heads, 11 sectors/track, 9242 cylinders, total 15656960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32    15656959     7828464    b  W95 FAT32




The /dev/sda1 is the Data HD.

---

### Post by Bashing-om on 2013-04-27
pianist16; Hi !

Let's see if we can make heads or tails of of this;
Post the output of terminal codes:
```
sudo blkid ##to list the UUID identifiers
ls -la /media/pianist16 ##(if that is your "username") - to see possible mount points
ls -la /mnt/pianist16
cat/etc/fstab ##to see the mounting structure
mount ##to see what is actually mounted
```
[INDENT=2]so a tale is told
[/INDENT]

---

### Post by pianist16 on 2013-04-27
Hello Bashing-on, thanks for your time! Here it is:[COLOR=#000000][FONT=Ubuntu Mono]

sudo blkid
[/FONT][/COLOR]
> /dev/sda1: LABEL="Dados" UUID="1AE44D4E7FAC3291" TYPE="ntfs" /dev/sdb1: LABEL="Reservado pelo Sistema" UUID="20EC0DE2EC0DB358" TYPE="ntfs" 
/dev/sdb2: UUID="FED69132D690EBE1" TYPE="ntfs" 
/dev/sdb6: UUID="85152222-dd58-479d-aaaa-0c24b4084ff6" TYPE="ext4" 
/dev/sdc1: LABEL="HAUCK" UUID="107F-5E9A" TYPE="vfat" 

ls -la /media/hauck

> total 16drwxr-x---+ 4 root  root  4096 Apr 27 14:24 .
drwxr-xr-x  5 root  root  4096 Apr 26 19:09 ..
dr-xr-xr-x  1 root  root  4096 Apr 24 21:17 Dados
drwx------  4 hauck hauck 4096 Dec 31  1969 HAUCK


ls -la /mnt/hauck

> ls: cannot access /mnt/hauck: No such file or directory


ls -la /mnt/ (since ls -la /mnt/hauck apparently not worked, don't know if that would help)

> total 8
drwxr-xr-x  2 root root 4096 Oct  9  2012 .
drwxr-xr-x 24 root root 4096 Apr 11 12:52 ..


cat /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


#Entry for /dev/sdb6 :
UUID=85152222-dd58-479d-aaaa-0c24b4084ff6	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=20EC0DE2EC0DB358	/media/Reservado_pelo_Sistema	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda1 :
UUID=1AE44D4E7FAC3291	/media/hauck/Dados	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
#Entry for /dev/sdb2 :
UUID=FED69132D690EBE1	/media/sdb2	ntfs	defaults,nls=utf8,umask=0222	00
/dev/mapper/cryptswap1	none	swap	sw	0	0


#UUID=ba871abd-fe9e-4c7f-abfe-121fee469da1	none	swap	sw	0	0




mount

> /dev/sdb6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sdb1 on /media/Reservado_pelo_Sistema type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/hauck/Dados type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/hauck/.Private on /home/hauck type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=b5927faeaac01fb1,ecryptfs_fnek_sig=2f34d9b482b72adc)
gvfsd-fuse on /run/user/hauck/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=hauck)
/dev/sdc1 on /media/hauck/HAUCK type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)




---

### Post by Bashing-om on 2013-04-27
pianist16;

Some observations:
1. It is generally not recommended to auto mount the Windows' operating system (sda1); easily corrupted.
2. NTFS partition read/write from ubuntu is better is utilize "ntfs-3g".
3. Your home and swap partitions are encrypted. I have no experience or knowledge of such and as such can not help you there.

These links will provide guidance on how to set up /etc/fstab to properly mount the ntfs partitions with the permissions and access as you may desire:
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)

I believe if you follow the guides and set up /etc/fstab accordingly, will resolve the problems.
Before editing any file, MAKE a backup of the file first, for what ever might perchance !

Once you have done your homework on the above, if there are any questions or doubts; By all means ask ! ->[INDENT=2]
we are here to help

[/INDENT]

---

### Post by pianist16 on 2013-04-27
Bashing-om, I really appreciated your help. After some reading, I could let the things the way I wanted. Now my second HD is being displayed in "Places" and always mounted.
Just to mention it, in the fstab: For the permissions to read/write, I changed from "ntfs" to "ntfs-3g" and changing the Options of it to auto,users,permissions.And about being shown in Places, not sure about that but the mount point was /media/hauck/Dados. I changed it to /media/Dados and not it's being shown in both Desktop and Places, just as I wanted.

But I still have a problem here. Whenever I boot Xubuntu, it usually keeps loading forever, then I have to ctrl+alt+del it, and when it reebots, the Xubuntu logo show up and appears a message about couldn't mounting /dev/sdb2. That's not being a trouble at all, but I guess isn't supposed to work like that, and I think it can get worse if I let it this way.

That error message is about what you told about home and swap partitions being encrypted? Any ideas?


[COLOR=#000000]EDIT:
Well, I was looking further into it, my other partition in my primary HD with Windows has been recently formatted (ntfs), and is being displayed as "123GB Volume", working and mounted on [/COLOR]/media/hauck/439C84FD7C3235B2  (if I'm not mistaken, is that his uuid, right?).
Running blkid:
> /dev/sda1: LABEL="Dados" UUID="1AE44D4E7FAC3291" TYPE="ntfs" 
/dev/sdb1: LABEL="Reservado pelo Sistema" UUID="20EC0DE2EC0DB358" TYPE="ntfs" 
/dev/sdb2: UUID="439C84FD7C3235B2" TYPE="ntfs" 
/dev/sdb6: UUID="85152222-dd58-479d-aaaa-0c24b4084ff6" TYPE="ext4" 


Right, everything seems fine until now, but if I check my fstab file:

cat /etc/fstab:

> #Entry for /dev/sdb6 :UUID=85152222-dd58-479d-aaaa-0c24b4084ff6    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb1 :
UUID=20EC0DE2EC0DB358    /media/Reservado_pelo_Sistema    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda1 :
UUID=1AE44D4E7FAC3291    /media/Dados    ntfs-3g    auto,users,permissions    0    0
#Entry for /dev/sdb2 :
UUID=FED69132D690EBE1    /media/sdb2    ntfs    defaults,nls=utf8,umask=0222    00
/dev/mapper/cryptswap1    none    swap    sw    0    0


#UUID=ba871abd-fe9e-4c7f-abfe-121fee469da1    none    swap    sw    0    0


In fstab the /dev/sdb2 has a different UUID and a diferent mountpoint, and has something about swap and stuff.. I think there's something wrong here. I thought about changing something there, but I think it's better to hear your opinion first.

---

### Post by DuckHook on 2013-04-27
Wait for Bashing-om to confirm first, but it looks to me like you need to change your UUID for sdb2 to reflect the actual/proper UUID outputted by blkid. That is: 439C84FD7C3235B2
Not FED69132D690EBE1

You must also make sure to leave at least one space between the two "0" at the end of the line. It should be 0     0
Not 00

Swap is fine. I take it that you have an encrypted swap partition? This is a good practice.

Your boot is hanging because it is looking for and trying to mount a UUID that does not exist. I suspect that if you correct the UUID entry in fstab, the boot hang will also go away.

Again, wait for confirmation from Bashing-om before proceeding with these changes.

---

### Post by Bashing-om on 2013-04-27
@          pianist16; 
Something does smell in DenMark ( as a saying goes).
Any time I have a conflict in UUIDs I want double confirmation as to what the system is seeing. Once more and with feeling, lets see the updated out put of "blkid" and, and :
```
 sudo blkid
ls -l /dev/disk/by-uuid/
cat /etc/fstab
``` so all data is readably readable -> consolidated to one place for reference.

Again I must stress that it is not a good idea to automount the Windows' operating system. Much safer if you must access Windows' operating system files from 'buntu, to mount that partition manually as on demand. ( I am not talking about a common data partition)

@ DuckHook;
 I appreciate the confidence, Looks like something in the OP's system has changed from that of the original posted info.
[INDENT]'buntu, where there is a will there is a way


[/INDENT]

---

### Post by pianist16 on 2013-04-28
Okay, here it is:

> /dev/sda1: LABEL="Dados" UUID="1AE44D4E7FAC3291" TYPE="ntfs" /dev/sdb1: LABEL="Reservado pelo Sistema" UUID="20EC0DE2EC0DB358" TYPE="ntfs" 
/dev/sdb2: UUID="439C84FD7C3235B2" TYPE="ntfs" 
/dev/sdb6: UUID="85152222-dd58-479d-aaaa-0c24b4084ff6" TYPE="ext4" 


ls -l /dev/disk/by-uuid/:

> total 0lrwxrwxrwx 1 root root 10 Apr 28 18:17 1AE44D4E7FAC3291 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 28 18:17 20EC0DE2EC0DB358 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Apr 28 18:17 439C84FD7C3235B2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Apr 28 18:17 85152222-dd58-479d-aaaa-0c24b4084ff6 -> ../../sdb6


cat /etc/fstab:

> #Entry for /dev/sdb6 :UUID=85152222-dd58-479d-aaaa-0c24b4084ff6	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=20EC0DE2EC0DB358	/media/Reservado_pelo_Sistema	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda1 :
UUID=1AE44D4E7FAC3291	/media/Dados	ntfs-3g	auto,users,permissions	0	0
#Entry for /dev/sdb2 :
UUID=FED69132D690EBE1	/media/sdb2	ntfs	defaults,nls=utf8,umask=0222	00
/dev/mapper/cryptswap1	none	swap	sw	0	0


#UUID=ba871abd-fe9e-4c7f-abfe-121fee469da1	none	swap	sw	0	0


To clarify things, I have two HDs, the first one has two partitions with Xubuntu and Windows 8, and second one is just for data (called Dados there). Is that data drive I want to automount at first. Since Windows 8 completely sucks, I just formatted his partition in my primary HD (still with ntfs, intend to install Windows 7 there afterwards), and it is this one unlabelled in the blkid.
So, the Data drive is automatically mounting now, I just have to deal with that little mess with in the fstab file. According to my understanding, it's confusing the old windows partition with the swap partition. Is that right?

---

### Post by Bashing-om on 2013-04-28
pianist16;

Got to straighten up your fstab to match the mount points that are established in the "/media" directory.
sda1:should be:
> UUID=1AE44D4E7FAC3291    /media/hauck/Dados    ntfs-3g    auto,users,permissions    0    0

sdb1 == Window's operating system and should have the mount point of "/media/hauck/HAUCK" not /media/Reservado_pelo_Sistema    .
If you insist on mounting the Windows OS in ubuntu - NOT a good idea then make it's mounting access rights as you have it for the sda1 partition.
> UUID=20EC0DE2EC0DB358    /media/hauck/HAUCK    ntfs-3g    auto,users,permissions    0    0

sdb2: now;FED69132D690EBE1 is incorrect and should be ;439C84FD7C3235B2. There is no valid mount point for this partition and one must be made:
```
sudo mkdir /media/hauck/data
``` such that the fstab line beomes:
> UUID=439C84FD7C3235B2    /media/hauck/data    ntfs-3g    auto,users,permissions    0    0

Remember ---> make a copy of the current /etc/fstab file prior to making your corrections to this file.
```
gksudo thunar /etc/fstab
``` IF thunar is the editor you are using.
Then save that edited file prior to exiting.
In terminal run terminal code:
```
mount -a
``` if there is no result from the mount command that is a good thing, means all is well !
Else: post the errors that are generated.

This I expect will fix you up properly; mounting 3 NTFS partitions, /home and a encrypted swap partitions(5 entries in /etc/fstab file).[INDENT=3]
all good now ?

[/INDENT]
[INDENT]
[/INDENT]

---

### Post by pianist16 on 2013-04-28
Okay, everything seems fine and working now! I think I'm even starting to understand all that thing a little better.

Just get me rid of a curiosity: why changing the sda1 (which was working normally) from /media/Dados to /media/hauck/Dados? Also with the other drives. Is there a point behind that?

---

### Post by Bashing-om on 2013-04-28
pianist16;
Let me see if I can explain - an old adage is:if you can not teach you do not understand --
do in terminal:
```
ls -la /media
ls -la /media/hauck
la -la /media/hauck/Dados

```
Now mount the Dados partition and do:
```
ls -la /media/hauck/Dados
```

Thus ...a partition is a device that contains a file system. In order to access said file system one has to attach that file system to ubuntu's file system. This is done with what is called a mount point (here: /media/hauck/Dados) and the device (sda1 or sdb2 or whatever) ,that is a partition, is related to that mount point through a File System TABle (gvfs-fuse-daemon is another way too).

With that said, the mount point can be in any directory one chooses, but, later versions of 'buntu are making the "default" location of these mount points in /media/<username>/<descriptive_title>. In this instance I am following that standard. Mounting in media has the advantage that the file manager 'sees' the mount point and through .gvfs can do the mounting in the GUI.[INDENT=2]
clear as mud ??

[/INDENT]

---

### Post by pianist16 on 2013-04-28
Understood! Thank you very much for your help and DuckHook too!

---

### Post by DuckHook on 2013-04-28
> **Bashing-om said:**
> clear as mud ??

Linux is permanently, endlessly, eternally and absolutely as clear as mud.:frown:

---

### Post by Bashing-om on 2013-04-28
Yeah ! And that keeps me entertained. I will never know all I want to know about this fascinating Operating System. Very thankful to those thousands who have provided documentation.
Now in my old age, if I only had an application to apply all this effort too - believe me, I think about that a lot ![INDENT=2]
still learning even after all these years
[/INDENT]

@         pianist16;

As you are content with the solution, please mark this thread "solved":
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

---

### Post by Morbius1 on 2013-04-29
It's unlikely you will change anything at this point since it's taken you so long to get to this point but in case others stumble upon this topic there are some fundamental problems with this setup:

_ * [1] Based on the output of blkid it appears that:*_
UUID="1AE44D4E7FAC3291" = The "Data" partition ( i.e., sda1 )
UUID="20EC0DE2EC0DB358" = The "System Reserved" partition ( i.e., sdb1 ) not the Windows OS partition
UUID="439C84FD7C3235B2" = The Windows OS partition ( i.e., sdb2 )

_ * [2] If you add entries for partitions in fstab avoid the /media/$USER directory.*_

You have already posted the reason why:
> ls -la /media/hauck
total 16drwxr-x---+ 4 root root 4096 Apr 27 14:24 .
At first glance that appears to only allow root access to anything contained withing that directory. But you will notice that at the end of the permissions part of the line is a "+". That indicates that Access Control Lists are in control of who can access folder. If you run the following command you will see that only "hauck" has access to anything past that point in the path:
```
getfacl -t /media/hauck
```
** Have multiple users on your system and they will not be able to gain access.
** Try to share folders on that partition across the network using Samba and you will need to modify a few things because only "hauck" will be permitted access.

Your original instinct was correct - these should be placed in /media directly as in /media/Data.... or in /mnt or just about anywhere else.

_ * [3] But by far the most dangerous thing you are doing is using the "permissions" option.*_

The standard way one mounts an ntfs partition is to create a "view" of the partition such that it appears to have Linux ownership and permissions bit's when in fact they do not. The "permissions" option breaks this by allowing Linux the ability to change the attributes of files within NTFS itself. One can do that but it requires more than just adding a option to fstab since "maps" must be created within Linux and Windows that converts Linux users to Windows users. It's not something that one should do without serious consideration and should certainly be avoided in a dual boot situation.

If you do noting else I would highly recommend you remove the "permissions" option from your fstab entries. We in this forum should not be in the business of repairing, restoring, and offering assistance to reinstall Windows.

---

### Post by Bashing-om on 2013-04-29
@  		Morbius1;

Appreciate your input and instruction, I regret in my haste to reach a solution I did not properly follow through. For future consideration I take these conclusions to heart.
[INDENT=2]
garbage in - garbage out

[/INDENT]

---

### Post by DuckHook on 2013-04-29
> **Morbius1 said:**
> ...in case others stumble upon this topic there  are some fundamental problems with this setup...

It's always worthwhile reading what you have to say. Thanks for teaching me many new things today.

---

### Post by pianist16 on 2013-04-29
> **Morbius1 said:**
> It's unlikely you will change anything at this point since it's taken you so long to get to this point... 

I actually haven't changed the mount point after that since Bashing-om said it was only a matter of standards and I was afraid of messing things up there again. Never thought I was doing the right thing not changing it, though! :p

I will remove the "permissions" option in the fstab, then. Thank you for the info, Morbius1.

---

