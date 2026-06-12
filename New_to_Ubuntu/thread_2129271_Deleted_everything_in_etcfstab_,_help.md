---
title: "Deleted everything in /etc/fstab , help?"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by mocroboy on 2013-03-25
Hello,

I did something very stupid as I know very little about Ubuntu. I tried to add a rule to /etc/fstab but ended up deleting everything (and I think I saved it to). Now, when I go back and check the file I see that it's empty. I still didn't reboot, I am typing this thread from my system at this very moment. Can someone tell me how to undo the changes I made, or does someone know about a way of changing the file back? I still didn't reboot, so I think that there has to be a way of reading all my mounted partitions and add them to fstab, or am I wrong?

Can someone please reply? Thank you in advance.

---

### Post by Cheesemill on 2013-03-25
Can you post the output of the following commands please and I'll get back to you with a correct fstab file.
```
mount
sudo blkid -c /dev/null
```

---

### Post by mocroboy on 2013-03-25
This is the output generated:

/dev/sda3 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda4 on /media/sda4 type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /home/someone/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=someone)
/dev/sda2 on /media/System type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)



Although I have to say that I don't see another partition ntfs named Data in this information. I have a dual boot with Windows 7.
Thank you for your help!

---

### Post by Cheesemill on 2013-03-25
Can you post the output of the second command I asked for as well please.

---

### Post by mocroboy on 2013-03-25
The second command gives me no output. Nothing happens?

**Edit:**
Sorry my bad, I should run it as root of course.

This is first output:
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda4 on /media/sda4 type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /home/someone/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=someone)
/dev/sda2 on /media/System type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

second output:
/dev/sda1: UUID="620AD03B0AD00DC3" TYPE="ntfs" 
/dev/sda2: LABEL="System" UUID="B282D56882D53219" TYPE="ntfs" 
/dev/sda3: UUID="2d48f0a4-2b3b-4a33-b612-8f2e217794fb" TYPE="ext4" 
/dev/sda4: LABEL="Data" UUID="1820EEF620EEDA30" TYPE="ntfs"

---

### Post by Cheesemill on 2013-03-25
How about just...
```
sudo blkid
```

Or if that still doesn't work can you post the output of...
```
sudo lsblk -f
```

---

### Post by Cheesemill on 2013-03-25
OK then, this should do you...
```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> 				<mount point>   <type>  <options>       		<dump>  <pass>
UUID=2d48f0a4-2b3b-4a33-b612-8f2e217794fb	/		ext4	errors=remount-ro		0	1

```

You don't appear to have a swap partition, is this correct?

---

### Post by mocroboy on 2013-03-25
That's true, I don't. The problems began when I was trying to add a swap file :). How can I edit the file? Can I do it with gedit, because with the terminal everything went wrong? And shouldn't there be something like the names of all my partitions in your fstab?

---

### Post by Cheesemill on 2013-03-25
You can edit your fstab using gedit with the command...
```
gksudo gedit /etc/fstab
```

The best method to refer to partitions is by using their UUID instead of using /dev/sda3 as UUID's are guaranteed not to change, whereas the device name can change between reboots. You could use the partition label instead, but you don't have one for your /dev/sda3 partition.

---

### Post by mocroboy on 2013-03-25
**Edit:**
[FONT=Verdana]Ok, now I understand. But would my drives automatically mount when I only paste your solution? I mean, would my other partitions be recognized when using your solution? I was thinking about the following, but can't tell what should be at the question marks?:[/FONT]

```
[FONT=Verdana]# /etc/fstab: static file system information.#[/FONT]
[FONT=Verdana]# Use 'blkid' to print the universally unique identifier for a[/FONT]
[FONT=Verdana]# device; this may be used with UUID= as a more robust way to name devices[/FONT]
[FONT=Verdana]# that works even if disks are added and removed. See fstab(5).#[/FONT]
[FONT=Verdana]# <file system>                                                                    <mount point>        <type>            <options>                 <dump>      <pass>[/FONT]

[FONT=Verdana]UUID=620AD03B0AD00DC3                                                                           ntfs                  ????????                     ?                    ?[/FONT]
[FONT=Verdana]UUID=B282D56882D53219                                          /media/system           ntfs                 ??????                          ?                    ?[/FONT]
[FONT=Verdana]UUID=2d48f0a4-2b3b-4a33-b612-8f2e217794fb     /                                     ext4                errors=remount-ro     0                    1[/FONT]
[FONT=Verdana]UUID=1820EEF620EEDA30                                         /media/sda4               ntfs                  ????                              ?                    ?[/FONT]
```

Sorry, I know I'm terrible with editing :)

---

### Post by Cheesemill on 2013-03-25
Your other drives don't need to be in your fstab file.

Instead of being mounted by fstab they are being mounted by a combination of gvfs and fuse, you don't need to worry about what this means just that everything will be OK.
The fstab I've given you will have your system in exactly the same state it was in before you made your mistake.

---

### Post by mocroboy on 2013-03-25
I wanted to thank you for all the help, the problem is no more! :). So again, thanks!

---

