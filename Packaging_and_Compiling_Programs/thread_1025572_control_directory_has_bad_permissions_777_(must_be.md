---
title: "control directory has bad permissions 777 (must be &gt;=0755 and &lt;=0775)"
date: 2008-12-30
forum: Packaging and Compiling Programs
---

### Post by god0fgod on 2008-12-30
I get that error when trying to make a debian package. I got this before when helping someone else work out how to make a debian package and I fixed it by changing the DEBIAN folder and the control file to permissions 0775. I tried the same thing again with the command:

```

sudo chmod -R 0755 '/home/matt/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN'
```

I tried to build the .deb file with:

```
sudo dpkg -b '/home/matt/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev' guessing_game.deb
```

It gives:

```
dpkg-deb: building package `guessing-game' in `guessing_game.deb'.
dpkg-deb: control directory has bad permissions 777 (must be >=0755 and <=0775)
```

The permissions don't seem to be changing correctly.

```
matt@matt-desktop:~/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN$ ls -l
total 1
-rwxrwxrwx 1 root root 387 2008-12-30 13:37 control
matt@matt-desktop:~/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN$ sudo chmod 0775 control
matt@matt-desktop:~/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN$ ls -l
total 1
-rwxrwxrwx 1 root root 387 2008-12-30 13:37 control
```

Can anyone help me? I'm not very good at this. I would just like to make it easy for people to install a nice python program I made.

Thanks.

---

### Post by dcstar on 2008-12-30
> **god0fgod said:**
> I get that error when trying to make a debian package. I got this before when helping someone else work out how to make a debian package and I fixed it by changing the DEBIAN folder and the control file to permissions 0775. I tried the same thing again with the command:

```

sudo chmod -R 0755 '/home/matt/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN'
```

I tried to build the .deb file with:

```
sudo dpkg -b '/home/matt/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev' guessing_game.deb
```

It gives:

```
dpkg-deb: building package `guessing-game' in `guessing_game.deb'.
dpkg-deb: **control directory** has bad permissions 777 (must be >=0755 and <=0775)
```

The permissions don't seem to be changing correctly.

```
matt@matt-desktop:~/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN$ ls -l
total 1
-rwxrwxrwx 1 root root 387 2008-12-30 13:37 control
matt@matt-desktop:~/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN$ sudo chmod 0775 control
matt@matt-desktop:~/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN$ ls -l
total 1
-rwxrwxrwx 1 root root 387 2008-12-30 13:37 control
```


Is say control directory, not the control file.

---

### Post by eBoxNet on 2008-12-30
i think ```
sudo chmod 755 /home/matt/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev
``` it may solve your prob..

---

### Post by god0fgod on 2008-12-31
After adding quotes around the directory it has no effect. Thank you for suggesting that though.

```
matt@matt-desktop:~$ sudo chmod 755 '/home/matt/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev'
matt@matt-desktop:~$ ls -l '/home/matt/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev'
total 0
drwxrwxrwx 1 root root 0 2008-12-29 22:05 bin
drwxrwxrwx 1 root root 0 2008-12-30 13:36 DEBIAN
drwxrwxrwx 1 root root 0 2008-12-29 22:05 usr
matt@matt-desktop:~$ ls -l '/home/matt/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN'
total 1
-rwxrwxrwx 1 root root 387 2008-12-30 13:37 control

```


Can I simply say ubuntu has bust?

And dcstar I was changing the permissions for the directory but also recursively did the file inside it as well just in case.

Edit: I noted the command without the beginning 0 wasn't recursive so I tried -R but still no luck.

---

### Post by albinootje on 2008-12-31
> **god0fgod said:**
>  Edit: I noted the command without the beginning 0 wasn't recursive so I tried -R but still no luck.

I just searched in the two threads about this problem, and I didn't find the "NTFS" mentioned.

Is this a FAT32 partition ?
If so... you can forget working with UNIX alike permissions
In FAT32, the ancient primitive FS inherited from the DOS era, basically everything is 777, there's only 1 owner, and that's everyone who has access to that partition :(

Or is this NTFS ? Then you have more luck.
Then you can try mounting that partition with uid=your_uid,gid=your_gid
Where your_uid and your_gid are probably 1000
First user created during an Ubuntu installation gets uid and gid 1000.

---

### Post by god0fgod on 2009-01-01
Wow. I completely forgot that I placed these files on the NTFS. Ack! If It were my decision there wouldn't be Windows at all on this machine.

Thank you for pointing out the obvious. I'll simply move the stuff to be used on ext3 which is easiest.

Thank you so much.

---

