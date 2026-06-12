---
title: "Problem with Synaptic Package Manager - Adding a new URI"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Lahlah on 2008-10-11
Hi,

I'm trying to get my vodafone dongle to work with Ubuntu.  Over on betavine they've suggesting some software that they use not particuarly for the the dongle I have but can give it a go.  

I need to add a new repository (?) in order to pick up the betavine software, but when I try to add the API line the add button won't change so I can click it. 

What the betavine guys want me to do is add the API or the repository

Type: Binary (deb)
URI: [http://betavine.net/repo/debian/dists/etch/](http://betavine.net/repo/debian/dists/etch/)
Distribution: EeePC

I've tried typing in: 
deb [http://betavine.net/repo/debian/dists/etch](http://betavine.net/repo/debian/dists/etch)

and vairious other combinations but the add souce button won't come up.  I don't have web access through it yet (it's why I'm trying to do that, so I can have web access) is there anything I'm missing, or need to do?

---

### Post by baizon on 2008-10-11
Add this code to the sources.list (/etc/apt/) file.
```
deb http://betavine.net/repo/debian/dists/etch
```

---

### Post by perlluver on 2008-10-11
To add that code: ```
gksudo gedit /etc/apt/sources.list
``` add ```
deb http://betavine.net/repo/debian/dists/etch
``` and then save.  Then run ```
sudo apt-get update
``` then install your program.

---

### Post by Lahlah on 2008-10-12
Hi,

Thanks for the advice.  

I do all this in the terminal screen then run the program.  It opens in a dos (?) terminal and then says the message:

You must be root!
Press Return to close this window...

I take it it hasn't worked?  Am I missing something, I put the deb [http://betavine.net/repo/debian/dists/etch/](http://betavine.net/repo/debian/dists/etch/) by just pressing return and adding it to the top.  Does this make a difference?

Lx

---

### Post by Lahlah on 2008-10-13
Hate to bump:(

Can anyone else help with this?

---

### Post by cariboo on 2008-10-13
You have to edit /etc/apt/sources.list as root. If you are doing it in a terminal type:

```
sudo nano /etc/apt/sources.list
```

Enter your user password when asked. This will open the file in nano a text editor. Add the repository to the bottom of the list, the prees Ctrl-o to sve and Ctrl-x to exit. Then in the same terminal type:

```
sudo spt-get update
```

This will update the sources.list.

Jim

---

### Post by Vadi on 2008-10-13
Try adding this: 

> deb [http://betavine.net/repo/debian/dists/etch/](http://betavine.net/repo/debian/dists/etch/) EeePC

You can do so via System - Administration - Software Sources - Third-Party tab. No need to mess with the terminal.

---

### Post by gandaran on 2008-10-13
to run any application as root you must use **sudo**

---

### Post by scratman on 2008-10-13
Open up terminal and type 

sudo -s

and then press enter.  You'll be asked for your superuser password.  Enter that, and you'll be logged in as root.

---

### Post by Lahlah on 2008-10-18
Cheers for all the help and suggestions I've tried the following:

I get this message when I go into the synaptic manager - 

E: Malformed line 53 in sourse list /etc.apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E:_cache->open()failed,please report. 

I went back into the 'sudo nano' and deleted the  
deb [http://betavine.net/repo/debian/dists/etch](http://betavine.net/repo/debian/dists/etch) 

I also ran the sudo apt-get update, it says
E: Malformed line 53 in source list /etc/apt/sources.list (dist parse)

I also tried sudo -s, but it won't accept my password - I did not set one when I installed ubuntu.  Should I re install, pick a password and start again?

---

### Post by oldos2er on 2008-10-18
Can you please post the output of "cat /etc/apt/sources.list"?

---

