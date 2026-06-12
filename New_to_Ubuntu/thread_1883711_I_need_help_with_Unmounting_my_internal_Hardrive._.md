---
title: "I need help with Unmounting my internal Hardrive. Answer ASAP"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by Discipl on 2011-11-19
When I try unmounting it, it says only root can unmount and I've been trying to find a way to deal with this for like 5 hours but everything is to complicated and WAY to technical for someone who is normally a windows user. So I'm asking someone that will give me COMPLETE walk through of how to fix this problem but doesn't use any complicated terminology. I'm using Ubuntu 11.10 by the way.

---

### Post by boblemur on 2011-11-19
Did you mount it via the GUI in the first place? 

or did you mount it using the command line?

you can unmount it using command line with (which you shouldn't have to do):
```
sudo umount /media/<name of drive>
```

---

### Post by klein de usa on 2011-11-19
hi 

i'v had the same problem with a computer running 10.04 64bit, it has 3 sata hard drives installed, it is slow booting up and after you type your password to login it puts up a window up saying something about the power management program is not finished, in a couple of seconds that goes away and your at your desktop, i mount a hard drive by going to places and it is listed, when i'm done i right click on the icon and chose unmount it tells me i'm not root i have to be root and maybe something about fstab's  so i go to system > administration > disk utility and unmount it there.

this computer was one of the first to get 10.04 and after an update it started doing this, so i reinstalled it with 10.04.3 and it still does it i just figure it doesn't like having 3 sata hdd's to deal with? if someone has a explanation or a fix that would be nice

---

### Post by Discipl on 2011-11-19
> **boblemur said:**
> Did you mount it via the GUI in the first place? 
 
or did you mount it using the command line?
 
you can unmount it using command line with (which you shouldn't have to do):
```
sudo umount /media/<name of drive>
```
 
 
im sorry im being a noob haha but how do i find out what my drive is called?

---

### Post by Hedgehog1 on 2011-11-19
**boblemur**'s info will work to unmount the drive for this boot up.

When a drive is mounted as root every time you boot up and you didn't do it using the 'mount' command manually, that means it is mounted for you when you boot up by a setup file.

There is a text file that tells your system what to mount automatically for you whenever you boot up.

It is the '**F**ile **S**ystem **TAB**le', and Linux calls it: **fstab**.  It lives in the **/etc** directory, so to look at it and change it, we use the path: **/etc/fstab**

Here is an example of some of my **/etc/fstab** file:

```

# <file system>                           <mount point>  <type> <options>      <dump><pass>
proc                                      /proc           proc nodev,noexec,nosuid  0 0
UUID=fa6c0c73-f95a-4b44-a985-2bb26a42f1c8 /               ext4 errors=remount-ro    0 1
UUID=4aebc2c6-5984-47e3-b2ea-7fdfaf23343e /home           ext4 defaults             0 2
UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a none            swap sw                   0 0
UUID=EA561004560FCFED                     /media/Area51   ntfs defaults             0 0
UUID=5C28DA0E28D9E754                     /media/Area52   ntfs defaults             0 0

```

The last two lines mount my two NTFS partitions for me:

```

UUID=EA561004560FCFED                     /media/Area51   ntfs defaults             0 0
UUID=5C28DA0E28D9E754                     /media/Area52   ntfs defaults             0 0

```

If I wanted to make the 'Area52' one not mount at boot up, I would do this command to edit the **/etc/fstab** text file:

```
sudo gedit /etc/fstab
```

And then 'comment out' the mount command by pitting the '#' character in front of it:

```

UUID=EA561004560FCFED                     /media/Area51   ntfs defaults             0 0
#UUID=5C28DA0E28D9E754                     /media/Area52   ntfs defaults             0 0

```

And then save the file.

This may be what you need to do; after the next reboot the 'Area52' drive will not be mounted.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-11-19
Finding the name of the drive to manually unmount is usually done this way (non techie method):

If my drive says it is '**Area52**' in the file browser, then  the real name is usually '**/media/Area52**'.

If my drive says it is '**elements**' in the file browser, then  the real name is usually '**/media/elements**'.

***The Hedge***

:KS

---

### Post by boblemur on 2011-11-19
to extend Hedgehog1's answer you can also replace the word

on the line that he said:
```
UUID=5C28DA0E28D9E754                     /media/Area52   ntfs defaults             0 0
```
you can replace the word **defaults** with **rw,user,exec,auto** This will cause it to be automatically mounted at startup but should allow you to manually umount it.

---

### Post by Discipl on 2011-11-19
> **Hedgehog1 said:**
> Finding the name of the drive to manually unmount is usually done this way (non techie method):
 
If my drive says it is '**Area52**' in the file browser, then the real name is usually '**/media/Area52**'.
 
If my drive says it is '**elements**' in the file browser, then the real name is usually '**/media/elements**'.
 
***The Hedge***
 
:KS
 ok i tried using sudo /media/dev/sda but it says its not found

---

### Post by lisati on 2011-11-19
> **Discipl said:**
> ok i tried using sudo /media/dev/sda but it says its not found

A shot in the dark here:
```
sudo umount /dev/sda
```

---

### Post by boblemur on 2011-11-19
can you please provide the output of just running

```
mount
```

it should list something like:
```
$ mount
/dev/sda1 on / type ext4 (rw,noatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,size=5242880,mode=755,size=5242880,mode=755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=755,size=10%,mode=755)
tmpfs on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880,mode=1777,size=5242880,mode=1777)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,size=20%,mode=1777,size=20%,mode=1777)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /run/shm type tmpfs (rw,nosuid,nodev,size=20%,mode=1777,size=20%,mode=1777)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620,gid=5,mode=620)
/dev/sda3 on /home type ext4 (rw,noatime)

```
but not exactly the same of course

---

### Post by dFlyer on 2011-11-19
depending on what your trying to unmount have you tried Disk Utility. Just highlight the drive or partition and select unmount.

---

### Post by Discipl on 2011-11-19
> **boblemur said:**
> can you please provide the output of just running

```
mount
```

it should list something like:
```
$ mount
/dev/sda1 on / type ext4 (rw,noatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,size=5242880,mode=755,size=5242880,mode=755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=755,size=10%,mode=755)
tmpfs on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880,mode=1777,size=5242880,mode=1777)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,size=20%,mode=1777,size=20%,mode=1777)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /run/shm type tmpfs (rw,nosuid,nodev,size=20%,mode=1777,size=20%,mode=1777)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620,gid=5,mode=620)
/dev/sda3 on /home type ext4 (rw,noatime)

```
but not exactly the same of course
heres what i got


  


$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jesse/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jesse)
jesse@lukas-AO751h:~$

---

### Post by Discipl on 2011-11-19
> **dFlyer said:**
> depending on what your trying to unmount have you tried Disk Utility. Just highlight the drive or partition and select unmount.

this is what i tried in the first place and thats where im getting the only root can unmount error.

---

### Post by oldos2er on 2011-11-19
If you're trying to unmount your root partition, /dev/sda1/, you cannot be booted into it. You'd need to boot from LiveCD or LiveUSB.

Can you explain what your goal is, i.e. why you need to unmount the drive?

---

### Post by boblemur on 2011-11-19
oldos2er is right, im not sure what you are trying to do, but your operating system is running of /dev/sda1 and you cannot unmount the main drive the operating system is running on and You do not have any other drives mounted.

If you let us know why you need to unmount that drive we may be able to help you further

---

### Post by Discipl on 2011-11-19
im trying to install windows on it but when i try and install it when the computer turns on then it says it has to be ntfs file system so i tried formating it by clicking format volume but then it had an error say its busy and the details said it was mounted  and thats where i got the only root can unmount so basicly i need to format it to ntfs so i can reinstall windows vista

---

### Post by boblemur on 2011-11-19
Do you intend to dualboot? or do you wish to go back to windows only?
You cannot install windows from within ubuntu (as far as i know)
formatting back to ntfs will wipe ubuntu off the computer.

I think what you intend to do (if you want to dualboot) is to boot off a ubuntu live cd, resize the linux partition (using gparted) and then install windows in the newly created space. 

if you want to delete ubuntu entirely you will need to boot of the windows CD/DVD and delete the partition this will ERASE EVERYTHING and let you start again.

There are good guides to dualbooting:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

for example

Be careful what you are destroying when you try things like this if in doubt please post a new thread with your questions

---

### Post by Discipl on 2011-11-19
> **boblemur said:**
> Do you intend to dualboot? or do you wish to go back to windows only?
You cannot install windows from within ubuntu (as far as i know)
formatting back to ntfs will wipe ubuntu off the computer.

I think what you intend to do (if you want to dualboot) is to boot off a ubuntu live cd, resize the linux partition (using gparted) and then install windows in the newly created space. 

if you want to delete ubuntu entirely you will need to boot of the windows CD/DVD and delete the partition this will ERASE EVERYTHING and let you start again.

There are good guides to dualbooting:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

for example

Be careful what you are destroying when you try things like this if in doubt please post a new thread with your questions

is there any way i could turn my file system into ntfs while in ubuntu?

---

### Post by Discipl on 2011-11-19
nevermind i deleted the partition. and windows is installing. thank you to everyone who replied with helpful answers.

---

### Post by lisati on 2011-11-19
> **Discipl said:**
> is there any way i could turn my file system into ntfs while in ubuntu?

Changing a file system's format while it is in use is risky with the possibility of losing or damaging data. It might be easier to make a backup of your important data then make the changes you want from a Live CD

---

