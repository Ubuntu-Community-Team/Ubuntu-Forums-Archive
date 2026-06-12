---
title: "problems with ls command"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by unibroker on 2012-10-18
I am trying to see the contents of an external drive.```
jim@computer:~$ ls /media
  apt  HP Pocket Media Drive  HP Pocket Media Drive_
jim@computer:~$ ls /media/HP Pocket Media Drive_
ls: cannot access /media/HP: No such file or directory
ls: cannot access Pocket: No such file or directory
ls: cannot access Media: No such file or directory
ls: cannot access Drive_: No such file or directory
```

As you can see when I "ls /media" it returns 2, "HP Pocket Media".  When I add either one of the choices it returns "cannot access". Is this a permissions problem and if so how do I fix it?

---

### Post by papibe on 2012-10-18
Hi unibroker.

Spaces are interpreted as a separator, thus for 'ls' the name:
```
/media/HP Pocket Media Drive_
```
appears as 2 parameter.

You have 3 options:
[LIST]
[*]Use quotes: '/media/HP Pocket Media Drive_'
[*]Escape the space with '\': /media/HP Pocket\ Media Drive_
[*]Or let the system escape the spaces by using tab to complete the name of the directory:
```
ls /media/HP<tab>
```
and the name will complete itself.
[/LIST]
I hope that helps, and let us know how it goes.
Regards.

---

### Post by unibroker on 2012-10-18
> **papibe said:**
> Hi unibroker.

Spaces are interpreted as a separator, thus for 'ls' the name:
```
/media/HP Pocket Media Drive_
```
appears as 2 parameter.

You have 3 options:
[LIST]
[*]Use quotes: '/media/HP Pocket Media Drive_'
[*]Escape the space with '\': /media/HP Pocket\ Media Drive_
[*]Or let the system escape the spaces by using tab to complete the name of the directory:
```
ls /media/HP<tab>
```
and the name will complete itself.
[/LIST]
I hope that helps, and let us know how it goes.
Regards.

Thanks. I used the single quote suggestion and it worked and returned ```
ls: cannot open directory /media/HP Pocket Media Drive: Permission denied
```

I then used it with "sudo" but just returned the prompt.  My /home backup is in here and I just want to make sure I can do a restore.

---

### Post by drmrgd on 2012-10-18
That suggests that your drive is not mounted at the location for some reason.  You can look to see if it's mounted by looking at mtab:

```
cat /etc/mtab
```

You also might try to remount all of your devices (or just that one, but it's more typing :) ):

```
sudo mount -a
```

Does that bring the drive back up?  If not, we'll have to troubleshoot a little more by finding out how you set up the mount point for the drive and how you're connecting it.

---

### Post by unibroker on 2012-10-18
[QUOTE=drmrgd;12303685]That suggests that your drive is not mounted at the location for some reason.  You can look to see if it's mounted by looking at mtab:

```
cat /etc/mtab
```

That returned ```
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jim/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jim 0 0
/dev/sdf2 /media/6e9ac323-45f6-4cb0-acca-8277530a3584 ext4 rw,nosuid,nodev,uhelper=udisks 0 0
/dev/sdf5 /media/HP\040Pocket\040Media\040Drive_ fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
```

I followed with the other input and then followed that with the initial code and it returned the above results.  A little history on my setup.  The external drive was originally used with WinXP.  I dual booted Ubuntu late last year never really setting up any drives as I just used the default installation of Ubuntu and started backing things up not understanding the process.  That is why possibly I'm incurring problems now.

---

### Post by drmrgd on 2012-10-18
> **unibroker said:**
> [QUOTE=drmrgd;12303685]That suggests that your drive is not mounted at the location for some reason.  You can look to see if it's mounted by looking at mtab:

```
cat /etc/mtab
```

That returned ```
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jim/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jim 0 0
/dev/sdf2 /media/6e9ac323-45f6-4cb0-acca-8277530a3584 ext4 rw,nosuid,nodev,uhelper=udisks 0 0
/dev/sdf5 /media/HP\040Pocket\040Media\040Drive_ fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
```

I followed with the other input and then followed that with the initial code and it returned the above results.  A little history on my setup.  The external drive was originally used with WinXP.  I dual booted Ubuntu late last year never really setting up any drives as I just used the default installation of Ubuntu and started backing things up not understanding the process.  That is why possibly I'm incurring problems now.

So, based on that, can you access the drive now?  The mtab output shows that the drive is mounted at "/media/HP Pocket Media Drive_" now.

---

### Post by unibroker on 2012-10-18
> **drmrgd said:**
> [QUOTE=unibroker;12303718]

So, based on that, can you access the drive now?  The mtab output shows that the drive is mounted at "/media/HP Pocket Media Drive_" now.

When I do ```
sudo ls '/media/HP Pocket Media Drive'
``` it just returns the prompt.  I am expecting to see the contents.  Am I wrong?

---

### Post by drmrgd on 2012-10-18
Yes, you should see files.  However, be aware that the mounted drive actually has an underscore at the end of the name, just like I listed.  I suspect that if you list the contents of /media:

```
ls -l /media
```

You'll see one with an underscore and one without.  Something happened with the original mount and the system created a second mount with an underscore.  I think that happens if the drive is not present and you try to right to it somehow...not exactly sure what causes that to be honest.

---

### Post by unibroker on 2012-10-18
> **drmrgd said:**
> Yes, you should see files.  However, be aware that the mounted drive actually has an underscore at the end of the name, just like I listed.  I suspect that if you list the contents of /media:

```
ls -l /media
```

You'll see one with an underscore and one without.  Something happened with the original mount and the system created a second mount with an underscore.  I think that happens if the drive is not present and you try to right to it somehow...not exactly sure what causes that to be honest.

Yes, I tried both because I noticed the underscore.  I'm considering just reformatting the drive and starting from scratch.  Once I set up the partitions (something I didn't do originally) I'll go into WinXP first a make a copy of my database and then come back to Ubuntu and make a copy of my /home.  I'm doing all of this to do a clean install of the 64 bit version of the Ubuntu I have.  Thanks for your input.

