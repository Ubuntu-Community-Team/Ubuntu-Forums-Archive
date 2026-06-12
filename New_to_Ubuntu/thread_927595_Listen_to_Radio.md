---
title: "Listen to Radio"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by beeky on 2008-09-23
How can I get Ubuntu to allow me to listen to the BBC radio programmes. At present if I click on listen - say to five live - I get the iplayer up which doesn't of course work. I have also tried to add the raio station to the inbuilt music player but without luck. Any ideas please

Beeky

---

### Post by ww711 on 2008-09-23
Real Player would be the alternative.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin)

---

### Post by beeky on 2008-09-23
Thanks but you are talking to a real beginner. I have tried the link and I would need some guidance what was need. For example Terminal? Hope you can help

---

### Post by oldos2er on 2008-09-23
If you're using Gnome, the terminal is under the menus Applications, Accessories.

---

### Post by L Campbell on 2008-09-23
> **ww711 said:**
> Real Player would be the alternative.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin)

With all due respect here the very first part of these instruction didn't work for me:-

qwer@qwer-desktop:~$ chmod 770 RealPlayer11GOLD.bin
chmod: cannot access `RealPlayer11GOLD.bin': No such file or directory
qwer@qwer-desktop:~$   sudo ./RealPlayer11GOLD.bin
[sudo] password for qwer: 
sudo: ./RealPlayer11GOLD.bin: command not found
qwer@qwer-desktop:~$ 

Did I do something wrong?

---

### Post by Paqman on 2008-09-23
> **beeky said:**
> At present if I click on listen - say to five live - I get the iplayer up which doesn't of course work.

Have you tried going to the online iPlayer? It uses Flash, and should work fine.

---

### Post by Mornedhel on 2008-09-23
Did you cd to the directory you stored your .bin file in ?

Bash is powerful, but it can't read your mind (yet).

---

### Post by fogcat on 2008-09-23
Just a shot:  have you tried "streamtuner"?  I use it for internet radio, shoutcast primarily.  I do not know if the particular BBC programming is on that.

fogcat

---

### Post by L Campbell on 2008-09-23
> **Mornedhel said:**
> Did you cd to the directory you stored your .bin file in ?

Bash is powerful, but it can't read your mind (yet).


How does one do that?

---

### Post by oldos2er on 2008-09-23
cd Desktop

is the command you use, assuming the file you downloaded is on your desktop. Then you should be able to run the commands you tried earlier.

---

### Post by L Campbell on 2008-09-24
> **oldos2er said:**
> cd Desktop

is the command you use, assuming the file you downloaded is on your desktop. Then you should be able to run the commands you tried earlier.

Thanks, that did the trick and I appreciate it.

---

### Post by billgoldberg on 2008-09-24
> **L Campbell said:**
> With all due respect here the very first part of these instruction didn't work for me:-

qwer@qwer-desktop:~$ chmod 770 RealPlayer11GOLD.bin
chmod: cannot access `RealPlayer11GOLD.bin': No such file or directory
qwer@qwer-desktop:~$   sudo ./RealPlayer11GOLD.bin
[sudo] password for qwer: 
sudo: ./RealPlayer11GOLD.bin: command not found
qwer@qwer-desktop:~$ 

Did I do something wrong?

I have a graphical guide on install real player 11.

Here you go (no terminal usage):

[http://linuxowns.wordpress.com/2008/04/15/real-player-11/](http://linuxowns.wordpress.com/2008/04/15/real-player-11/)

---

