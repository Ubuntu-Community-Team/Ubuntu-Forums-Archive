---
title: "[SOLVED] Disk Mount Disaster."
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Rabidmonkey1 on 2008-05-29
Hi all, I really hope someone out there can help me sort this out, because I'm desperate!

My setup is as follows:  On one physical drive I keep Ubuntu. On another physical drive I keep Windows X64, which I dual boot.  I recently installed a new Western Digital 500 gb SATA drive in my computer so that I could share a single media drive between the two - all my music and documents,etc. It's formatted as ext3. I'd like the new ext3 drive to mount on startup.

I was able to get it to work yesterday, mounting and everything, but after installing fs-driver, from fs-driver.org, windows seems to have locked it up, and now I can't access it.

Worse yet, I can't mount the windows partition now either, because I've thoroughly trounced my FSTAB file, which, after hours of searching forums and google, is in horrible shape in my effort to fix it...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                            0  0  
# /dev/sda1
UUID=483835a4-10ed-4b28-aa0e-309daab4dd0f  /              ext3         defaults,errors=remount-ro          0  1  
# /dev/sda5
UUID=5739bd42-d709-48f9-bbba-1eafd78a4b10  none           swap         sw                                  0  0  
/dev/hdb                                   /media/cdrom0  udf,iso9660  user,noauto,exec                    0  0  

none                                       /proc/bus/usb  usbfs        devgid=46,devmode=664               0  0  
/dev/sdc1                                  /media/sdc1    ext3         check,errors=remount-ro,users,user  0  0  
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
/dev/sdc1 /media/sdc1 ext3 ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
```

I know that the answer lies in editing the FSTAB file, I just have no idea what to write in there (or at least a very poor idea).  Can someone help me out so that I can automatically mount my 3rd hard drive (but not the NTFS windows partition) on startup?  It would be really, amazingly, fantastically appreciated.  Thanks!!!

-Bob

---

### Post by unutbu on 2008-05-29
Please post
```
sudo fdisk -l
blkid
```

---

### Post by Rabidmonkey1 on 2008-05-29
> **unutbu said:**
> Please post
```
sudo fdisk -l
blkid
```
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ac884

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59416   477258988+  83  Linux
/dev/sda2           59417       60801    11125012+   5  Extended
/dev/sda5           59417       60801    11124981   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fa00f9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f3fba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

```

---

### Post by unutbu on 2008-05-30
```
sudo mv /etc/fstab /etc/fstab-orig

gksu gedit /etc/fstab
```
Put this in /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system>                            <mount point>  <type>       <options>                      <dump>  <pass>
proc                                       /proc          proc         defaults                            0  0  
# /dev/sda1
UUID=483835a4-10ed-4b28-aa0e-309daab4dd0f  /              ext3         defaults,errors=remount-ro          0  1  
# /dev/sda5
UUID=5739bd42-d709-48f9-bbba-1eafd78a4b10  none           swap         sw                                  0  0  
/dev/sdb1                                  /media/sdb1    ntfs-3g      ro,user,fmask=0111,dmask=0000  0  0  
/dev/sdc1                                  /media/sdc1    ext3         defaults                            0  0  
```

Make sure that /media/sdb1 and /media/sdc1 exist:

```
sudo mkdir /media/sdb1
sudo mkdir /media/sdc1
```

Test that you can mount the hard drives:

```
mount /dev/sdb1 /media/sdb1
mount /dev/sdc1 /media/sdc1
```
If you can mount /dev/sdc1 this way, then it should also mount automatically at boot. (Per your request, sdb1 will not be mounted at boot [Edit: This is a mistake. It will get mounted unless you add the 'noauto' option]).

There is a chance that the NTFS partition won't mount. In that case, you probably need to install the ntfs-3g package
```
suda apt-get install ntfs-3g
```
Then try
```
mount /dev/sdb1 /media/sdb1
```
again.

Hope this helps.

---

### Post by logos34 on 2008-05-30
[delete - I see unutbu has responded]

---

### Post by Rabidmonkey1 on 2008-05-30
Thanks for the responses so far!

unutbu, I see where you're headed with all this and it makes sense, but when I go to mount the drives as per your instructions
```
mount /dev/sdb1 /media/sdb1
mount /dev/sdc1 /media/sdc1
```

I receive this message back for both drives:

"mount: only root can do that"

A sudo will get it to mount and unmount, but obviously I don't want to log into root to do something so simple.  I guess this is a permission thing?  Sorry if this is a noob question, but how do I go about modifying that? (the only reason I ask is because I messed up the fstab file so badly last time :lolflag:)

---

### Post by unutbu on 2008-05-30
Rabidmonkey1, (hehe, I enjoy saying that) so you can play with fstab with impunity:

```
sudo cp /etc/fstab /etc/fstab-worksok
```

Then you can experiment/play with /etc/fstab, and if you don't like the changes, then you can revert by running
```

