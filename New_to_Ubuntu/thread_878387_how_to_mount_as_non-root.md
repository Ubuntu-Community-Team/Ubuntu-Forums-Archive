---
title: "how to mount as non-root"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by finer recliner on 2008-08-02
i have an external hard drive (2 partitions both NTFS format) that I would like to be able to mount as a normal user (non-root). 

here is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=778f1cb7-6cef-4a90-b026-411bb9a4ab18 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b80255a8-4c3f-4054-b34c-9c32e2224eb1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#windows partition
UUID=421CDA391CDA2825 /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# seagate external hdd
UUID=1CB0533B31D885A5 /media/exta ntfs defaults,umask=007,gid=46,user 0 1
UUID=6FB11FB42F00284E /media/extb ntfs defaults,umask=007,gid=46,user 0 1


```

the 2 partitions i want to be able to mount is /media/exta and /media/extb


they both mount fine as is right now, but i need to use sudo, and i'd like to get rid of that extra step. any ideas?

---

### Post by sharks on 2008-08-02
IMHO i think u cant.

---

### Post by hovzio on 2008-08-02
I was hearing somthing about gnome-u/mount but this doesn't seem to work. (I may be doing somthing wrong) I have also found it troublesome only being able to mount as root. Any ideas, thanks:)

Edit: I am guessing that gnome-mount has something to do with automatically mounting devices when they are plugged in??

---

### Post by ibuclaw on 2008-08-02
Doesn't it mount when you go into "Places->Device Label"?

Regards
Iain

---

### Post by sharks on 2008-08-02
> doesn't it mount when you go into "places->device label"?

+1

---

### Post by K2712 on 2008-08-02
I was under the impression that as long as you had user in the fstab line, and the permissions on the mount point were set to 777 a user could mount?

---

### Post by dmm1285 on 2008-08-02
look up umask fstab, I can't remember the exact setting you need

---

### Post by finer recliner on 2008-08-03
it seems it was a problem with FUSES and ntfs-3g (since my drive is NTFS format):

[http://ntfs-3g.org/support.html#useroption](http://ntfs-3g.org/support.html#useroption)

i'd have to recompile ntfs-3g and do a couple other things, and i'd rather not get into all of that today.

thanks anyways guys.

---

### Post by finer recliner on 2008-08-03
i found an unexpected solution: editting my sudoers file.

if anyone else is interested, here are the changes i made to my /etc/sudoers file:

1) add this line under where it says "# Cmnd alias specification"
```
Cmnd_Alias      MOUNT         =/bin/mount, /bin/umount 
```


2) add your user under "#users" and what he is allowed to do:
```
user_name ALL=NOPASSWD: MOUNT 
```
(replace "user_name" with your real user name.)

if i understand it correctly, all i did was give my normal user account access to use the mount and umount commands. you still need to put sudo in front of the commands, but you will not be prompted for your password. logout & login to for changes to take effect.

please let me know if i accidentally gave myself more permission than expected ;)

---

