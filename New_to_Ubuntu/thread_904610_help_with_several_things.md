---
title: "help with several things"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by sivo802 on 2008-08-29
i have a ps3 with gutsy gibbon and i really need help super noob to linux. first i need help with changing the screen size then i need help with installing zsnes emulator and last i need help changing the screen size thanks in advance

---

### Post by sailor2001 on 2008-08-29
in terminal (applications/accessories) type gksudo displayconfig -gtk
enter password

---

### Post by sivo802 on 2008-08-29
thanks but what does this do

---

### Post by sivo802 on 2008-08-29
can someone plz help

---

### Post by okey666 on 2008-08-29
System>> preferences>> screen resolution. If that does not work it get more complex. Looking at zsnes now.

---

### Post by okey666 on 2008-08-29
ok, go to 
[http://sourceforge.net/project/downloading.php?groupname=zsnes&filename=zsnes151src.tar.bz2]("http://sourceforge.net/project/downloading.php?groupname=zsnes&filename=zsnes151src.tar.bz2")
to download zsnes then extract the folder inside to your desktop.

This program does not have a binary for ubuntu so you have to build it.

First open the terminal applicastions>>accesories>>terminal

Then, navigate to your desktop (where you put the folder)
```
cd Desktop
```

Then type
```
cd zsnes[then press tab to complete the path]
```

You must first check you have the stuff it needs
```
sudo apt-get install build-essential
```
and
```
sudo apt-get install nasm
```

Finally type:
```
./configure
```

and post the output here.

---

### Post by okey666 on 2008-08-29
ok,  i do not know if this package will work on ps3 but I have found a 32-bit package (I can't test it cause I have 64-bit).
[http://mirror.aarnet.edu.au/pub/linux/debian/pool/contrib/z/zsnes/](http://mirror.aarnet.edu.au/pub/linux/debian/pool/contrib/z/zsnes/)

---

