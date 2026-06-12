---
title: "Can't figure out how to get ext4 data partition to read/write permanently"
date: 2015-01-11
forum: New to Ubuntu
---

### Post by android73 on 2015-01-11
Hi Everyone,

I have been working on this problem for a full day now checking all the previous posts regarding this subject but no luck, so thought I would seek help. Yesterday I installed Xubuntu(latest) alongside windows 7 in a dual boot scenario. Everything worked fine until I installed Steam and tried to stipulate where the games library would be. I had created a 40 GB logical drive partition for this purpose but it keeps telling its read only. Now thinking back to when I installed, I did specify something about using encryption, could this be causing a problem? Here are the steps I am taking and the results. 

I type in first in the emulator:

andrew@andrew-MS-7350:~$ sudo blkid
[sudo] password for andrew: 
/dev/sda1: LABEL="UUI" TYPE="vfat" 
/dev/sdb1: UUID="20483E3C483E1150" TYPE="ntfs" 
/dev/sdb5: LABEL="/" UUID="90f7daf4-5f4e-40aa-b97e-494780906d5c" TYPE="ext4" 
**/dev/sdb7: UUID="3dfe77cf-6f80-410e-8009-43a72bb71856" TYPE="ext4" **
/dev/sdc1: UUID="6C2CB25B2CB21FCE" TYPE="ntfs" 
/dev/sdd1: UUID="2A92BE8D53E0D596" TYPE="ntfs" 
andrew@andrew-MS-7350:~$ 

I have highlighted in bold the location of the drive.

Then I type this

andrew@andrew-MS-7350:~$ gksudo gedit /etc/fstab

Then I enter this:

andrew@andrew-MS-7350:~$ UUID=<3dfe77cf-6f80-410e-8009-43a72bb71856> /dev/sdb7 /media/3dfe77cf-6f80-410e-8009-43a72bb71856 ext4 defaults 0 2
bash: 3dfe77cf-6f80-410e-8009-43a72bb71856: No such file or directory
andrew@andrew-MS-7350:~$ 

Then I test:
sudo mount -a

there is no output after that command

So I finally try this as others have:

andrew@andrew-MS-7350:~$ sudo chown <andrew>:<andrew> /dev/sdb7 /media/3dfe77cf-6f80-410e-8009-43a72bb71856
bash: andrew: No such file or directory
andrew@andrew-MS-7350:~$ 


Now bear with me I am new to Linux and don't know what I am doing. But if I can't get my data partition to read/write then using Linux seems pointless. I never used to have this problem with the previous Ubuntu. I need it to be mounted once I boot to the desktop. Any help would be greatly appreciated!

aapeppin

---

### Post by sudodus on 2015-01-11
A line in **/etc/fstab** should be built like this

 ```
# <file system>                           <mount point>      <type>  <options>       <dump>  <pass>
```

where the <> symbols should not be there when you type in the real strings (see your entry for the root partition in your own file).
I have a separate data file, which has the following line in my fstab file

 ```
UUID=a4f3f4ba-3d5c-4e4f-8e1a-c2f0de792f81 /mnt/multimed-2     ext4    defaults         0       2
```

This will assume that the drive is always there. The system wants to mount the drive at boot.

If you have an external drive, that you do not always connect, the following line might be better

 ```
UUID=a4f3f4ba-3d5c-4e4f-8e1a-c2f0de792f81 /mnt/multimed-2     ext4    defaults,noauto  0       0
```

In order for it to work you must create the mount point (only once so not in fstab)
```

sudo mkdir -p /mnt/multimed-2
```

Of course, ***use your own UUID string instead of mine***, and select a mount point that you prefer (or use **/mnt/multimed-2**)

```
UUID=3dfe77cf-6f80-410e-8009-43a72bb71856
```

And then connect the drive manually.

---

### Post by efflandt on 2015-01-11
I do not understand what you are attempting to enter at the shell prompt after **gksu gedit /etc/fstab**, especially when not saying what you did in the gedit window.

To edit /etc/fstab you either need to edit it in the gedit window that pops up after you enter **gksu gedit /etc/fstab** (and you authenticate yourself) or another way to edit it within terminal or console would be **sudo nano /etc/fstab** (nothing is echoed while you enter your password blindly when sudo prompts for that). Make sure that whatever window you edit in is wide enough to not appear to (or actually) wordwrap long lines.

---

### Post by android73 on 2015-01-11
That's because i did not see a gedit window pop up, is this supposed to happen?

---

### Post by android73 on 2015-01-11
Ok did what you said and the gedit window came up. Now not sure what to do? I have never edited this before, sorry!:p

---

