---
title: "[Hardy] Mounting share at bootup?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by antmenj on 2008-11-23
I want to mount some shares at boot up on hardy.  How do I do it.
On Dapper you could put a folder on the desktop with the connect to server function and it would stay after reboot.  I worked out how to mount them with a launcher but would rather do it automaticly.

They mount as smb://URI at present.

Can I add script to a autoexec.bat type file and if so which one.

---

### Post by talsemgeest on 2008-11-23
Well, I'm not sure how to get it to mount, but if you have the command/commands that can do what you want, and want it to do it every startup you can just put the commands into a shell script and add that to startup.
If you need help doing that please ask.

Hope this helps :)

---

### Post by antmenj on 2008-11-24
I don't have all the commands but I'd still like to know where to put them if I did.

I'm sure there is a file with a startup script but I don't know which one it is.

---

### Post by talsemgeest on 2008-11-24
I'm not sure but it is easy enough to make one yourself. Just add all of the commands into a text file, and save it as something like "startup.sh". Then right-click the file, go to the permissions tab and check "allow executing this file as a program."

Then you just have to go to  System>Preferences>Sessions and add the file to that.

---

### Post by antmenj on 2008-11-24
Any takers on my question of how to make a connection to server stick as was possible under dapper.  At present I can't even connect to a server via places ---> connect to server as I could in dapper.

PS thanks for the info on startup.

---

### Post by DieB on 2008-11-24
well there is a way to edit > /etc/fstab , that it will mount network shares on boot up here is how:

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

hope it helps:

p.s. use cifs and not smbfs (you will see)

p.p.s: for all of you hungry for beans - do the research so you earn them, plus ou keep the forum clean of lousy "yeah there is a way - but i don't know either"

---

### Post by antmenj on 2008-12-23
Well I still haven't got this one sorted.

This is my fstab file before:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=82c0b1c7-3d9d-497e-b4b3-5c1350853996 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3c249123-89bc-4d0a-9be8-3d32f2b7b408 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I did ```
sudo mkdir /media/mountname
``` and it made a folder owned by root.

I added ```
//old/dskshr  /media/mountname  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```to fstab & tryed numerous variations on that including swaping unicode for cp850.

That didn't work.

I did ```
sudo apt-get install smbfs
``` but that didn't help but do we need that with cifs?

If I do get this to work will it be read only seeing its owned by root.  I want read write access.

I also tryed a different approach in another thread but got no answers.

Any help would be appreciated....

---

