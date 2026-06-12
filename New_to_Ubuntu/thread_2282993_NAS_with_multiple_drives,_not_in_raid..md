---
title: "NAS with multiple drives, not in raid."
date: 2015-06-18
forum: New to Ubuntu
---

### Post by joakim6 on 2015-06-18
Hello, new here and new to ubuntu! Been googling to find what I need but still with no success I turn here, hope you guys could help me. My goal is turning my "old" computer to a NAS which I can reach with my PC and over the internet. To begin with I'm trying to fix it so I can reach it with my PC they way I want it.

The NAS is installed with Ubuntu Server 14.04, OpenSSH and Samba. It contains 5 HDD, 1 for OS and rest for storage. As they are different size I wont RAID them (maybe 2 in RAID1 if it's worth it?). Not sure what kind of information you guys need but I will try and include everything I can. So just tell me what more you need!


Not sure how the system works on ubuntu but I'm trying to make a separate folder for each drive. So when I open NAS under network on my windows PC I should either find 4 folders, one for each or just 1 folder with 4 folder in it. Hope that makes sense.


/dev/sdb1   - OS, 120GB (smallest I had)
/dev/sda    - 160GB storage, disk1
/dev/sdc    - 250GB storage, possible for RAID1 if it's worth it at all, disk2
/dev/sdd    - 500GB storage, disk3
/dev/sde    - 250GB storage, possible for RAID1 if it's worth it at all, disk4

Right now they are mounted to one folder each, /media/diskX, but they didn't show up when I shared them. Have managed to share one folder earlier from /home/username/share but removed it because most seemed to want to mount and share from /media/. Might be something right here that I'm missing...

Anyway. Right now the 4 storage drives doesn't show up with sudo lshw -C disk and df -h. But with mount they show up and says that they are mounted to the folders mentioned earlier.


Would be awesome if someone could point me in the right direction from here because I've tried like everything I could find.

Yours
/Zoubiey

---

### Post by dino99 on 2015-06-18
heterogene hdds is not the best case for a raid installation, but setting a lvm should makes sense.
hit the links below to access the wikis & howtos

---

### Post by joakim6 on 2015-06-18
> **dino99 said:**
> heterogene hdds is not the best case for a raid installation, but setting a lvm should makes sense.
hit the links below to access the wikis & howtos
Thanks for your reply, but I'm not even sure what I'm looking for.

Might be easy to spot that I come from Windows as I want one HDD for one "folder". Is that even possible to do and share without using lvm?

I rather skip the RAID as the only HDDs that can do it are my 250GB and not sure if I even can have RAID and single drives? If not, then I just rather have single drives all together.

Hope I make some sort of sense.

---

### Post by matt_symes on 2015-06-18
Hi

I would really recommend against using LVM to create a volume over all the disks, unless you are using a raid array, because if one disk fails then you can consider the entire volume lost.

Personally, i would RAID 1 for your two 250GB hard drives and use those mirrored drives for you most important files such as pictures, photos, videos of family and friends..... Remember though, RAID is not a backup. I would highly, highly recommend this.

For remote access i would look at using sshfs (as you already have ssh installed) or using a VPN such as openVPN. With SSH use keys and with openVPN use certs.

Both will be encrypted and authenticated connections to your NAS but you will suffer a performance hit because of that. You will also have to punch a hole through your firewall to the box hosting your NAS.

Can you see the drives in the NAS ?

If you could post the actual output of these commands on the terminal or console on the NAS.

```
sudo parted -l
```

```
sudo blikd
```

```
mount
```

Kind regards

---

### Post by joakim6 on 2015-06-18
> **matt_symes said:**
> Hi

I would really recommend against using LVM to create a volume over all the disks, unless you are using a raid array, because if one disk fails then you can consider the entire volume lost.

Personally, i would RAID 1 for your two 250GB hard drives and use those mirrored drives for you most important files such as pictures, photos, videos of family and friends..... Remember though, RAID is not a backup. I would highly, highly recommend this.

For remote access i would look at using sshfs (as you already have ssh installed) or using a VPN such as openVPN. With SSH use keys and with openVPN use certs.

Both will be encrypted and authenticated connections to your NAS but you will suffer a performance hit because of that. You will also have to punch a hole through your firewall to the box hosting your NAS.

Can you see the drives in the NAS ?

If you could post the actual output of these commands on the terminal or console on the NAS.

```
sudo parted -l
```

```
sudo blikd
```

```
mount
```

Kind regards


Yeah, thought the same thing with LVM. That's why I didn't go with that in the first place. Did the RAID1 in the beginning but couldn't get the other drives to mount properly or something so I just reinstalled everything. But could give it a try once again.

After I posted I managed to get the folder to show for each drive (I think it was made the correct way atleast) but couldn't enter the folders because it said my login was wrong. So right now I'm stuck there, but I could reinstall everything again and just start from scratch, feels much better.

My girlfriend just came over so will get back to you as soon as possible with the outputs. Thanks! :)

---

### Post by matt_symes on 2015-06-18
Hi

No worries. When you're ready, just create a new post and we'll take it from there.

There a many people who can help you on these forums.

Kind regards

---

### Post by joakim6 on 2015-06-18
> **matt_symes said:**
> Hi

No worries. When you're ready, just create a new post and we'll take it from there.

