---
title: "[SOLVED] I feel so inadequate"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by GordHatt on 2008-05-08
so i have just finished installing ubuntu 8.04 server on a brand new machine running a raid1 system. the install seems to have gone flawlessly and the machine know me as user gord.

when i turn it on i get 

gord@unbutuServer:~$

i know it is looking for input, but i was kind of hopeing for a desktop with something i can click, then i neew to configure it to be a domain controller and start using it as a file server with no windows induced 10 'puter limit.

so i guess my question is how do i get to.start running my desktop program (gnome? maybe)

looking at the black screen and white letters, flashes me back to dos and all that fun

then i guess i'm off to the book store to get a nice thick book

thanks in advance
Gord

---

### Post by SanjoEel on 2008-05-08
oops wrong thread

---

### Post by quelx on 2008-05-08
Try this

```
sudo apt-get install ubuntu-desktop
```

then reboot

---

### Post by tamoneya on 2008-05-08
the server cd does not have a desktop environment install by default.  This is because most servers dont need to have a GUI running and it would just waste resources.  If however you want the GUI you can just type ```
sudo apt-get install ubuntu-desktop 
startx
```This installs gnome which is the standard desktop enviroment for ubuntu and then it starts it.  After this first run you will only need to type ```
startx
```to get this started.

The problem you may run into is that it may not install all the peices that you want.  Personally I find that it is easier for some one in your situation to install the desktop version of ubuntu which will configure and autostart the gui for you and then add in servers as necessary. eg:```
sudo apt-get install apache2
```

---

### Post by rickh57 on 2008-05-08
I went with tamoneya's route for my "new" Ubuntu box. Even though I'm going to be using it primarily as a server, I installed the client version and added on Apache/Mysql/Php/Squid/etc.

---

