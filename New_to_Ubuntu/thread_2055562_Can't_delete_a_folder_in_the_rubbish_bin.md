---
title: "Can't delete a folder in the rubbish bin"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by nifty542 on 2012-09-09
Hi, all
Using asunder, I tried to rip a CD. I got an error message, so thought I would try again.
Now, I can't delete the folder or restore it.
I get the message: 
Automount failed: DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered

I don't know how to proceed.I'm using Lubuntu 12.04.
Thanks you, in advance.

David

---

### Post by Bashing-om on 2012-09-09
david; Hi ! Welcome to the forum.

  Do you not have two issues here ?

 To address the files:
Open a terminal (ctl+alt+t) and post the output of
```
ls /home/username/.local/share/Trash 
```replace username in the above with your actual username.
and advise the exact commands you have used to delete said files.
[ utilizing the terminal facilitates communications]

further advise pending:[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by nifty542 on 2012-09-11
Hi

Thanks for the reply. Actually, I hadn't tried the command line up to that point. The message I quoted appeared automatically when I right clicked on the folder and tried to click on delete.
I tried the commmand you suggested, and just got "files info" in blue.
Don't know if that helps.
Regards
David

---

### Post by Hadaka on 2012-09-11
Hi, your error Automount failed: DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered. Is saying that its in use and cant be mounted. To
display all your mountpoints->

```
mount -i 
```

then try deleting or removing that mountpoint, so you can delete your folder.

---

### Post by nifty542 on 2012-09-11
Hi

Thanks for the reply.
WhenI do that, I get:
david@david-System-Product-Name:~$ mount -i
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)

Sorry, but really don't know what to do next.

Regards
David

---

### Post by Hadaka on 2012-09-11
Hi, that output looks normal to me, do you have a space in the folder name?
or perhaps some typo you might have done? you can perhaps try the rm -f
option via terminal on the full path to the folder and see what happens. 
and just for good measure, power down and boot back up.

---

### Post by nifty542 on 2012-09-19
Hi
Thanks for the reply. Sorry for the long delay in getting back, work has got in the way.
I'm not sure what to do next- I can't restore or rename the folder. The title is what was downloaded in cddb lookup.
Anyway, not very familiar with the terminal.
Regards
David

---

### Post by nifty542 on 2012-09-19
Hi
Also, tried the rm command but no joy

Regards
David

---

### Post by hypnot0ad on 2012-09-19
```
cd ~/.local/share/Trash/files; rm -rf *

```

---

### Post by nifty542 on 2012-09-21
Hi
It worked!
Thank you very much. Really appreciate the help.
Regards
David

---

