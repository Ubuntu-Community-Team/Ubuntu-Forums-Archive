---
title: "[SOLVED] transmission 1.22 Hardy"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by bred on 2008-07-31
[COLOR="Navy"]Hi there,
I have trasmission 1.04 - by default on hardy and I would like to upgrade to 1.22...
I found the .deb package for 1.22, I installed it but I cannot find it on Application-Internet... I can not launch it...have no idea how... 

thx for suggestions[/COLOR]

---

### Post by espressopigeon on 2008-07-31
In a terminal type:

transmission

It should launch. To put it on the menu, create a new menu entry and in the command field type: 'transmission'

---

### Post by bred on 2008-07-31
[COLOR="DarkRed"]tried and what I get :[/COLOR]


[COLOR="Navy"]pc@pc-laptop:~$ transmission
The program 'transmission' is currently not installed.  You can install it by typing:
sudo apt-get install transmission-gtk
bash: transmission: command not found

pc@pc-laptop:~$ sudo apt-get install trasmission-gtk
[sudo] password for pc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package trasmission-gtk
pc@pc-laptop:~$[/COLOR]

any suggestions pls?

---

### Post by espressopigeon on 2008-07-31
It looks like you misspelled 'transmission' as 'trasmission'

It also appears that transmission is made of two packages, the program (transmission-common) and a GUI frontend (transmission-gtk). You may need version 1.22 of both.

---

### Post by bred on 2008-07-31
> **espressopigeon said:**
> It looks like you misspelled 'transmission' as 'trasmission'

It also appears that transmission is made of two packages, the program and a GUI frontend (transmission-gtk). You may need version 1.22 of both.


[COLOR="DarkRed"]LOL ...[/COLOR]


[COLOR="Navy"]pc@pc-laptop:~$ transmission
The program 'transmission' is currently not installed.  You can install it by typing:
sudo apt-get install transmission-gtk
bash: transmission: command not found
pc@pc-laptop:~$ sudo apt-get install transmission-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  transmission-gtk: Depends: transmission-common (= 1.06-0ubuntu6) but 1.22-0~getdeb1 is to be installed
E: Broken packages
pc@pc-laptop:~$ 

[/COLOR]

---

### Post by espressopigeon on 2008-07-31
So the transmission-gtk from the repo wants the older version of transmission-common, which of course you don't have. See if the package you downloaded included v1.22 of both transmission-common and transmission-gtk, or just transmission-common, or what.

---

### Post by bred on 2008-07-31
the deb package I installed contains transmission common 1.22


I tried to install transmission 1.04 then to apply package transmission common 1.22, but it gives me an error, its not compatible...well I guess I'm doing wrong the update..

---

### Post by espressopigeon on 2008-07-31
Ah, see if you can find an ubuntu transmission-gtk 1.22 .deb somewhere.

---

### Post by bred on 2008-07-31
I found transmission-gtk 1.22-1ubuntu1~hardy1 (lpia binary) in ubuntu hardy here
[https://launchpad.net/ubuntu/hardy/lpia/transmission-gtk/1.22-1ubuntu1~hardy1]("https://launchpad.net/ubuntu/hardy/lpia/transmission-gtk/1.22-1ubuntu1~hardy1")

but when I want to install it gives an error 

[COLOR="DarkRed"]wrong architecture 'lpia'[/COLOR]


thx for help

---

### Post by espressopigeon on 2008-07-31
That's the wrong edition of that package. LPIA is Intel's mobile device platform that Ubuntu Mobile is used on. Maybe this link will help: [http://packages.ubuntu.com/source/intrepid/transmission](http://packages.ubuntu.com/source/intrepid/transmission)

---

### Post by bred on 2008-07-31
well I've downloaded another one from here

[http://packages.ubuntu.com/intrepid/i386/transmission-gtk/download]("http://packages.ubuntu.com/intrepid/i386/transmission-gtk/download")

and got an error: [COLOR="DarkRed"]dependencies is not satisfiable lbgtk2.0-0[/COLOR]

have no idea ...

---

### Post by espressopigeon on 2008-07-31
Ooh, looks like transmission-gtk wants a newer version of libgtk, which will probably want newer versions of other programs and so on. You may just have to go back to an older version and wait for the official update.

---

### Post by phoenix_abhi on 2008-07-31
Wait for the official update

---

