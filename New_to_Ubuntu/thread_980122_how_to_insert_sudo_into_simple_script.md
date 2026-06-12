---
title: "how to insert sudo into simple script?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by ferral-cat on 2008-11-12
Hi,

I want to create a simple script to mount my Windows hard-drive.

Here is the script but I want to just be able to double click on the script and have it launch without asking for the sudo password.  

```
#!/bin/sh
mkdir /mnt/WindowsXP
mount -t ntfs /dev/sda2 /mnt/WindowsXP

```

Then I did this:
```
chmod 755 mount_windows.sh
```

But still it gives me error:

```
daka@daRk-deSkTop:~/Desktop$ sh mount_windows.sh 
mkdir: cannot create directory `/mnt/WindowsXP': Permission denied
mount: only root can do that

```

---

### Post by markjensen on 2008-11-12
Options:
Have the ntfs partition mount declared in fstab automatically every time.
Have it in fstab, but with "user" as an option, so users can mount it.

This may help: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by bodhi.zazen on 2008-11-12
Well, this is a bad idea. Any script that runs with root permissions should be owned by root and run by root.

I would venture that the best solution is to configure fstab so that you can mount your partition as a user. Use the options noauto (or auto to automatically mount it at boot) and users.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

You can also use ntfs-config

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

Second options is to make the script , ownership set to root and edit /etc/sudoers (with visudo) to run the command without a password.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)
[indent]look at the bottom of the page[/indent]

[http://linux.die.net/man/8/visudo](http://linux.die.net/man/8/visudo)

Third option is to use expect.

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

    [http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

### Post by kerry_s on 2008-11-12
how about this:
```
#!/bin/sh
mkdir /tmp/WindowsXP
pmount -t ntfs /dev/sda2 /tmp/WindowsXP
ln -s /tmp/WindowsXP ~/Desktop/WindowsXP
```

no permission needed. to unmount> "pumount /tmp/WindowsXP"

man pmount
man pumount

to learn more about user mounting.

---

### Post by bodhi.zazen on 2008-11-12
Nice. You need to make a small edit to a config file for pmount (to enable hard drives, pmount is usually used for removable media). Or at least the last time I tried pmount with an internal hard drive :rolleyes:

[http://ubuntuforums.org/showpost.php?p=1487054&postcount=3](http://ubuntuforums.org/showpost.php?p=1487054&postcount=3)

Also pmount uses /media

So

pmount /dev/sdxy Windows

will mount the drive in /media/Windows (no need for /tmp/Windows or mkdir /media/Windows).

---

### Post by kerry_s on 2008-11-12
> **bodhi.zazen said:**
> Nice. You need to make a small edit to a config file for pmount (to enable hard drives, pmount is usually used for removable media). Or at least the last time I tried pmount with an internal hard drive :rolleyes:

[http://ubuntuforums.org/showpost.php?p=1487054&postcount=3](http://ubuntuforums.org/showpost.php?p=1487054&postcount=3)

Also pmount uses /media

So

pmount /dev/sdxy Windows

will mount the drive in /media/Windows (no need for /tmp/Windows or mkdir /media/Windows).

thanks, i forgot about /etc/pmount.allow. i haven't had to mount an internal drive in age's, the only thing i mount is the flash drive i keep my backups on. :)

---

### Post by kerry_s on 2008-11-12
okay, so here's the new instructions:
gksudo gedit /etc/pmount.allow
put:
/dev/sda2

for the script:
#!/bin/sh
pmount sda2
ln -s /media/sda2 ~/Desktop/WindowsXP

i think it might be better:
ln -s /media ~/Desktop/WindowsXP

which won't leave a broken link when you unmout.

---

### Post by ranthal on 2008-11-12
> **bodhi.zazen said:**
> Third option is to use expect.

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

    [http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

This thought crossed my mind too since a script doing something that typically requires root permissions really shouldn't be worked around.

The expect script would be fairly straightforward too, simply sudo ./mount.sh (forgot the name you used) then expect the password prompt and send it, should take care of the rest.

---

### Post by kerry_s on 2008-11-12
the way i have mine is,  i have a link to media, so when i want to access my flash drive, i just do "pmount sda1" in terminal, then go into my media-link folder, i just right click> unmount when i'm done, cause i have pumount set in rox. i might add a little script in there so i can skip the terminal. :)

---

### Post by ferral-cat on 2008-11-12
I added this line to /etc/fstab/

```
/dev/sda2       /mnt/   ntfs   user,noauto,fmask=0111,dmask=0000   0   0

```

Then i tried to mount the drive as a normal user and get this error:

```
daka@daRk-deSkTop:~$ mount -t ntfs /dev/sda2 /mnt 
mount: only root can do that

```

What did I do wrong?

---

### Post by bodhi.zazen on 2008-11-13
when you have an entry in fstab you need only specify the device or mount point.

So ...

mount /dev/sda2

or

mount /mnt

---

### Post by ferral-cat on 2008-11-13
Thanks for the fast reply.  Now its giving me the following error:

```
daka@daRk-deSkTop:~$ mount /mnt
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```

I just want to be able to mount it without being sudo and without typing in the password basically.

---

