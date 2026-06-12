---
title: "Can't access cdrom, cdrom0 and some other folders like lost and found"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by kayfes on 2008-06-09
I get this message:

You do not have the permissions necessary to view the contents of "cdrom0".

---

### Post by gr4nf on 2008-06-09
in the terminal, type this:
```

sudo cd /media/cdrom0

```
it will ask for a password. that will get you into the directory. To list it's contents, type "ls"

---

### Post by kayfes on 2008-06-09
Tried that and got:

steven@steven-desktop:~$ sudo cd /media/cdrom0
sudo: cd: command not found

---

### Post by gr4nf on 2008-06-09
try this:

run "sudo chmod 777 /media/cdrom0".
enter your password when prompted.
That should allow you to open it up normally, i.e. through the desktop environment file browser (nautilus).

---

### Post by kayfes on 2008-06-09
I think it must be the CD I was trying to access as I put in another disc and it worked.  Thank you.

---

### Post by gr4nf on 2008-06-09
No problem, sorry i couldnt help.

---

### Post by kayfes on 2008-06-09
Why do I have cdrom cdrom0 and cdrom2?  Both cdrom and cdrom0 show the same disc.

---

### Post by atoponce on 2008-06-09
> **gr4nf said:**
> try this:

run "sudo chmod 777 /media/cdrom0".
enter your password when prompted.
That should allow you to open it up normally, i.e. through the desktop environment file browser (nautilus).

No no no.  There is no need to set the write bit on the other category for permissions in this troubleshooting exercise.  This is a perfect example of bad administration.

First, mount /dev/cdrom to /mnt, and see if you can access the contents of /mnt (of course assuming that a CD is in the CDROM):

```
sudo mount -t iso9660 /dev/cdrom /mnt
```

If we still get permission denied, then print out the permissions, and check the relative permissions to your user account:

```
ls -ld /mnt
```

What category do you fit in as the unpriveledged user?  Are you the owner?  Do you belong in the group that has access?  You probably are under "other" if you have the following permissions:

```
ls -ld /mnt
dr-xr-xr-x 3 root root 4096 2008-06-08 15:07 /mnt
```

Further, you mention in your post title that you have having trouble with the lost+found folder permissions.  There should be no reason why you are poking around in the lost+found folder, unless you have recovered data from your filesystem as a result of bad or inconsisten blocks.  Hopefully, you didn't remove the lost+found directory.  If so, as root, you can execute the 'mklost+found' command to rebuild the directory.

---

### Post by kayfes on 2008-06-09
so what i get for the first two codes:

steven@steven-desktop:~$ sudo mount -t iso9660 /dev/cdrom /mnt
mount: block device /dev/scd0 is write-protected, mounting read-only
steven@steven-desktop:~$ ls -ld /mnt
drwx------ 3 400 401 2048 2005-09-23 02:04 /mnt


I didn't touch the lost and found I just noticed that the Lost and found folder has an X on it like the Cdrom folder and subsequently the cdrom and cdrom0.

---

### Post by kayfes on 2008-06-09
Now I can't even open my CD drive.  It says:

There is probably no media in the drive.

---

### Post by gr4nf on 2008-06-09
You could try:
```
sudo umount /dev/cdrom
```
but i don't think that that's the problem. It *should* unmount it for you upon the request for ejecting. If that doesn't work, your guess is as good as mine.

---

### Post by MegaJim on 2008-06-09
have you tried ```
eject /media/cdrom
```

---

### Post by atoponce on 2008-06-09
Who is UID 400 and GUD 401?  Those are not standard on an Ubuntu install, so I'm curious where they're coming from.  Further, what UID is your user?  I would assume 1000, as is default on standard Ubuntu installations.

---

### Post by kayfes on 2008-06-09
Ok I got the Cd to eject but thats not really the point as I still am unable to access its contents.

I don't know what you mean exactly "Who is UID 400 and GUD 401?"  and I don't know how to find mine.

