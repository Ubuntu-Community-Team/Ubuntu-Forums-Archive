---
title: "using sudo from command line."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by kzamora on 2008-05-20
Hi,

I entered sudo (from gnome GUI) to copy a file but it doesn't seem to work? Here is a transcript of what I did.

kevin@kevin-desktop:/etc/apt$ sudo cp sources.list sources.list.orig
sudo: /etc/sudoers is mode 0777, should be 0440
kevin@kevin-desktop:/etc/apt$ more sources.list.orig
sources.list.orig: No such file or directory
kevin@kevin-desktop:/etc/apt$ ls -lh
total 36K
drwxr-xr-x 2 root root 4.0K 2008-05-15 17:38 apt.conf.d
-rw------- 1 root root    0 2007-10-15 16:18 secring.gpg
-rw-r--r-- 1 root root 3.0K 2008-05-15 16:12 sources.list
drwxr-xr-x 2 root root 4.0K 2007-10-15 13:40 sources.list.d
-rw-r--r-- 1 root root 3.0K 2008-05-15 16:12 sources.list.distUpgrade
-rw------- 1 root root 1.2K 2008-05-15 17:40 trustdb.gpg
-rw-r--r-- 1 root root 6.6K 2008-05-15 17:40 trusted.gpg
-rw-r--r-- 1 root root 6.6K 2008-05-15 17:40 trusted.gpg~
kevin@kevin-desktop:/etc/apt$ ls -af
..            trustdb.gpg  sources.list.d  sources.list.distUpgrade
trusted.gpg~  trusted.gpg  sources.list
.             secring.gpg  apt.conf.d



I changed the permission on /etc/sudoers file from the recovery console (just experimenting) but I am unable to do anything from GUI, terminal window. Here I tried to change the permissions back. Interestingly, I don't get asked for a password.

kevin@kevin-desktop:/etc$ sudo chmod 440 /etc/sudoers
sudo: /etc/sudoers is mode 0777, should be 0440
kevin@kevin-desktop:/etc$ ls -l sudoers
-rwxrwxrwx 1 root root 496 2008-05-15 07:11 sudoers
kevin@kevin-desktop:/etc$

---

### Post by john91 on 2008-05-20
at the grub bootloader that comes up when you boot your computer (i'm assuming you installed grub along w/ ubuntu), you'll want to select and boot into the recovery option.  from there, you'll be entered as root, and so you won't need to sudo anything.  from there, change the permissions on /etc/sudoers simply with this command:

```
chmod 440 /etc/sudoers
```

That should resolve the permissions problem, but you may have another problem underlying that one.  If this doesn't work, post your /etc/sudoers file and we'll see what we can do.

---

### Post by danny_nero on 2008-05-26
I had a complete different problem but you helped a lot. Thanx anyway.
danny

---

