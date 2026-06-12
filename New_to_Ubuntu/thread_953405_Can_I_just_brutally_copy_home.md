---
title: "Can I just brutally copy /home?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by ginestre on 2008-10-20
Can I just brutally copy /home, and then paste it back later if my upgrade from 7.10 to 8.04 works out? 

And if I can, will I be able to paste it back into an entirely different location from its present home? I've learned so far on my ubuntu journey that I should originally have set /home up on a different partition to keep it safe from updates etc, so I'd like to do that now, too.

---

### Post by Jaded Misanthrope on 2008-10-20
I don't see why you can't back it up and replace your files later on, no.

Actually mounting it could be awkward, and you may have to reinstall from media of your choice to do that, select a partition to mount as /home and dump your backup there.

---

### Post by drowner on 2008-10-20
Here is an excellent guide on how to make a seperate /home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by geirha on 2008-10-20
Depends if permissions and ownership are preserved when copying. Don't copy directly to a FAT or NTFS filesystem for instance, since they don't support this type of ownership and permissions. If you need to copy to a NTFS, archive it with tar as the root user. That will preserve ownership and permissions.

The following will archive everything inside /home to /media/disk/home-backup.tar.bz2. You may get some warnings when doing this for various reasons. .gvfs will usually give you a warning, and if you are browsing the web while doing it, you'll get some warnings about files changing (browser cookies and cached pages) while archiving. They are mostly safe to ignore. If in doubt, post the warnings here and ask for a second opinion :)
```
sudo tar jcf /media/disk/homes-backup.tar.bz2 /home
```

To extract it again:
```
cd /
sudo tar jxf /media/disk/home-backup.tar.bz2
```

However, upgrading will not overwrite /home. Installing the newer Ubuntu release over the old one will though.

---

### Post by kellemes on 2008-10-20
> **ginestre said:**
> (..) I've learned so far on my ubuntu journey that I should originally have set /home up on a different partition to keep it safe from updates etc, so I'd like to do that now, too.

Not needed at all..
If updates do destroy valuable data in /home it will be done no matter what /home's location is..

---

### Post by ginestre on 2008-10-20
I have run into a silly problem. As suggested by geirha above, I'm backing up to a WD external drive I have, which has kept its manufacturer's name of My Book. So I substituted the name of the drive in the tar command, and ran (I think) into the problem of the existence of a space in the device name:

(operating system in Italian so excuse my rough translation of messages)
..........

richard@kids:~$ sudo tar jcf /media/My Book/homes-backup.tar.bz2
tar: Book/homes-backup.tar.bz2: Can't stat: No such file o directory
tar: Uscita per errore ritardata dall'errore precedente (Exiting because of error which was made later by preceding error (?))
richard@kids:~$ 

..............

Is there some way to cope with this?

---

### Post by geirha on 2008-10-20
It's because of the space in the directory "My Book". Make sure the space is escaped with a \ in front OR put the full path inside quotes ""

```
sudo tar jcf [COLOR="Red"]"[/COLOR]/media/My Book/homes-backup.tar.bz2[COLOR="Red"]"[/COLOR] /home
```

EDIT: Also, to avoid getting the error messages translated to your locale (which is unreadable to me), you can put "LANG=C" in front of the entire command.

e.g.:
```
LANG=C sudo tar jcf ....
```

---

### Post by Sef on 2008-10-20
> I have run into a silly problem. As suggested by geirha above, I'm backing up to a WD external drive I have, which has kept its manufacturer's name of My Book.

I would use either [Partimage]("http://partimage.org/Main_Page") or [Clonezilla]("http://clonezilla.org/").

---

### Post by gn2 on 2008-10-20
If you save your hidden configuration files to use later with a new installation, remember to use the same username and password when creating the new installation that you used for the old one.

---

### Post by AndyCooll on 2008-10-20
> **kellemes said:**
> Not needed at all..
If updates do destroy valuable data in /home it will be done no matter what /home's location is..
It's why it's always adviseable to make backups of everything, including your separate /home partition if you have one.

:cool:

---

### Post by kellemes on 2008-10-20
> **AndyCooll said:**
> It's why it's always adviseable to make backups of everything, including your separate /home partition if you have one.

:cool:

Indeed.. It's backups that may save your data, not the original location of data.
A separate /home-partition may be handy if you want to share one /home across several distro's. But even that is not advisable.
Or if you insist on cloning (clonezilla, partimage etc..) to create your backups.

---

### Post by AndyCooll on 2008-10-20
> **kellemes said:**
> Indeed.. It's backups that may save your data, not the original location of data.
A separate /home-partition may be handy if you want to share one /home across several distro's. But even that is not advisable.
Or if you insist on cloning (clonezilla, partimage etc..) to create your backups.
Nope. A separate /home partition is useful if you want to do a fresh install (not just an upgrade) and keep your old settings. I've done this quite a few times without any problems. 

And very often a separate /home partition is useful if you have errors and need to a re-install. It's only _not_ useful if the error is actually a config file that's in your /home partition. That's when you need your backup.

:cool:

---

### Post by Duck2006 on 2008-10-20
Why not make a home partition and move your old home to the new one so when you reinstall or upgrade you still have your settings.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

