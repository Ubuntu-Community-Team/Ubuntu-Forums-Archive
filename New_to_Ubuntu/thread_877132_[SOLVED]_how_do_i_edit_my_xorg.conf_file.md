---
title: "[SOLVED] how do i edit my xorg.conf file?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by pcrussell50 on 2008-08-01
it has been suggested that i edit my xorg.cong file in order to fix my screen resolution problems.  when i go to etc/x11/xorg.conf i can't rename, cut, or paste, so therefore i can't edit it.  every time i open it in mousepad and edit it and try to save it, using mousepad, i get "can't open file to write".  when i look at permissions, everything is greyed out, even though it says i'm root. so how can i edit this thing?

-peter

---

### Post by LowSky on 2008-08-01
you need to type

```

sudo gedit /etc/X11/org.conf
```

(Capital X)

---

### Post by bks on 2008-08-01
You need to have root permission in order to write to this file so type this in to the terminal:
```

sudo nano /etc/X11/xorg.conf

```

---

### Post by PmDematagoda on 2008-08-01
If you were trying to access and write to the file as a normal user under a normal session then you aren't root. In order to obtain the necessary permissions to edit the file with mousepad you will need to use a command like this(I am not extremely sure if it's gksudo with Xfce as well):-
```
gksudo mousepad /etc/X11/xorg.conf
```
which should open the file in mousepad and allow you to edit it properly. But please make a backup of the xorg.conf file before editing it, in case you mess something up by accident.

---

### Post by Alldan on 2008-08-01
try this:
ALT+F2 
then
gksudo gedit
then open and edit xorg.conf

---

### Post by Iandefor on 2008-08-01
Wait, are you running mousepad as root? If not, you need to run it with sudo:```
gksudo mousepad
```EDIT: Wow, I got beaten like, four times already.

@PMDematagoda: I've tried that before, and gksudo usually thinks that the file path intended for mousepad is an argument to gksudo and chokes on it.

---

### Post by Elfy on 2008-08-01
If gedit haas been installed otherwise

```
gksudo mousepad /etc/X11/org.conf
```

or use nano instead

```
sudo nano /etc/X11/org.conf
```

Edit - I guess that's enough people giving that help then lol

---

### Post by oldsoundguy on 2008-08-01
I use:  sudo nano /etc/X11/xorg.conf 

just another editor that works.

---

### Post by PmDematagoda on 2008-08-01
> **Iandefor said:**
> @PMDematagoda: I've tried that before, and gksudo usually thinks that the file path intended for mousepad is an argument to gksudo and chokes on it.

Ah, thanks for that:). I guess Mousepad isn't the same as Gedit, though it does cross my mind as being a little strange.

---

### Post by pcrussell50 on 2008-08-01
ok thanks gang!  you showed me how to run mousepad as root. [and it worked and i have my graphics back! woohoo!]

now i wonder how i can run as root in my file manager, because all my renaming and writing permissions are greyed out when i navigate to xorg.conf via file manager.  iow, it would have been easier to just rename xorg.conf as something else, but i can't do that.

-Peter

---

### Post by pcrussell50 on 2008-08-01
nevermind, i figured it out.  thanks again, all!

---

