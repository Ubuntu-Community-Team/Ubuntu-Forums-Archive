---
title: "VESA:SUMO driver for Radeon?"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by drabina on 2011-11-10
I have laptop with Radeon HD 6480G graphic card. When I launch System Info, the graphics driver is listed as VESA:SUMO. Is that the correct driver for the video card? I am asking because I am new to Ubuntu but VESA sounds kinda generic to me and also the experience says standard.

Thanks.

---

### Post by acrazyplayer on 2011-11-11
I don't know what version of ubuntu you are using so just run this in a terminal. 

```
jockey-gtk
```

If it says you can install a driver for it then go for it. Maybe make sure you have important documents backed up first though, just to be safe.

---

### Post by undeadbobop on 2012-10-28
Have same question but have a issue running jockey I have it installed according to synatics package manager but I get:

bobop@bobop-HP-Pavilion-dv6-Notebook-PC:~$ jockey-gtk
The program 'jockey-gtk' is currently not installed. You can install it by typing:
sudo apt-get install jockey-gtk

And when ever I do sudo apt-get install jockey-gtk I get:

bobop@bobop-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get install jockey-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jockey-gtk is already the newest version.

And I still get this when I try jockey-gtk:
bobop@bobop-HP-Pavilion-dv6-Notebook-PC:~$ jockey-gtk
The program 'jockey-gtk' is currently not installed. You can install it by typing:
sudo apt-get install jockey-gtk

And I am running 12.10

---

### Post by Mark Phelps on 2012-10-29
> **undeadbobop said:**
> Have same question but have a issue running jockey I have it installed according to synatics package manager but I get:

bobop@bobop-HP-Pavilion-dv6-Notebook-PC:~$ jockey-gtk
The program 'jockey-gtk' is currently not installed. You can install it by typing:
sudo apt-get install jockey-gtk

And when ever I do sudo apt-get install jockey-gtk I get:

bobop@bobop-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get install jockey-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jockey-gtk is already the newest version.

And I still get this when I try jockey-gtk:
bobop@bobop-HP-Pavilion-dv6-Notebook-PC:~$ jockey-gtk
The program 'jockey-gtk' is currently not installed. You can install it by typing:
sudo apt-get install jockey-gtk

And I am running 12.10

Version 12.10 poses NEW problems because they updated the X-server version and ONLY the latest beta drivers from AMD will work with this version.  Plus, unless your HP has a video chipset newer than the HD 4xxx version, it's not going to work anyway.

---

### Post by Bashing-om on 2012-10-29
@ drabina -as the original poster...

install the mesa-utils utility, reboot and see what the result is then.
terminal code (ctl+alt+t)
```
sudo apt-get install mesa-utils 
``` sudo requires the use of your password; will get no response to the screen (security reasons)
I expect that "system info" will display correct info now.
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by wildmanne39 on 2012-10-30
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

