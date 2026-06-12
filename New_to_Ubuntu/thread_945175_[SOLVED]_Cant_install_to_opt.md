---
title: "[SOLVED] Cant install to /opt"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-10-12
Hey

Im trying to install PlaneShift now, but it wants to install to /opt However when I click ok it says "Cannot write to /opt as current user" but does not give me the opportunity to log in so I can be root and install the game etc etc, I have tried installing into my home folder but that just results in things (like the updater) not working -_-

Please help.

Thanks

---

### Post by scragar on 2008-10-12
```
sudo PlaneShift...bin
```
run the whole installer with sudo.

---

### Post by sinclair86 on 2008-10-12
try using ```
sudo
``` before the command

---

### Post by Vendettaseve on 2008-10-12
Thanks, Diddent know I could just sudo (file) that makes life alot easier :D

---

### Post by Vendettaseve on 2008-10-12
Heres a sad story... It diddent work.. at all


vendettaseve@vendettaseve-Lair:~$ ls
amsn_received          Music                       Public
Desktop                My Spore Creations          rarcrack-0.2
Documents              opt                         Spore-RELOADED
Examples               PenumbraEp1                 Templates
Firefox_wallpaper.png  Pictures                    Videos
Furcadia               PlaneShift-v0.4.01-x86.bin  virtual-drives
vendettaseve@vendettaseve-Lair:~$ sudo PlaneShift-v0.4.01-x86.bin
sudo: PlaneShift-v0.4.01-x86.bin: command not found

---

### Post by Perfect Storm on 2008-10-12
```
chmod +x PlaneShift-v0.4.01-x86.bin
sudo ./PlaneShift-v0.4.01-x86.bin
```

[http://gaming.gwos.org/doku.php/guides:64bit:planeshift](http://gaming.gwos.org/doku.php/guides:64bit:planeshift)

---

### Post by Vendettaseve on 2008-10-12
thanks :D

I already did chmod but the second code works like magic, Your a legendary hero of ubuntu :D

---

### Post by Vendettaseve on 2008-10-12
Seem to be having a problem now that its installed to /opt

Apparently I dont have permission to play the game -_-  I tried using the run window but it just does the little loading circle forever instead of loading files when I try to get into /opt/planeshift

-_-

---

### Post by Perfect Storm on 2008-10-12
Actually there's no reason to install it /opt. Just set it up in your home directory instead. I usually set games up in ~/.Games in my home folder.
When there's a dot infront of the name of the file or folder it's hidden. Then I can keep a clean look in my home.

---

### Post by Vendettaseve on 2008-10-12
Ah right, 

So how would I go about uninstalling it now that I cant get anywhere near it due to permissions.. Cant even seem to cd my way into the directory to get to the uninstall via terminal.

---

### Post by Perfect Storm on 2008-10-12
Try check /opt/planeshift if there's a file that is called uninstall.

else;
```
cd /opt
sudo rm -rf planeshift
```

Note that you have to change planeshift name if it's a diffrent name.

You might afterwards look if it have installed some files in the a bin dicectory.

```
whereis planeshift
locate planeshift
```

---

### Post by freak42 on 2008-10-12
> **Vendettaseve said:**
> So how would I go about uninstalling it now that I cant get anywhere near it due to permissions.. Cant even seem to cd my way into the directory to get to the uninstall via terminal.


use a root console (be VERY careful with it)

start your new console in a console with

sudo bash

to exit to your normal console use

exit

---

### Post by Perfect Storm on 2008-10-12
It's been a year since I tested the guide so I took some time to re-write it to fit $home installation. Tested in 8.10 64-bit; [Planeshift Installation Guide](http://gaming.gwos.org/doku.php/guides:64bit:planeshift)

---

