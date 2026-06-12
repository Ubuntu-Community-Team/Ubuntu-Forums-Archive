---
title: "cannot open usershare directory /var/lib/samba/usershares"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by happyisland on 2008-08-02
For some reason HAL doesn't auto-mount my mp3 player (iriver's lplayer) which means i have to mount it manually. I then use the command 'sudo gnome-open /mnt/lplayer' to open a folder so I can drag and drop files. This works, but I get the following error message in the terminal window:

~$ Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:7440): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


What is that all about? Can anyone help me get my computer running the way it should? 
Thanks in advance,

---

### Post by eightmillion on 2008-08-02
Try this. Run these commands:
```
sudo newgrp sambashare
sudo adduser `whoami` sambashare
```
Then log out and log back in.

---

### Post by ibuclaw on 2008-08-02
How does the lplayer connect to your PC?

---

### Post by happyisland on 2008-08-02
> **eightmillion said:**
> Try this. Run these commands:
```
sudo newgrp sambashare
sudo adduser `whoami` sambashare
```
Then log out and log back in.

Here's what it says when I do the sudo newgrp sambashare part:

unknown group: sambashare

---

### Post by happyisland on 2008-08-02
> **tinivole said:**
> How does the lplayer connect to your PC?

It is connected via usb. When i plug it in I have to manually mount it using the command 'sudo mount -t vfat /dev/sde /mnt/lplayer'

---

### Post by eightmillion on 2008-08-02
That should have been this:
```
sudo groupadd sambashare
sudo adduser `whoami` sambashare
```

---

### Post by ibuclaw on 2008-08-02
> **happyisland said:**
> It is connected via usb. When i plug it in I have to manually mount it using the command 'sudo mount -t vfat /dev/sde /mnt/lplayer'

Try this instead :)
```
sudo mount /dev/sde -o shortname=mixed,uid=$(id -u),utf8,umask=077,exec,flush /mnt/lplayer
```
[EDIT]
unmount the device first, if that doesn't work. append "remount" onto the options list.

You should now be able to access the drive without root privileges.

Regards
Iain

---

### Post by eightmillion on 2008-08-02
You'll probably have to install samba too if it's not installed already.
> sudo apt-get install samba

---

### Post by happyisland on 2008-08-02
> **eightmillion said:**
> That should have been this:
```
sudo groupadd sambashare
sudo adduser `whoami` sambashare
```

Ok, I did that and logged out, logged back in, and I'm still getting the same error...

---

### Post by happyisland on 2008-08-02
> **eightmillion said:**
> You'll probably have to install samba too if it's not installed already.

This is why I still post in beginner forums. Now that samba is installed it works, no errors. Thanks for the help!

---

### Post by eightmillion on 2008-08-02
No problem. :)

---

### Post by happyisland on 2008-08-02
woops! Not so fast! Now, when I type sudo gnome-open /mnt/lplayer it opens the folder, but in the terminal window I get the following message instead of the samba one I used to get:

:~$ Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:9093): WARNING **: Unable to add monitor: Operation not supported

---

### Post by happyisland on 2008-08-02
> **tinivole said:**
> Try this instead :)
```
sudo mount /dev/sde -o shortname=mixed,uid=$(id -u),utf8,umask=077,exec,flush /mnt/lplayer
```
[EDIT]
unmount the device first, if that doesn't work. append "remount" onto the options list.

You should now be able to access the drive without root privileges.

Regards
Iain

I tried this and it seems to do functionally the same thing as the 'sudo mount -t vfat /dev/sde /mnt/lplayer' command I've been using. Could you please explain to me what the difference is between the two? 
Thanks!

---

### Post by eightmillion on 2008-08-02
You might try this...
> sudo chown -R `whoami`:`whoami`/mnt/lplayer
Then try to open it in a normal nautilus window. You should ideally create an entry in you fstab.

---

### Post by eightmillion on 2008-08-02
```
sudo mount /dev/sde -o shortname=mixed,**uid=$(id -u)**,utf8,umask=077,exec,flush /mnt/lplayer
```
The bold part there makes sure the filesystem is own by your current user and not root. That way you won't have to run a root nautilus to drop files on it.

---

