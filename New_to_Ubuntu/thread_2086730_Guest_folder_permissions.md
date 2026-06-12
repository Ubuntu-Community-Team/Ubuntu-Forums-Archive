---
title: "Guest folder permissions"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by paulemony on 2012-11-21
Ubuntu 11.10 

I'm sure this has been answered already but my eyes have glazed over looking for it, simply put I have some folders (not all of them) on a separate partition (/media/Data) that I want Guest and/or standard account holder to access read-only. I've tried gksudo nautilus, properties, permissions but can't change anything (it couldn't be that simple, could it?).

---

### Post by papibe on 2012-11-21
Hi paulemony.

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2083469&highlight=read") for a similiar concern and a simple solution.

Let us know how it goes.
Regards.

---

### Post by paulemony on 2012-11-21
That was simple? Couldn't make head nor tail of it! Put it this way, there's a folder called Fotos which is full of other folders full of jpegs, it's on an NTFS partition called Data (dev/sda3, mount point media/Data). I want anyone who logs in as Guest to see these jpegs read-only. OK, I open a terminal & type sudo.

Then what?

---

### Post by papibe on 2012-11-21
Sorry about that.

Even if you understand it, that won't work on a NTFS disk, as it doesn't support ownership and permissions.

The only solution would be set the proper mount options.

As a fast non permanent solution, try this:
```
sudo umount /media/Data/

sudo mount -t ntfs /dev/sda3 /media/Data/ -odefaults,user,noexec,uid=1000,gid=1000,dmask=002,fmask=003

```
The values for uid, and gid (1000) probably work, but you can check the proper values if you run:
```
id
```

For a more permanent solution you could set an entry on the /etc/fstab file (different format though).

Let us know how it goes.
Regards.

---

### Post by paulemony on 2012-11-21
Permanent is good, what's the fstab entry though?

---

### Post by papibe on 2012-11-21
First you need to find out the disk ID using blkid.

For instance:
```
sudo blkid
``````

```
The results would be something like this:
```
dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-030D" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="40F88A9AF88A8DBA" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="4CB68E97B68E8166" TYPE="ntfs" 
/dev/sda5: UUID="ddf8b1e2-9852-449e-8a99-d334fc3d4b5a" TYPE="ext4" 
/dev/sda6: UUID="4498aa1b-7d1b-4612-bbee-dfe456091814" TYPE="ext4" 
/dev/sda7: UUID="61d8bda3-2b03-4920-b9f3-99a3fa1c9f8d" TYPE="swap" 
/dev/sdb1: LABEL="swapprecise" UUID="18c6d6c0-b7c1-4ad0-b1a4-e53ef6bf1db3" TYPE="swap" 
**/dev/sdc1: LABEL="My Book" UUID="02D0852FD08529CD" TYPE="ntfs" **

```
In this case the disk id for my external USB WD My Book will be:
```
02D0852FD08529CD
```
Then you need to add a line to the file /etc/fstab. To edit it:
```
gksudo gedit /etc/fstab
```
Add it to the end. Similar to this line (but use the proper disk ID):
```
UUID=02D0852FD08529CD  /media/Data  ntfs   defaults,user,noexec,uid=1000,gid=1000,dmask=002,fmask=003     0       2
```
For more information on the fstab file check this [tutorial]("https://help.ubuntu.com/community/Fstab"). 
Let us know how it goes.
Regards.

---

### Post by paulemony on 2012-11-21
Not so good, fstab looked like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc  proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=e50e43c6-31e4-42b6-8cfa-c522cee7db12  /      ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=faa20783-4388-45f4-8a21-71f755629b45  none   swap  sw                   0  0 
UUID=01CDA1A903D07330   /media/Data  ntfs   defaults,user,noexec,uid=1000,gid=1000,dmask=002,fmask=003     0       2 
```

whereupon computer froze, rebooted, got error message, basically couldn't mount Data so deleted line from fstab, back to square one!

---

### Post by paulemony on 2012-11-21
P.S.

```
$ sudo blkid
/dev/sda3: LABEL="Data" UUID="01CDA1A903D07330" TYPE="ntfs" 

