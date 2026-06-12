---
title: "Automount and Fstab revisited"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by JonWasHere42 on 2008-06-15
Ok, so i have gotten pretty comfortable with Fstab, and such. And i have a line in /etc/fstab that should mount the windows partition of my hard drive, with all the things i need on there. 

(Mostly its security since my computer is used by several users who i dont really want messing around in my windows folders.)

So here is my line from fstab:

> UUID=[its uuid] /media/disk ntfs async,atime,nodev,noexec,auto,nosuid,owner,ro,uid=1000,gid=1000,umask=227 0 0


The drive automounts at startup, in accordance with the auto option. And here is the mount in /etc/mtab:

> /dev/sda3 /media/disk fuseblk ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0

Obviously not what is laid out in fstab. Is there something else that mounts this drive, that i am unaware of? Somewhere else i should look?

Thanks
--Jon

---

### Post by ibuclaw on 2008-06-15
It looks correct from here Jon.

Remember, most the commands in your fstab line are aliases that activate other mount options.
ie:  users = noexec, nosuid, and nodev

Also, fstab and mtab are both isolated (ran by separate apps), so what they display may differ.

But it all seems to be there and working properly.

Regards
Iain

[EDIT]
FYI:
my FSTAB:
```
UUID=6AB0419AB0416E1F  /media/.sdb5  ntfs  defaults,umask=007,gid=46  0  1
```
my MTAB:
```
/dev/sdb5  /media/.sdb5  fuseblk  rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096  0  0
```

---

### Post by Rocket2DMn on 2008-06-15
This is what I use, and it has worked for everybody else, too:
```
UUID=[its uuid] /media/disk ntfs-3g defaults,locale=en_US.utf8 0 0
```
Note that it is "ntfs-3g" and not "ntfs", this is important.
Also check out
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
and
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by cariboo on 2008-06-15
If you have other people using your computer, why not set up a seperate account for them and just limit what they can do. Linux was designed as a multi-user platform and you can have as many users as you have room for.

To do this got to System-->Aministraation-->Users and Groups, unlock it using your password and just fill in the form. On The user privileges tab you just put cheek marks on the things that you would allow them to do. If they know your password of course you will have to change it

Then just logout when you are not using the computer. It is a little bit more hassle, but you are secure in knowing they can't get at your important data.

Jim

---

### Post by spiderbatdad on 2008-06-15
It is possible to have problems with umask if it is not set with octal values. In your case umask=0227

man umask

---

### Post by JonWasHere42 on 2008-06-16
Yes a lot of the keywords in fstab are aliases, however the ones at the end should take precedence over the earlier ones, so invoking uid and gid should be the last thing done. 

mtab is just a record of the mounted drives, so something is mounting this drive that is not fstab, and im not sure what is doing the mounting. 

As for changing user settings, i have done all that, now all there is left to do is to change the permissions of the drive itself, but since it has the 
allow_other,defaultpermissions
flags, it gives the drive r_x access to everyone. which defeats the purpose.

--Jon

---

### Post by Rocket2DMn on 2008-06-16
HAL can mount drives, but since you are using fstab, it is getting its mount options from there.  If you look at 
[code]man mount[code]
you can see a list of all available options.  Also, here is a nice resource for using fstab:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

