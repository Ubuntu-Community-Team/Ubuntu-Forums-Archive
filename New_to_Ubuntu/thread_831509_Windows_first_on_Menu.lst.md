---
title: "Windows first on Menu.lst"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by mitzelpick on 2008-06-16
Don't shoot me !

Is it possible to edit the Menu.lst to list a different OS at the top of the list ? 

I want XP to be the default system and have UBUNTU as one of the choices. I have tried to edit the menu.lst and was told that I did not have "permission" to save the edited file. 

Is there an app or something that I need ?

---

### Post by swaknight on 2008-06-16
you should be able to but you need to do it like this:

```
sudo gedit /boot/grub/menu.lst
```

i think that 

```
gksudo gedit /boot/grub/menu.lst
```

is technically the correct way, but i am not sure if it is gksudo.  both accomplish the same,  just edit as regular after that, the menu.lst will open and you will have permission

---

### Post by mclavey on 2008-06-16
You could also install KGRUBEditor with the package manager and use it to edit the boot up menu.

---

### Post by mitzelpick on 2008-06-16
Great - I will try it.
Thanks for the help !

---

### Post by mitzelpick on 2008-06-16
Thx - I was curious about Package Manager anyway.

---

### Post by Victormd on 2008-06-16
all you need to do is
```
sudo gedit /boot/grub/menu.lst
```
and edit this line:
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**_default		0_**
replacing the "0" with the current position for windows (the numbering system starts with 0, not 1 here)

---

### Post by rraj.be on 2008-06-16
The simplest way is to use GUI type of 
startup manager.

```
sudo apt-get install startupmanager


```

More than setting default OS you can d a lot with startup manager like setting password for GRUB,changing timeout,setting background colours for boot screen etc.

This is the safest way to proceed than editing menu.lst.


Moreover it wont lead you to any errors by mistake as it is a GUI.

Hope this help's you.

---