sudo cp /etc/fstab-worksok /etc/fstab
```

To allow any user to mount a filesystem, just add the 'user' option:


```
# /etc/fstab: static file system information.
#
# <file system>                            <mount point>  <type>       <options>                             <dump>  <pass>
proc                                       /proc          proc         defaults                                   0  0  
# /dev/sda1
UUID=483835a4-10ed-4b28-aa0e-309daab4dd0f  /              ext3         defaults,errors=remount-ro                 0  1  
# /dev/sda5
UUID=5739bd42-d709-48f9-bbba-1eafd78a4b10  none           swap         sw                                         0  0  
/dev/sdb1                                  /media/sdb1    ntfs-3g      user,fmask=0111,dmask=0000                 0  0  
/dev/sdc1                                  /media/sdc1    ext3         rw,suid,dev,exec,auto,user,async           0  0
```

Notice that for /dev/scd1, 'defaults' became 'rw, suid, dev, exec, auto, **user**, async'. That's because defaults is shorthand for 
rw, suid, dev, exec, auto, **nouser**, async. I simply changed nouser to user.

Here is a list of common options and what they mean:

```
defaults        rw, suid, dev, exec, auto, nouser, async.
user            Permit any user to mount the filesystem. This automatically implies noexec, nosuid,nodev unless overridden.
ro 		Mount read-only.
rw 		Mount read-write.
auto         	The filesystem can be mounted automatically at bootup. This is really unnecessary as this is the default action of mount -a anyway.
noauto       	The filesystem will NOT be automatically mounted at startup, or when mount passed -a. You must explicitly mount the filesystem.
dev/nodev    	Interpret/Do not interpret character or block special devices on the file system.
exec / noexec   Permit/Prevent the execution of binaries from the filesystem.
suid/nosuid     Permit/Block the operation of suid, and sgid bits.
nouser          Only permit root to mount the filesystem. This is also a default setting.
_netdev         this is a network device, mount it after bringing up the network. Only valid with fstype nfs.
fmask           file permission mask (for vfat/ntfs). fmask=0111 means world readable,writable
dmask           directory permission mask (for vfat/ntfs). dmask=0000 means world readable,writable,executable
sync/async   	All I/O to the file system should be done (a)synchronously.
```

My information comes from [bodhi.zazen's excellent How to fstab tutorial]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by Rabidmonkey1 on 2008-05-30
Thanks again for the response!  That's a handy bit of info there.  

This is what's going on now:  Both drives automount when I boot, and I don't have the privilege to unmount either, even after making those new changes to the fstab.  When I gksudo nautilus, and look at the properties of the drives, and then go to the "Permissions" tab, it reads that the permissions of the drives could not be determined...

I'm halfway there, and could live with the drives automounting like this, but why on earth is it not letting me unmount them?  Like you said, the user option should allow for that...

---

### Post by unutbu on 2008-05-30
Ah. I think I know. When the hard drive partitions get mounted at boot, it is root that is doing the mounting. So root is the only user that gets permission to unmount.

If we set it up so these partitions are not mounted at boot, then a normal user will have the opportunity to mount them as desired, and will then have the privilege to unmount them too.

Try this:
```
# /etc/fstab: static file system information.
#
# <file system>                            <mount point>  <type>       <options>                             <dump>  <pass>
proc                                       /proc          proc         defaults                                   0  0  
# /dev/sda1
UUID=483835a4-10ed-4b28-aa0e-309daab4dd0f  /              ext3         defaults,errors=remount-ro                 0  1  
# /dev/sda5
UUID=5739bd42-d709-48f9-bbba-1eafd78a4b10  none           swap         sw                                         0  0  
/dev/sdb1                                  /media/sdb1    ntfs-3g      noauto,user,fmask=0111,dmask=0000          0  0  
/dev/sdc1                                  /media/sdc1    ext3         rw,suid,dev,exec,noauto,user,async         0  0
```

I changed 'auto' to 'noauto' so the partitions won't mount at boot.

---

### Post by Rabidmonkey1 on 2008-06-15
Awesome!  Thanks a lot for your help!  Sorry I took so long to respond, there's been so much going on, but now my comp works much more like I wanted it to, and those links really helped me understand the FSTAB configuration options!!!  Thanks again!!:KS

---

### Post by Rabidmonkey1 on 2008-07-08
Hey there, sorry, one last question...

Recently I tried to mount my windows partition, sdb1, but I received an error, which read:


```
Unable to mount the volume. 

[mntent]: line 9 in /etc/fstab is bad.
mount: can't find /media/sdb1 in /etc/fstab or /etc/mtab
```


I'd like to be able to still manually mount sdb1 when I click on it.  I went into the fstab file to try to determine what's wrong, but I'm not experienced enough to notice anything.  Here is the fstab.  Any ideas?

```
# /etc/fstab: static file system information.
#
# <file system>                            <mount point>  <type>       <options>                      <dump>  <pass>
proc                                       /proc          proc         defaults                            0  0  
# /dev/sda1
UUID=483835a4-10ed-4b28-aa0e-309daab4dd0f  /              ext3         defaults,errors=remount-ro          0  1  
# /dev/sda5
UUID=5739bd42-d709-48f9-bbba-1eafd78a4b10  none           swap         sw                                  0  0  
/dev/sdb1                                  /media/sdb1    ntfs-3g      noauto, user,fmask=0111,dmask=0000  0  0  
/dev/sdc1                                  /media/sdc1    ext3         rw,suid,dev,exec,auto,user,async    0  0
```

---

### Post by unutbu on 2008-07-08
A line in fstab must be composed of six fields separated by spaces. (Lines beginning with # are ignored).

The line referring to sdb1:
> 
/dev/sdb1                                  /media/sdb1    ntfs-3g      noauto, user,fmask=0111,dmask=0000  0  0  

has a space between "noauto," and "user".
Remove the space.

---

