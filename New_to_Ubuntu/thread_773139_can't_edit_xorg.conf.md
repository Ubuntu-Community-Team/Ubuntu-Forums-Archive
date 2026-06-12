---
title: "can't edit xorg.conf?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by nate9000 on 2008-04-28
alright, im a beginner to Ubuntu, and Linux alike. the last Distro i used was mandrake.

i downloaded 'Kubuntu 8.04 KDE4'
and as i don't have a computer to use this on. i used Virtual Box to install it. all went fine. and everything works nicely. all but one problem. the screen resolution is stuck at 800X600. and i know how to fix this. i searched the forums here and found the solution. i modified my Xorg.Conf file.
(i have done this successfully on my mandrake system in the past)
so here is my problem...
it wont let me overwrite the old file? i tried logging in as root. but i keep getting denied access? so i opened my terminal. typed 'SU' typed in my password. and it denied me again... and i know i am using the correct password. because i need a super user password when i use the add/remove program app.

i hope that explains my problem clear enough?

does anyone know what im doing wrong?

and please be patient with me. as i am a beginner :)

:popcorn:

---

### Post by riven0 on 2008-04-28
You didn't say you tried sudo, so try this command: **sudo nano -w /etc/X11/xorg.conf**

---

### Post by dokdoom on 2008-04-28
Did you try to use sudo? Say you use vim

sudo vim /etc/X11/xorg.conf

Also which video driver are you using?

---

### Post by kestrel1 on 2008-04-28
You shouldn't need to edit the xorg.conf file. I had a similar issue & it was down to the monitor not being recognised correctly. Have a look here for a possible solution: [http://ubuntuforums.org/showthread.php?t=766846&page=2](http://ubuntuforums.org/showthread.php?t=766846&page=2)

---

### Post by elmer_42 on 2008-04-28
First, you should backup the file.
```
sudo cp /etc/X11/xorg.conf ~/xorg.bak
```
Then run
```
sudo kwrite /etc/X11/xorg.conf
```
You should be able to edit to your heart's content! If you do screw it up, restore it.
```
sudo cp ~/xorg.bak /etc/X11/xorg.conf
```

---

### Post by nowshining on 2008-04-28
or you can use

sudo kate /etc/Xll/xorg.conf

by default linux doesn't allow access to system critical files without root access. :)

---

### Post by Zralou on 2008-04-28
Or try kdesu kate /etc/Xll/xorg.conf

Sara Lou

---

