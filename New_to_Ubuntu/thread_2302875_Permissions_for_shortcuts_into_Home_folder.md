---
title: "Permissions for shortcuts into Home folder"
date: 2015-11-14
forum: New to Ubuntu
---

### Post by Alan_Dean on 2015-11-14
Because I could not Get Plex to access my external hard drives (Seagate drive called "Music" and Transcend drive called "Multimedia") I changed the permissions thus:


sudo gpasswd -a plex plugdev
sudo gpasswd -a plex root
sudo gpasswd -a plex sudo
sudo gpasswd -a plex alan
sudo gpasswd -a alan plex 


Created folders in the Home directory with the same names as the two external drives named "Music" and "Multimedia"


Changed fstab so that they both are mounted on bootup - which they do


Now the Seagate drive called "Music" works well and is accessed by Plex and the permissions tab shows that alan (that's me) has permissions. The permissions for the Transcend drive called "Multimedia" is greyed out and is accessible by root and cannot be accessed by Plex. 


Any ideas so that I can access "Multimedia" from the Home folder. All the folders of both drives in the Home directory open OK and the music files play ok. 


Thanks
Alan

---

### Post by TheFu on 2015-11-14
Assuming I understand the issue....
Symbolic links do not have any permissions of their own.

I've been running PlexMS for a few years and I'm extremely familiar with Unix permissions.
Please post the output from:
```
mount
df  -h
cat /etc/fstab
ls -al  /path/to/the/Music  /path/to/the/Multimedia
```

And,  please use [code-tags]("http://blog.jdpfu.com/code_tags") so things line up correctly. The output is too hard to read otherwise.

---

### Post by Alan_Dean on 2015-11-15
Thanks for the reply. I tried your recommendation and am coming to the conclusion that it is an issue with the Transcend (Multimedia) external drive. The Seagate (Music) external drive works responds perfectly.

```
alan@alan-desktop ~ $ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdb1 on /media/alan/Music type ext4 (rw)
/dev/sdc1 on /media/alan/Multimedia type vfat (rw)
/dev/sdb1 on /home/alan/Music type ext4 (rw,0)
/dev/sdc1 on /home/alan/Multimedia type vfat (rw,0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=alan)
alan@alan-desktop ~ $ df  -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        20G  6.1G   13G  33% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           795M  1.4M  794M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G   80K  3.9G   1% /run/shm
none            100M   24K  100M   1% /run/user
/dev/sdb1       459G  294G  142G  68% /home/alan/Music
/dev/sdc1       932G  305G  627G  33% /home/alan/Multimedia
alan@alan-desktop ~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=77bfec5c-9516-4c1c-9e3e-8c9d986cdbb5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=471cd8c5-647d-4345-846d-93dcef130819 none            swap    sw              0       0
/dev/sdb1 /media/alan/Music/	ext4	defaults	0	0
/dev/sdc1 /media/alan/Multimedia/	vfat	defaults	0	0
# Plex Music USB External Mount
UUID=f5e0e121-6878-4906-8b7f-c6b6a929c42f	/home/alan/Music	ext4	00
UUID=533E-AEDB	/home/alan/Multimedia	vfat	0	0
```

```
]alan@alan-desktop ~ $ ls -al  /path/to/the/Music  /path/to/the/Multimedia
ls: cannot access /path/to/the/Music: No such file or directory
ls: cannot access /path/to/the/Multimedia: No such file or directory
alan@alan-desktop ~ $
``` 

I can get Plex to read the Transcend Drive (Multimedia) and copy and paste files if I do a manual method (avoiding fstab):

sudo mount /dev/sdc1 /home/alan/Multimedia

Thanks
Alan

---

### Post by Alan_Dean on 2015-11-16
I have an external hard drive called "Multimedia" that on permissions is greyed out and says "root". How do I change it it so that I can access it usually my login "alan"

Thank you

Alan

---

### Post by TheFu on 2015-11-16
Non-linux file system permissions are usually controlled by the **mount** options.  What file system is on the drive?  BTW, isn't this in some other thread?  I remember asking for some information to determine some stuff about this ... was that posted?

---

### Post by howefield on 2015-11-16
Threads merged.

---

### Post by Alan_Dean on 2015-11-16
Running FAT 32 but the same issue arose when it was EXT4

---

### Post by TheFu on 2015-11-16
> **Alan_Dean said:**
> Running FAT 32 but the same issue arose when it was EXT4

Under ext4, it is easier to fix (for me), forever. Plus you won't run into the limited file size issues that fat32 has (which is commonly hit with multimedia files).

So ... if you will reformat to ext4, that would be easier to fix and the 2G or is it 4G file size limit won't be an issue. If you have hidef video files, this would be very important.

All of this comes down to having your usereid and the plex userid in the same group, then forcing all directories and files to use that group in the Multimedia area. All of this is pretty easy.

Basically, you want permissions like (assuming "alan" is your Linux userid): 
```
drwxrwsr-x  2 alan   plex   4096 Nov 16 08:15 Multimedia/
```
Note the "s" in the group-execute permissions?  THAT is critical.  

Also, note how the 'group' is "plex" ... add your userid to the plex group.  I'd use sudoedit /etc/group and just put "alan" at the end of the  line with "plex" in it already.

Bam. Everything will "just work" ... (assuming the default umask for you and plex is 002). If there isn't anything under Multimedia/ ... all new files and directories will be created with the group you want automatically.  If there are files already, run .... 
```
sudo chown -R alan:plex /full/path/to/Multimedia
```
followed by 
```
find /full/path/to/Multimedia -type d -exec chmod g+s {} \;
```
The order here matters.

Bam!  That's it.  You can use Plex to manage your media ... including deletion.  If you want to prevent deletion, don't use the plex group and don't give "other" any permissions except read.

Again, if you use fat32, things are different. The above stuff won't help.  I don't have any fat32 stuff here connected to plex, but that answer would be in the **mount** options for the storage.

---

### Post by Alan_Dean on 2015-11-16
Thank you. I shall get to work on that and reformat to ext4. I do prefer ext4, it boots and transfers faster. My only reservation is that fat32 will play on anything. No real problem though I am 100% Linux and can always transfer files to USB stick for TV

Thank you
Alan

---

