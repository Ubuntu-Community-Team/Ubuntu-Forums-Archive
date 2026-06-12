---
title: "Unable to log into sudo and don't have su pw?"
date: 2015-04-11
forum: New to Ubuntu
---

### Post by Aphexlog on 2015-04-11
i was attempting to add a new group to the sudoers file... however, i did it in the wrong order.
I deleted my user from the sudoers file before adding him to the group that i added to the sudoers file.
I so not have a SU pw set up yet and I am unable to log in as sudo.
does anyone know of a way around? so that I can add my user back as sudo.
(FYI: I am the only user on the system)
Thank you,

---

### Post by nerdtron on 2015-04-11
Boot into a live CD and edit the sudoers file on your hard drive.

---

### Post by Aphexlog on 2015-04-11
Excellent idea, thank you

---

### Post by Aphexlog on 2015-04-11
Actually, it seems that I am unable to edit the sudoers via live disk because I do not have permission. I tried coping in to a flash drive so I can edit it on another computer, but can't because I do not have permission, nor can I edit permissions.

---

### Post by nerdtron on 2015-04-11
You can edit the sudoers file on the live mode.

```
 sudo nano /etc/sudoers 
```

Ctrl+O to save, Press enter.
Ctrl+X to exit

---

### Post by Bashing-om on 2015-04-11
Aphexlog; Hello;

2 other ^^ ways to gain access to that file.
1) from grub's boot menu -> recovery console -> root; and remount the root file system:
```

mount -o remount,rw /

```
2) from the liveDVD -> terminal -> gksu ( may have to install the utility) :
Mount the partition - say the file is on 'sda1'
```

sudo mkdir /mnt/access
sudo mount /dev/sda1 /mnt/access/
gksu gedit /mnt/access/<file>

```

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by TheFu on 2015-04-12
**sudoedit** is a better/safer way to edit protected files.

---