```

---

### Post by papibe on 2012-11-21
Did it work when run manually as in post #4?

---

### Post by paulemony on 2012-11-22
```
sudo umount /media/Data/
```

```
~$ sudo mount -t ntfs /dev/sda3 /media/Data/ -odefaults,user,noexec,uid=1000,gid=1000,dmask=002,fmask=003
fuse: failed to access mountpoint /media/Data/: No such file or directory

```

```
~$ sudo blkid
$: command not found

```

```
~$ /dev/sda3: LABEL="Data" UUID="01CDA1A903D07330" TYPE="ntfs"
bash: /dev/sda3:: No such file or directory

```

---

### Post by Paqman on 2012-11-22
I'm familiar with this issue. The problem isn't a permissions one as such, it's that the guest account now has a slightly more restrictive apparmor setup than before.

What you need to do is edit the guest account's apparmor profile in /etc/apparmor.d and remove the "owner" conditional that's been attached to the location /media.

---

### Post by paulemony on 2012-11-22
The only thing I can see in /etc/apparmor.d that refers to Guest is a doc > lightdm-guest-session:

```
# vim:syntax=apparmor
# Profile for restricting lightdm guest session 
# Author: Martin Pitt <martin.pitt@ubuntu.com>

#include <tunables/global>

/usr/lib/lightdm/lightdm-guest-session-wrapper {
  #include <abstractions/authentication>
  #include <abstractions/nameservice>
  #include <abstractions/wutmp>
  /etc/compizconfig/config rw, # bug in compiz https://launchpad.net/bugs/697678
 
  / r,
  /bin/ rmix,
  /bin/fusermount Px,
  /bin/** rmix,
  /cdrom/ rmix,
  /cdrom/** rmix,
  /dev/ r,
  /dev/** rmw, # audio devices etc.
  owner /dev/shm/** rmw,
  /etc/ r,
  /etc/** rmk,
  /etc/gdm/Xsession ix,
  /lib/ r,
  /lib/** rmixk,
  /lib32/ r,
  /lib32/** rmixk,
  /lib64/ r,
  /lib64/** rmixk,
  /media/ r,
  /media/** rmwlixk,  # we want access to USB sticks and the like
  /opt/ r,
  /opt/** rmixk,
  @{PROC}/ r,
  @{PROC}/* rm,
  @{PROC}/asound rm,
  @{PROC}/asound/** rm,
  @{PROC}/ati rm,
  @{PROC}/ati/** rm,
  owner @{PROC}/** rm,
  # needed for gnome-keyring-daemon
  @{PROC}/*/status r,
  /sbin/ r,
  /sbin/** rmixk,
  /sys/ r,
  /sys/** rm,
  /tmp/ rw,
  owner /tmp/** rwlkmix,
  /usr/ r,
  /usr/** rmixk,
  /var/ r,
  /var/** rmixk,
  /var/guest-data/** rw, # allow to store files permanently
  /var/tmp/ rw,
  owner /var/tmp/** rwlkm,
  /{,var/}run/ r,
  # necessary for writing to sockets, etc.
  /{,var/}run/** rmkix,
  /{,var/}run/shm/** wl,

  capability ipc_lock,

  # silence warnings for stuff that we really don't want to grant
  deny capability dac_override,
  deny capability dac_read_search,
  #deny /etc/** w, # re-enable once LP#697678 is fixed
  deny /usr/** w,
  deny /var/crash/ w,
}
``` 

don't see anything akin to location/media, but even if I did wouldn't I be giving Guest access to the entire partition?

---

### Post by paulemony on 2012-11-22
P.S. I see "/owner" and "/media" but not clear what has to be changed, & what to.

---

### Post by Paqman on 2012-11-23
> **paulemony said:**
> P.S. I see "/owner" and "/media" but not clear what has to be changed, & what to.

Hmm, ok. It looks like your guest account doesn't have that restriction on /media. Weird, mine has on the last two versions of Ubuntu. Ignore my advice then, it looks like standard permissions stuff will solve your problem.

---

