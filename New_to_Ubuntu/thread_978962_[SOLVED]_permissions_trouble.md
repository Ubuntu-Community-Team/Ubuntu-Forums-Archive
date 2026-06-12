---
title: "[SOLVED] permissions trouble"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by person8451 on 2008-11-11
I have been searching around here and have not yet found a way to change permissions on a bunch of folders at once.  I have a bunch of folders in Music that I would like to be able to move/delete/whatever, and the only way I can do it now is to "gksudo nautilus" and change them one at a time.

Every time I copy a music file I have saved on CD/DVD, it acts like this.  I don't know if I am doing it wrong or what.  It seems weird that I cannot just "own" the damn things to begin with.

Anyhow, if there is some way to quickly claim ownership of everything in my Music folder, that would save me much hassle.  I can do it one folder at a time if I have to, but I am hoping there is a command that will accomplish it faster.

(Hardy 8.04 btw)

---

### Post by MuH4hA on 2008-11-11
You can do this with

```
chown username -R /home/yourmusicfolder
``` to get ownership and

```
chmod -R 755 /home/yourmusicfolder
``` to change permissions

---

### Post by newbee70 on 2008-11-11
> **person8451 said:**
> I have been searching around here and have not yet found a way to change permissions on a bunch of folders at once.  I have a bunch of folders in Music that I would like to be able to move/delete/whatever, and the only way I can do it now is to "gksudo nautilus" and change them one at a time.

Every time I copy a music file I have saved on CD/DVD, it acts like this.  I don't know if I am doing it wrong or what.  It seems weird that I cannot just "own" the damn things to begin with.

Anyhow, if there is some way to quickly claim ownership of everything in my Music folder, that would save me much hassle.  I can do it one folder at a time if I have to, but I am hoping there is a command that will accomplish it faster.

(Hardy 8.04 btw)

I'm just a noob so take this with a grain of salt.

Have you checked out the man page for chown -R

W.

Dang, beat out by MuH4hA

---

### Post by Coreigh on 2008-11-11
Chown will set the owner, but if you are trying to grant permissions to other users or a network share you will want to look at chmod as well.```
man chmod
```

in terminal window or in Google.

---

### Post by person8451 on 2008-11-11
Thanks that did it.  :)

---

