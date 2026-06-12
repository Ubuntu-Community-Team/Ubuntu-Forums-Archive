---
title: "Trouble with graphics drivers"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by abdallah2 on 2013-09-20
hi...iam new to use ubuntu..
i install ubuntu 12.04  64bit
the problem i have...in the additional drivers..i make update to "VGA GEDORCE NVIDIA "and after that I RESTART the computer abd the following screen appear...what can i do??
[ATTACH=CONFIG]246371[/ATTACH][ATTACH=CONFIG]246374[/ATTACH]

---

### Post by whitesmith on 2013-09-20
Is your computer hung?

---

### Post by abdallah2 on 2013-09-20
> **whitesmith said:**
> Is your computer hung?

NO...it works very good

i have beside ubuntu...windows 8 and it work very good and the graphics is working very good!!

---

### Post by Jonathan Precise on 2013-09-20
Try nomodeset or xforcevesa.

Usually I do not use proprietary drivers (I use open-source, since I know people that have problems with the proprietary drivers). So unless you really need them, use the default one.

----Work-around----

Boot ubuntu-live CD. Backup everything you need!!! Re-install (use the "Erase Ubuntu 12.04 and Install" button, but not "Erase everything and install"!!!), and stick to the open-source drivers.

--End-work-around--

---

### Post by Rob Sayer on 2013-09-20
He meant does your computer hang in ubuntu when you get the second screen ... ie. does it respond at all, if not it's hung ... not in windows.

---

### Post by Jonathan Precise on 2013-09-20
Also, hit Ctrl. Alt. F1.

You will see:

```
login: [flashing-cursor]
```

Type your username (no-capitals, use - instead of spaces usually):

```
...
Password: [flashing-cursor]
```

Type your password (you will not even see asterisks, this is normal).

```
...
*user*@*computer*:-$ [flashing-cursor]
``` (- is a tilde).

Type in:
```
startx
```

Post any errors.

---

### Post by Jonathan Precise on 2013-09-20
To shut-down, type in:

```
sudo halt
```

To reboot:

```
sudo reboot
```

Enter password in both cases (see previous post about asterisks).

---

### Post by abdallah2 on 2013-09-20
> **Jonathan Precise said:**
> To shut-down, type in:

```
sudo halt
```

To reboot:

```
sudo reboot
```

Enter password in both cases (see previous post about asterisks).

I do what u say...i reinstalled ubuntu..and no change...when iam try to update the VGA "GEFORCE NVIDIA"  and restart..the same screen appear.....
and i try now the method ctrl+alt+f1
and followed the steps ...this is the result
[ATTACH=CONFIG]246377[/ATTACH]
what can i do?

notice that the graphic is unknown !! 

[ATTACH=CONFIG]246378[/ATTACH]

---

### Post by abdallah2 on 2013-09-20
Thank you all for your attention and i tired you with me

---

### Post by Jonathan Precise on 2013-09-20
I don't think I understand. You are showing that the computer is unable to display anything except the console-login, yet you are showing a graphical application.

Wait: is your problem with unity (panel, launchers/dash, etc.)?

If it is, run with:

```
unity
```

> **abdallah said:**
> ... and i tired you with me

Nonsense! We are here to help!

---

### Post by buzzingrobot on 2013-09-20
Yes, it is unclear if you are booting into a normal graphical environment, or if the boot is stopping during that display of white text on a black background that you show in the image in your first post.

---

