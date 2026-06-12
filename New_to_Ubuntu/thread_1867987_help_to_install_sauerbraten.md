---
title: "help to install sauerbraten"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by ivoribeiro on 2011-10-23
hi guys, i downloaded the saurbraten game and i tried to install sauerbraten in the terminal, typing "sudo apt-get install sauerbraten " but the terminal always says "sudo: apt-get: command not found" .. if you can help me i would be quite thankfull !

---

### Post by ikt on 2011-10-23
> **ivoribeiro said:**
> hi guys, i downloaded the saurbraten game and i tried to install sauerbraten in the terminal, typing "sudo apt-get install sauerbraten " but the terminal always says "sudo: apt-get: command not found" .. if you can help me i would be quite thankfull !

Why not use the Ubuntu Software Centre? or Synaptic?

```
sudo: apt-get:
```

!=

```
sudo apt-get install sauerbraten
```

This is what I get when I try on Ubuntu 11.10:


```
ikt@ikt-desktop:~$ sudo apt-get install sauerbraten
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmikmod2 libsdl-mixer1.2 libsmpeg0 sauerbraten-data sauerbraten-wake6
The following NEW packages will be installed:
  libmikmod2 libsdl-mixer1.2 libsmpeg0 sauerbraten sauerbraten-data
  sauerbraten-wake6
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 462 MB of archives.
After this operation, 550 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

But I don't see why you would when it's in the ubuntu software centre:

[IMG]http://ikt.id.au/blog/wp-content/uploads/2011/10/sauerbraten.png[/IMG]

---

### Post by mahmoud.l on 2011-10-23
Try to install another app in the terminal and see if it does the same thing
Also, use software center like ikt said

---

### Post by oldos2er on 2011-10-23
Copy and paste this in a terminal: ```
sudo apt-get update && sudo apt-get install sauerbraten
```
If there are any errors please copy and paste them in full here.

---

