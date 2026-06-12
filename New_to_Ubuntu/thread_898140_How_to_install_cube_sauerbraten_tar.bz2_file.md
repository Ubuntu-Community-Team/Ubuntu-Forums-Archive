---
title: "How to install cube sauerbraten tar.bz2 file"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Milan Josipovic on 2008-08-22
Hi all

J've downloaded this file:
sauerbraten_2008_06_20_ctf_edition_linux.tar.bz2

Can anyone tell me step by step how to install this game,because J am noob.
J found this game through links on:
[https://help.ubuntu.com/community/Cube?highlight=%28CategoryGames%29](https://help.ubuntu.com/community/Cube?highlight=%28CategoryGames%29)

And J downloaded it from the [http://www.cubeengine.com/](http://www.cubeengine.com/)

thanks

---

### Post by mevets on 2008-08-22
I looked for this in the repos and was surprised it was there. To install it just run:
```
sudo apt-get install sauerbraten
```
Now its supposed to install sauerbraten-data too. But when I tried to install this game it said it didnt like the version of the data package in the repo. Tell me if this happens to you. If it does not, then I just configured my apt oddly.

---

### Post by nickgaydos on 2008-08-22
You can also get it from getdeb . net or if your an ultimate user like myself you can use the "upgrade" Script on your desktop :)

---

### Post by Milan Josipovic on 2008-08-23
J got this in terminal:
milan@Milan:~$ sudo apt-get install sauerbraten
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sauerbraten

---

### Post by mevets on 2008-08-23
Guess you have to enable multiverse. To do this go to Add/Remvoe and search for sauerbraten. Check it then it will ask if you want to enable.

PS - [http://www.getdeb.net/release/2865](http://www.getdeb.net/release/2865) to downlaod from getdeb.net

---

### Post by Milan Josipovic on 2008-08-23
This is odd....J looked in add/rem and find nothing

---

### Post by Milan Josipovic on 2008-08-23
Never mind...thanks for your time...
J'll download it from getdeb....
thanks again

---

### Post by MaxIBoy on 2008-08-23
Make sure you have "all available applications" selected as your source:

---

### Post by Milan Josipovic on 2008-08-23
Well it is selected.
What do u think,is there some error in my system?

---

### Post by mevets on 2008-08-23
Try going to System > Admin > Software Sources and check (multiverse)

---

### Post by Sepero on 2011-01-17
A good guide
[http://gwos.org/doku.php/guides:64bit:sauerbraten](http://gwos.org/doku.php/guides:64bit:sauerbraten)

---

### Post by overdrank on 2011-01-17
No need to revive a 2 year old thread. Thread closed :)

---

