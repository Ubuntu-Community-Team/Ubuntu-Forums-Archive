---
title: "Disappearing windows"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by ColmCille on 2008-09-23
When I try to enter a repository key:

System > Administration > Software Sources > authentication > import key file

The window disappears.  I get error messages in my log viewer like this:

kernel: [  716.319424] software-proper[6360]: segfault at 0 rip 0 rsp 41a07058 error 14

Only with slightly different numbers each time, i.e.:

 kernel: [  829.483032] software-proper[6446]: segfault at 0 rip 0 rsp 41ce6058 error 14

Likewise, when I try edit the login screen

System > Administration > Login Window

The Editing window pops up for a split second and disappears. There remains a minimize tab in my lower panel for a few seconds and then it, too disappears.

I get very similar messages:

kernel: [  948.597782] gdmsetup[6476]: segfault at 0 rip 0 rsp 7fffa923ad28 error 14

I'm running Hardy on a 60GB partition on a Presario F700 series, Turion64 X2, 2 gids of ram, around 4 GB swap partition. 

Need more info let me know.

Any idea what might be going on? 

Thanks.

---

### Post by ColmCille on 2008-09-23
No idea, huh?

---

### Post by RussW210 on 2008-09-23
I had a similar problem getting the login window settings to pop up and:

sudo dbus-launch gdmsetup

Worked for me... try locating the file it is opening and type

sudo dbus-launch <file name>

Worth a shot.

---

### Post by RussW210 on 2008-09-23
The dbus-launch terminal command was a temporary fix but it gets you into the login window.  Keep the terminal open, make the changes to your login window, then close out of the login window and all should be good.

---

### Post by ColmCille on 2008-09-24
I'll try it, thanks. Maybe it will help with software sources, which is the more important thing, actually. Software sources seems to be running two files. This is the command line:

gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

Every part of it seems to work fine, it just crashes every time I try and feed it a key. 

I guess nobody has a clue what the error codes mean. I did some Googling and found nothing. Or if I found something, I couldn't understand it. :)

---