There a many people who can help you on these forums.

Kind regards

Well she fell asleep fast so took the chance to try againt and this is what I got.

sudo parted -l gives me this:
```


Model: ATA Hitachi HDS72161 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  160GB  160GB  primary




Model: ATA SAMSUNG SP1213C (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  116GB  116GB   primary   ext4            boot
 2      116GB   120GB  4022MB  extended
 5      116GB   120GB  4022MB  logical   linux-swap(v1)




Model: ATA HDS722525VLSA80 (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary




Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary




Model: ATA HDS722525VLSA80 (scsi)
Disk /dev/sde: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary



```

sudo blkid got me this:
```
/dev/sdb1: UUID="88ce44ed-040d-472f-af48-0b0b2fadd490" TYPE="ext4"/dev/sdb5: UUID="f4b31ab6-ee2c-4e88-a5ab-d47eb25c95f3" TYPE="swap"

```
If I'm not it should show the UUID for all my drives. But this is just my OS drive.

mount got me this:
```


/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda on /home/jlundqvist/160GB type ext4 (rw)
/dev/sdc on /home/jlundqvist/250GB type ext4 (rw)
/dev/sdd on /home/jlundqvist/500GB type ext4 (rw)
/dev/sde on /home/jlundqvist/250GB2 type ext4 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
```

Hope that could shine some light on the "problem".

Maybe it's better I start over from scratch and start with the RAID and then this, or what do you think?

---

### Post by matt_symes on 2015-06-18
Hi

You have not created any partitions on the block devices sda, sdc, sdd and sde by the looks of it.

You need to create some partitions, format them and then mount them and not the block devices.

Kind regards

---

### Post by mastablasta on 2015-06-19
if I may suggest some completely different approach.

first I would say RAID1 is not really worth it especially since in case of disk failure you might have a problem finding a 250 GB drive to replace it anyway. :P

secondly I would suggest you have a look at the Ubuntu supported Zentyal project. they aim to replace windows small business server. use "expert install"  on it's install and install web gui only. then configure at ease via that GUI. although they reduced many of the modules in past couple of iterations, they still hold the basic ones such as networking with windows, ssh setup, automated updates and backup setup etc.

if you want a drop and forget webGUI with more options for home server/NAS and still easy to use I suggest you look at Openmediavault. The forum people there are mostly very friendly and devs will give you a hand as well. OMV is Debian based.

---

### Post by joakim6 on 2015-06-19
> **matt_symes said:**
> Hi

You have not created any partitions on the block devices sda, sdc, sdd and sde by the looks of it.

You need to create some partitions, format them and then mount them and not the block devices.

Kind regards

That's weird because I've created it. Have even done it twice because the first one just disappeared, but can fix that real quick!

Is is correct that I mount them to /home/username/160GB and so on?

> **mastablasta said:**
> if I may suggest some completely different approach.

first I would say RAID1 is not really worth it especially since in case of disk failure you might have a problem finding a 250 GB drive to replace it anyway. :P

secondly I would suggest you have a look at the Ubuntu supported Zentyal project. they aim to replace windows small business server. use "expert install"  on it's install and install web gui only. then configure at ease via that GUI. although they reduced many of the modules in past couple of iterations, they still hold the basic ones such as networking with windows, ssh setup, automated updates and backup setup etc.

if you want a drop and forget webGUI with more options for home server/NAS and still easy to use I suggest you look at Openmediavault. The forum people there are mostly very friendly and devs will give you a hand as well. OMV is Debian based.

Good point on the RAID part.. Might think about it.

OMW is good backup to fall back on, but will try and see if I can fix this issue with ubuntu. Not fun to take the easy way out and choose something else ;)

But will keep it in mind, thanks!

---

### Post by mastablasta on 2015-06-19
Zentyal is on Ubuntu and supported by Canonical (or is it partner of Cannonical?!) and you can install it from repositories.

on the other hand I installed Ajenti to the Ubuntu server to be able to Admin server more easily. but I am thinking once it is all setup that maybe I should move to zentyal. ajenti is nice as it has a built in terminal as well as text editor &file manager, so it's easier to edit the server config files (nano is really not my thing (compared to DOS edit it looks horrible), Vim is worse as you need to know the shortcuts and commands to use it).

---

### Post by joakim6 on 2015-06-21
Now every disk got a partition and changed the mounting point to /mnt/folderX. Everything seems to be working, can see and access every folder from my windows PC. Without login tho, might need to change that. Now time to see if I can get SSH keys to work so I can access the computer over the internet. Thanks for your help!

EDIT: Can't write or create new folders. Guessing something is wrong in my permissions because I don't need any password to enter the folders either..

---

### Post by matt_symes on 2015-06-23
Hi

> **joakim6 said:**
> Now every disk got a partition and changed the mounting point to /mnt/folderX. Everything seems to be working, can see and access every folder from my windows PC. Without login tho, might need to change that. Now time to see if I can get SSH keys to work so I can access the computer over the internet. Thanks for your help!

EDIT: Can't write or create new folders. Guessing something is wrong in my permissions because I don't need any password to enter the folders either..

Your mount points are most probably owned by root. Change them to your user.

```
sudo chown -R <your_username>:<your_username> /mnt/folderX
```

Kind regards

---