---

### Post by kayfes on 2008-06-09
Ok figured out what UID is and I don't know who UID 400 and GUD 401 are.  If I have a UID of 1000 wouldn't that mean they have more access rights than I do?

---

### Post by atoponce on 2008-06-09
> **kayfes said:**
> Ok figured out what UID is and I don't know who UID 400 and GUD 401 are.  If I have a UID of 1000 wouldn't that mean they have more access rights than I do?

UID = user ID, GID = group ID.  Your Ubuntu box doesn't care about the user "foo" (or whatever your username is).  All it cares about is the unique identifier that your account has been given.  You can see your user ID with the "id" command:

```
id
uid=1000(aaron) gid=(1000) groups=4(adm),20(dialout),24(cdrom),35(floppy), ... (snip)...
```

To get the information on user ID 400 and group ID 401:

```
grep 400 /etc/passwd; grep 401 /etc/passwd
```

---

### Post by kayfes on 2008-06-10
I was trying to get Quake 4 to run on my PC when this happened.

[http://ubuntuforums.org/showthread.php?t=823268&highlight=quake+wine](http://ubuntuforums.org/showthread.php?t=823268&highlight=quake+wine)

---

### Post by kayfes on 2008-06-10
Ok so grep 400 /etc/passwd and grep 401 /etc/passwd don't me anything and yes my id is 1000.  I am the only user on this computer.

All I want to do is get Quake 4 running so I can try out my new GPU.

Thank you for your help.

---

### Post by cariboo on 2008-06-10
You've probably got your CD mounted in a couple of places. Try:

```
sudo umount /mnt
```

you should be able to eject it now.

Jim

---

### Post by kayfes on 2008-06-10
But I am trying to figure why I can't access the cds so I can get quake running.

---

### Post by atoponce on 2008-06-10
You still haven't told me who UID 400 and GID 401 are.

---

### Post by kayfes on 2008-06-10
Not sure how to find out who they are.

---

### Post by atoponce on 2008-06-10
I told you how to find out in a previous post.  However, it's no matter.  GNOME (or KDE) will automount the CDROM for you, and mount it to /media/cdrom or some other name, if the CDROM filesystem has a label.  You just need to be logged in a GNOME (or KDE).

---

### Post by kayfes on 2008-06-10
I am the only user on here so I have no idea why there is another UID.

---

### Post by gr4nf on 2008-06-10
When you insert your cd-rom, does it make an icon on the desktop? If so, what happens when you attempt to open it?

---

### Post by kayfes on 2008-06-10
Well I am totally lost here.  I was able to copy the files from the first cd yesterday then I ran into this problem and was unable to continue copying the needed files so I could play.  How Do I login into GNOME to get the other files?

---

### Post by kayfes on 2008-06-10
It does make an icon on the desktop and when I try to access the cd it says:

You do not have the permissions necessary to view the contents of "cdrom0".

---

### Post by kayfes on 2008-06-10
I don't understand why I can't access the cd drive.

---

### Post by togaclad on 2009-02-15
I know this is late but I ran into the same issue and took me a bit to deal with it.

Quick recap:
I was trying to install call of duty 2. I figured, copy the disks to my hard drive and and start the install. The first disk copied fine but when I try to mount disk 2 onward, I can't access the drive due to limited permissions. Checking the mounts I see my cdrom has mounted with uid 400 and gui 401.  The cd must be setting this some how. Trying to use sudo does not work.

The only thing I found that worked was to do this:
"sudo su"   and enter your passwd - your are now root
"cd <dir you want to copy to>"
"mount /media/cdrom0"
"cp  -r /media/cdrom0/* ."
"umount /media/cdrom0"
"eject"
change disks and continue back to the mount step.  Once all your files are copied you may need to chown them to your user name or chmod the permissions as they will all be owned by root.

As for why/what this 400/401 business is all about, you got me. Perhaps a security feature.

Good luck.

---

