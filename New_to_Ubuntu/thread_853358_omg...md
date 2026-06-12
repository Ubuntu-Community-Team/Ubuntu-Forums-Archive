---
title: "omg.."
date: 2008-07-08
forum: New to Ubuntu
---

### Post by adamant715 on 2008-07-08
This OS is starting to really piss me of..lol Anyway when I tried to move a file into a folder it said this.

There was an error moving the file into /usr/share/gimp/2.0/brushes.
Error moving file: Permission denied

---

### Post by llama320 on 2008-07-08
you need root privileges to copy the file. You can do this by using the cp (copy) command from terminal (Applications > Terminal)

```
sudo cp file_you_want_to_move target_location
```

then just type in your password

Good Luck

---

### Post by Dr Small on 2008-07-08
Use sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by phidia on 2008-07-08
If you are sure you want to move that file there use sudo in front of the mv command.
Linux prevents you from messing up system files by only allowing the admin account to make system level changes.

---

### Post by kestrel1 on 2008-07-08
Go to the terminal & use:
```
sudo CP 'source file' /usr/share/gimp/2.0/brushes
```

---

### Post by snowpine on 2008-07-08
It's a feature, not a bug. :)

---

### Post by Frak on 2008-07-08
As said, its there to protect your computer from unauthenticated use. Yes, you are by default not able to use some things on there. It's a way to protect you from yourself.

use sudo to do most things, but if you use a graphical app, use gksudo instead. (kdesu on KDE systems).

---

### Post by kostkon on 2008-07-08
> **adamant715 said:**
> This OS is starting to really piss me of..lol Anyway when I tried to move a file into a folder it said this.

There was an error moving the file into /usr/share/gimp/2.0/brushes.
Error moving file: Permission denied
Why not just copy them to your own user folder for Gimp that exists in your home, i.e.:
```
~/.gimp-2.0/brushes
```

---

### Post by Paqman on 2008-07-08
> **Frak said:**
> 
use sudo to do most things, but if you use a graphical app, use gksudo instead. (kdesu on KDE systems).

In other words, if you want to use the normal file manager, launch it (Alt-F2) using the command: 

```

gksudo nautilus

```
Then copy away to your heart's content. Close the file manager as soon as you're done with the task that needs root privileges.

File permissions are a pain at first, but they're one of the reasons Linux is so secure. It's worth learning about how to use them properly.

---

### Post by roderick on 2008-07-08
THe location you are using is a system directory, and not the correct place to put this, unless you have a multiuser setup and truly want it available to all users. If it's just one user, then put it in your local directory as previously mentioned.

Hint, if the directory isn't /home/USERNAME, then you need root (i.e. sudo) priviledges to write to it - this is for your own protection and the sanity of the system.

---