---

### Post by Lisiano on 2012-10-18
Before you do anything drastic, please provide the output of ```
ls -lha /media
```And ```
echo $USER
```

Also please show us the contents of /etc/fstab```
cat /etc/fstab
```

---

### Post by unibroker on 2012-10-18
> **Lisiano said:**
> Before you do anything drastic, please provide the output of ```
ls -lha /media
```And ```
echo $USER
```

Also please show us the contents of /etc/fstab```
cat /etc/fstab
```

ls -lha /media
```
total 108K
drwxr-xr-x  6 root root 4.0K Oct 18 12:01 .
drwxr-xr-x 25 root root 4.0K Oct 12 05:57 ..
drwxr-xr-x 21 root root 4.0K Dec 28  2011 6e9ac323-45f6-4cb0-acca-8277530a3584
drwxr-x---  2 root root 4.0K Dec 31  2011 apt
drwxr-xr-x  2 root root 4.0K Jul 15 12:28 HP Pocket Media Drive
drwx------  1 jim  jim   88K Oct 17 12:39 HP Pocket Media Drive_

```

echo $USER
```
jim
```

/etc/fstab
```
bash: /etc/fstab: Permission denied
```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c48cd755-355f-40ab-a1d7-a1aa9e72bd79 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4ad0f999-912a-482c-bd14-cea8879e2481 none            swap    sw              0       0

```

I think I understand where the second HP Media Drive_ came from; yesterday's attempt at restore.

---

### Post by Lisiano on 2012-10-18
Unplug all external media, then run this command
```
sudo rmdir '/media/HP Pocket Media Drive' '/media/6e9ac323-45f6-4cb0-acca-8277530a3584'
```
Then reconnect your drive.
Try looking again inside /media/HP Pocket Media Drive.
If it is empty or you get permission denied again, try looking in /media/6e9ac323-45f6-4cb0-acca-8277530a3584 instead.

---

### Post by unibroker on 2012-10-18
> **Lisiano said:**
> Unplug all external media, then run this command
```
sudo rmdir '/media/HP Pocket Media Drive' '/media/6e9ac323-45f6-4cb0-acca-8277530a3584'
```
Then reconnect your drive.
Try looking again inside /media/HP Pocket Media Drive.
If it is empty or you get permission denied again, try looking in /media/6e9ac323-45f6-4cb0-acca-8277530a3584 instead.

When I look under the Home Folder in I guess it's Nautilus and right click the external drive under Computer I get this 
```
umount: /media/HP Pocket Media Drive_ is not in the fstab (and you are not root)
```

When I look under Devices in the same Home Folder and right click this drive and select Safely Remove Drive I get this
```
Unable to stop 80 GB Hard Disk.  One or more partitions are busy on /dev/sdf
```

Do you still want me to physically disconnect?  I have noticed this for the last couple of days and rebooting it resolves it until something I do activates it again.  I could reboot, safely remove device and then try your instructions.  BTW, thanks for your's and the previous poster's help.  This has been a learning experience albeit a frustrating one.

---

### Post by unibroker on 2012-10-18
> **Lisiano said:**
> Unplug all external media, then run this command
```
sudo rmdir '/media/HP Pocket Media Drive' '/media/6e9ac323-45f6-4cb0-acca-8277530a3584'
```
Then reconnect your drive.
Try looking again inside /media/HP Pocket Media Drive.
If it is empty or you get permission denied again, try looking in /media/6e9ac323-45f6-4cb0-acca-8277530a3584 instead.
After your first instruction

```
rmdir: failed to remove `/media/6e9ac323-45f6-4cb0-acca-8277530a3584': No such file or directory
```

Reconnected drive and sudo ls.......and it returned all of the contents!  Voluminous thanks!  WoooHooo!

---

### Post by Lisiano on 2012-10-19
No need to use sudo when using ls

Happy I could help.

---

