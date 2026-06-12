---
title: "how to make a backup of /etc/x11/xorg.conf"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by bilbo.san on 2008-05-03
Hey,

I was able to install the nvidia setting for my video card, changed the res successfully. But I read somewhere in this forum that I should make a backup of the /etc/x11/xorg.conf just in case something goes wrong with the video settings, I have already installed the pack and changed the res twice and returned to the original just now to make this back up.

Is it something you would recommend?
How do I do that?

b.

---

### Post by damis648 on 2008-05-03
in terminal type

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

and the backup is stored as xorg.conf.backup in /etc/X11/

---

### Post by Monicker on 2008-05-03
It never hurts to have a backup copy of xorg.conf, especially if you start making changes to it.

```
cp /etc/X11/xorg.conf /some/safe/place/xorg.conf.backup
```

Or just copy/paste via the Nautilus file browser.

---

### Post by aheckler on 2008-05-03
To backup to your home directory:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

EDIT: Shoot! Third!

---

### Post by bilbo.san on 2008-05-03
Thanks !
I just did that, requested my user pass and it did not reported anything, I mean, I dont know, no saved file but no errors either... was it successful?

b.

---

### Post by aheckler on 2008-05-03
Yes, that is normal. It succeeded. To see for yourself, open up the file browser and go to the etc folder, then X11, and there should be a file called xorg.conf as well as a file called xorg.conf.backup.

---

### Post by bilbo.san on 2008-05-03
GREAT GREAT!!!

Thanks
b.

---

### Post by aktiwers on 2008-05-03
> **bilbo.san said:**
> Thanks !
I just did that, requested my user pass and it did not reported anything, I mean, I dont know, no saved file but no errors either... was it successful?

b.

Yes it was, you can check it by typing:
```
ls /etc/X11/
```

It shows the files in that folder, and the one you backed up should be called "xorg.conf.backup".

The command means:
sudo = gives you super user rights
cp = copy
 /etc/X11/xorg.conf = the file you want to copy
/etc/X11/xorg.conf.backup = where you want to copy it.

So to reverce back to your backup you could do like this:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by bilbo.san on 2008-05-03
> **aktiwers said:**
> Yes it was, you can check it by typing:
```
ls /etc/X11/
```It shows the files in that folder, and the one you backed up should be called "xorg.conf.backup".

The command means:
sudo = gives you super user rights
cp = copy
 /etc/X11/xorg.conf = the file you want to copy
/etc/X11/xorg.conf.backup = where you want to copy it.

So to reverce back to your backup you could do like this:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Hey,
This is great info... it is good to know what's that mean, I was actually looking for a manual or something to help understand these coding.

Thank you!

---

### Post by aheckler on 2008-05-03
> **bilbo.san said:**
> Hey,
This is great info... it is good to know what's that mean, I was actually looking for a manual or something to help understand these coding.

Thank you!

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) ;)

---

