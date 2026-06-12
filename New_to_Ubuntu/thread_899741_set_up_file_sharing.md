---
title: "set up file sharing?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-24
how do i set up file sharing between two computers? im just using a ethernet plug between two comps

---

### Post by WinterMadness on 2008-08-24
> **WinterMadness said:**
> how do i set up file sharing between two computers? im just using a ethernet plug between two comps

noone?

---

### Post by tuxulin on 2008-08-24
what do you have on these 2 machines ?



Tuxulin

---

### Post by WinterMadness on 2008-08-24
> **tuxulin said:**
> what do you have on these 2 machines ?



Tuxulin

ubuntu

---

### Post by tuxulin on 2008-08-24
if you can already ping the other machine
then install on both pc's 
sudo apt-get install openssh-server openssh-client

goto Places >> Connect to server...
choose SSH then fill the rest of the dialog box out
click connect, put the password in (the target machine password)

done

Tuxulin

---

### Post by Iowan on 2008-08-24
[Here]("https://help.ubuntu.com/community/SSHFS") is some good background information on SSHFS.

I presume that ethernet plug is a crossover cable - a straight cable between the two *probably* won't work.

---

### Post by Titan8990 on 2008-08-24
> I presume that ethernet plug is a crossover cable - a straight cable between the two probably won't work.

Are we still living in the 80s? Networking devices (switches, routers, and hubs) are cheap, plentiful, and just about everyone has one.

---

### Post by Kain000 on 2008-08-24
Yeah are you using a router or hub of some kind?  An eithernet cable between two machines wont network them.   Please explain your setup.

---

### Post by aloshbennett on 2008-08-25
Ftp across a cross-cable is what I prefer if I have to share a lot of data with another computer.

---

### Post by tuxulin on 2008-08-25
@ kain000

the user said the machines are connected via ethernet cable.

with that in mind why do you think that
> An eithernet cable between two machines wont network them

back in the day it worked quite well. all thats needed is a verification on a ping test, 2 private ip numbers and a subnetmask.

maybe ubunty was built slightly different and cannot manage peer to peer topology. since im not an linux expert can you explain :)

Tuxulin

---

