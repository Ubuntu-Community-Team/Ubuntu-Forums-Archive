---
title: "Kubuntu thunderbird loses profile"
date: 2015-08-23
forum: New to Ubuntu
---

### Post by makem2 on 2015-08-23
Hi,

I have for the time being, a dual boot Windows 8.1 and kubuntu.

My data for windows is on D:\ partition and accessible to kubuntu.

After installing Thunderbird in kubuntu I was pleasantly surprised (as I have been with many things in kubuntu), that I could use my windows Thunderbird profile after I pointed the program to the directory.

I used it for a while and then after a reboot found that the profile i had 'made' in Thunderbird was no longer there and it was necessary to start again, pointing the program to the data.

Do I need to do something else to make the settings 'stick'?

---

### Post by howefield on 2015-08-23
"D:\" would need to be mounted before it is accessible to your Kubuntu install, whether that is at boot up or manually after boot is up to you ?

---

### Post by makem2 on 2015-08-23
ah, thank you - must be at boot then to 'hold' the profile.

---

### Post by makem2 on 2015-08-23
My fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=21f2660b-69d7-4890-9a70-62c839d095ba /               ext4    errors=remoun$
# /boot/efi was on /dev/sda2 during installation
UUID=8A04-2EF8  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda8 during installation
UUID=4bf97d69-5fdb-4b9b-9a7a-cb3b63e4712f none            swap    sw           $

/dev/sda5 /media/makem/Data ntfs-3g uid=1000,gid=1000,dmask=027,fmask=137 0 1
```

```

makem@newTOSH:~$ mount
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda5 on /media/makem/Data type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /boot/efi type vfat (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=makem)
makem@newTOSH:~$

```

But Thunderbird profile is missing after reboot. Something more needed?

---

### Post by makem2 on 2015-08-23
I had noticed that when I started to make a profile path I got an error saying thunderbird could not be read. As I was able to continue, make a profile and use it, I had ignored that.

When I looked at permissions I found that .thunderbird was owned by root which explains why the profile was still lost after D:\ was mounted. I have no idea why it should have been owned by root. I decided to uninstall and reinstall.

When I checked for the .thunderbird directory before I reinstalled I found it still existed and was as before, owned by root. Uninstalling the program had not removed that directory. I manually removed it and reinstalled. The .thunderbird directory was now owned by makem and the profile persisted after reboot.

The first install and the last were preformed from the USC.

---

