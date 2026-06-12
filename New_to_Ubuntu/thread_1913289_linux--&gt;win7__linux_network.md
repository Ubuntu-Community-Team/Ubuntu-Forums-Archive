---
title: "linux--&gt;win7 / linux network"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by DeathByDigital on 2012-01-22
hello there.-..
atm ive got 3 computers running in the network.
i have installed win7 ultimate on all computers, and ive got ubuntu 10.04LTS on 2 of them, and this one has the newer 11.10

Anyways.. ive installed ubuntu, to learn it, and try to migrate over from windows.

This computer with the ubuntu 11.10 im hoping to function as dedicated fileserver.... 
so i want it to work on the network, not depending if i log on windows or linux on the clients.

ive searched kinda much. but ive used windows since the day we wrote our own autoexec.bat files. and linux is a whole new world. Ive figured i need a werry detailed guide.
(doesnt help me to get a guide who sais: then its just to configure cnf file (when i dont know how))

so i need to know what "network" i should run , but the main issue is, since im new to linux, i need the ultimate detailed guide.,... where its not assumed that ppl know anything about linux. 

Thanx in adv.

---

### Post by lechien73 on 2012-01-22
Hi,

It seems to me what you're looking for is a guide to setting up a Samba fileserver. This allows Windows clients to access files shared on a Linux machine over a network.

A great guide is here: [https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)

and more in-depth documentation is here: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

When the guide tells you to edit a .conf file, then - from a terminal window type:

```
gksudo gedit path-and-name-of-file
```

So, when the guide tells you to edit /etc/samba/smb.conf, you would type:

```
gksudo gedit /etc/samba/smb.conf
```

Since these are system files, you need to edit them with elevated privileges, which is what *sudo* or *gksudo* does - think of it as the Windows "Run as administrator" option for a program. *gedit* is the name of a GUI-based text editor.

---

### Post by davethewave83 on 2012-01-22
> **DeathByDigital said:**
> hello there.-..
atm ive got 3 computers running in the network.
i have installed win7 ultimate on all computers, and ive got ubuntu 10.04LTS on 2 of them, and this one has the newer 11.10

Anyways.. ive installed ubuntu, to learn it, and try to migrate over from windows.

This computer with the ubuntu 11.10 im hoping to function as dedicated fileserver.... 
so i want it to work on the network, not depending if i log on windows or linux on the clients.

ive searched kinda much. but ive used windows since the day we wrote our own autoexec.bat files. and linux is a whole new world. Ive figured i need a werry detailed guide.
(doesnt help me to get a guide who sais: then its just to configure cnf file (when i dont know how))

so i need to know what "network" i should run , but the main issue is, since im new to linux, i need the ultimate detailed guide.,... where its not assumed that ppl know anything about linux. 

Thanx in adv.

I've been pointed to many highly detailed guides to set up Samba and file sharing between linux and windows, none of the guides have ever worked for me even when I follow them very closely, and samba was never stable for me. Sometimes working, sometimes not working, working one moment and then the next moment unable to find any network or, asking me for login credentials when I specifically marked the "allow guests"

So,
I set up an FTP server with HTTP access as well. If you search around you might be able to find some good FTP guides. I haven't had any problems with FTP except over wi-fi (so I use http for wi-fi)

---

### Post by DeathByDigital on 2012-01-22
gksudo gedit /etc/samba/smb.conf
might be something wrong i get, but i got a empty file,  and have noe clue, what to put there ... ill restart and try again..
managed to see a few of my shared files in win 7 but got msg about file misspelling?
ill try and take a new look at the guides..and thanks alot

---

### Post by lechien73 on 2012-01-22
Ok...had you opened a terminal window and run:

```
sudo apt-get install samba
```

first?

---