### Post by sudodus on 2015-01-11
Add a line into /etc/fstab according to my previous post (Post #2)

Edit: You may need to reboot to make it use the new content of /etc/fstab.

---

### Post by android73 on 2015-01-11
This is what I see now

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=90f7daf4-5f4e-40aa-b97e-494780906d5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
#UUID=cf768823-80ca-4cd6-ba0c-2e10b4c0ddef none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0







                                                                                               [ Read 12 lines ]
^G Get Help                       ^O WriteOut                       ^R Read File                      ^Y Prev Page                      ^K Cut Text                       ^C Cur Pos
^X Exit                           ^J Justify                        ^W Where Is                       ^V Next Page                      ^U UnCut Text                     ^T To Spell

---

### Post by android73 on 2015-01-11
ok done, how do I save the gedit and close out?

---

### Post by android73 on 2015-01-11
Well I ran the **sudo nano /etc/fstab **command and amended the file with the line of code you told me to (UUID=3dfe77cf-6f80-410e-8009-43a72bb71856 /mnt/multimed-2     ext4    defaults         0       2). ****, i hit ctrl X to save, then I rebooted. Now the drive icon has disappeared all totgether from the desktop, and doesnt show up in nautilus.

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=90f7daf4-5f4e-40aa-b97e-494780906d5c /               ext4    errors=remoun$
# swap was on /dev/sdb6 during installation
#UUID=cf768823-80ca-4cd6-ba0c-2e10b4c0ddef none            swap    sw          $
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=3dfe77cf-6f80-410e-8009-43a72bb71856 /mnt/multimed-2     ext4    defaults $






                               [ Read 16 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell


I'm terribly confused.

---

### Post by android73 on 2015-01-11
Here is what I see when I search for all partitions:

andrew@andrew-MS-7350:~$ sudo blkid
[sudo] password for andrew: 
/dev/sda1: LABEL="UUI" TYPE="vfat" 
/dev/sdb1: UUID="20483E3C483E1150" TYPE="ntfs" 
/dev/sdb5: LABEL="/" UUID="90f7daf4-5f4e-40aa-b97e-494780906d5c" TYPE="ext4" 
/dev/sdb7: UUID="3dfe77cf-6f80-410e-8009-43a72bb71856" TYPE="ext4" 
/dev/sdc1: UUID="6C2CB25B2CB21FCE" TYPE="ntfs" 
/dev/sdd1: UUID="2A92BE8D53E0D596" TYPE="ntfs" 
andrew@andrew-MS-7350:~$ 


The sdb7 partition shows up here?

---

### Post by android73 on 2015-01-11
Now if i type in sudo gparted and look at the partition table, sdb7 is there and the mount point is stated as /mnt/multimed-2

---

### Post by kpatz on 2015-01-11
It's mounted, so you won't see it as a separate "drive" in Nautilus.  Look in /mnt/multimed-2 and see if the files in that partition are there.

Also, post the output of "mount" as well as "df".

---

### Post by corneldardenjr-y on 2015-01-12
Did you change permissions for the partition?

---

### Post by sudodus on 2015-01-12
> **kpatz said:**
> It's mounted, so you won't see it as a separate "drive" in Nautilus.  Look in /mnt/multimed-2 and see if the files in that partition are there.

Also, post the output of "mount" as well as "df".
+1

Please run these commands and post the output

```
mount
```

```
df
```

-o-

And we think that you can browse to /mnt/multimed-2 (with your file browser) and see the partition. Please try and report the result :-)

---

### Post by android73 on 2015-01-12
Hi, thanks for the response. This is frustrating, i got on the xubuntu live chat support for help and they told me I needed to revert the changes to the fstab and that the problem was with permissions and chown command?

---

### Post by android73 on 2015-01-12
```
andrew@andrew-MS-7350:~$ mount
/dev/sdc5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sdc7 on /mnt/multimed-2 type ext4 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/home/andrew/.Private on /home/andrew type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=f5791697ebf1ca50,ecryptfs_fnek_sig=184f640aad000a62)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=andrew)
/dev/sdb1 on /media/andrew/UUI type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda1 on /media/andrew/UUI1 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
andrew@andrew-MS-7350:~$ 


andrew@andrew-MS-7350:~$ df
Filesystem            1K-blocks    Used Available Use% Mounted on
/dev/sdc5              10189728 5466108   4182972  57% /
none                          4       0         4   0% /sys/fs/cgroup
udev                    4073068       8   4073060   1% /dev
tmpfs                    817660    1448    816212   1% /run
none                       5120       0      5120   0% /run/lock
none                    4088284   24920   4063364   1% /run/shm
none                     102400      28    102372   1% /run/user
/dev/sdc7              41763096   49032  39569552   1% /mnt/multimed-2
/home/andrew/.Private  10189728 5466108   4182972  57% /home/andrew
/dev/sdb1              28558100       4  27025636   1% /media/andrew/UUI
/dev/sda1             292977592       8 277332768   1% /media/andrew/UUI1
andrew@andrew-MS-7350:~$
```

---

### Post by sudodus on 2015-01-12
The partition /dev/sdc7 is mounted on /mnt/multimed-2 with read and write permissions

```
/dev/sdc7 on /mnt/multimed-2 type ext4 (rw)
```

This is good news (and expected from your earlier posts). So you succeeded in mounting it via fstab :-)

In order to check the permissions you run the long listing command

```
ls -l /mnt
``` and

```
ls -l /mnt/multimed-2
```

Now change directory to this partition

```
cd /mnt/multimed-2
```

Check that you are 'there' with

```
pwd
```

Maybe you want some subdirectories for example content-wise:{Documents, Pictures, Music, Video} or name-wise:{Anne, Burt, Carla, David ...} . Make those directories and give them the permissions you want. You have an ext4 partition, which gives you full flexibility to select permissions.

example
```
sudo mkdir Documents
```

If you want all users to have read,write and execute permissions

```
sudo chmod ugo+rwx directory-name
```

The directory and its subdirectories are owned by root alias superuser. You can change the owner of a particular directory

example:
```
sudo chown anne:root /mnt/multimed-2/Anne
```

which means that it is owned by Anne but belongs to the root (superuser) group.

You find tutorials about ***linux file permissions ***and*** ownership*** if you browse the internet. Select one that suits you, and read it for more details.

---

### Post by android73 on 2015-01-13
Hey thanks, I will give this a try and report back!

Andrew

---

