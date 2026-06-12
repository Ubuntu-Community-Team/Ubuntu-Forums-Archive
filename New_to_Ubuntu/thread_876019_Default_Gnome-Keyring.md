---
title: "Default Gnome-Keyring"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by dima338 on 2008-07-31
Recently I encountered the problem where I had to enter the default gnome-keyring password everytime I connected to my default wireless connection, so I googled that and found this page: [http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/]("http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/"). So I followed the instructions on this page carefully and the next time I turned on my laptop (HP Pavilion dv2000), I couldn't type anything in the username/password field and a message saying "Authentication failed" appeared. I can still get into recovery mode but I am unsure what to do...I am running Hardy by the way. Don't flame me for doing something I didn't know about, I know I should've gone straight to these forums and I already found a solution to stop it from asking me for the password. So all I need now is to be able to actually login :):)

---

### Post by LowSky on 2008-07-31
take out this from /etc/pam.d/gdm file
@include common-pamkeyring

then

uninstall that program

sudo aptitude remove libpam-keyring

to reset or delet keyring here an easier way
go to you home folder, hit ctrl+h
open the .keyring folder
delete the contents ( it ok trust me)
now when you see a keyring window type nothing just hit enter, it will never show up again

---

### Post by dima338 on 2008-07-31
Well as described in my previous post I can't log in...:confused: so would I be able to edit the file from recovery mode or some other way not having me logged in :confused:

---

### Post by LowSky on 2008-07-31
try loggin in from safe mode

it brings you to a terminal screen and you enter your name and password there, then type ```
startx
```, it should bring up Gnome

---

### Post by dima338 on 2008-07-31
Sorry for the stupid question but is safe mode the same as recovery mode, because in the grub menu that's all that I have (well besides the memtest and the rest) :confused:

EDIT: nvm found out by myself will try the provided instructions :)

---

### Post by dima338 on 2008-07-31
I typed start x but it said:
```
start: Unknown job: x
```
Was the 'x' suposed to be replaced by something?

Anyways bringing up Gnome will be no good as it won't let me log in....

---

### Post by dima338 on 2008-07-31
bump

---

### Post by dima338 on 2008-07-31
bump

---

### Post by blazercist on 2008-07-31
dima338 don't bump so often its not polite, startx not start x, there is no space between.

---

### Post by dima338 on 2008-07-31
umm well sorry it was two times and being left with an xp machine for 2 weeks which i can't use whenever i want makes you quite desperate ;) but thanks for your help

---

