---
title: "repo problem"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by gameryoshi600 on 2008-05-09
how come i get the following error message (attached image)

---

### Post by Joeb454 on 2008-05-09
run ```
gksudo gedit /etc/apt/sources.list
``` and remove the Wine repository from it, it seems like it's not being able to get it properly.

Then visit [http://www.winehq.org]("http://www.winehq.org") and add it again from there (it should work).

---

### Post by gameryoshi600 on 2008-05-09
what about the problem after?

---

### Post by Joeb454 on 2008-05-09
Which part?

To add the Wine repositories properly, follow the instructions on [this page]("http://www.winehq.org/site/download-deb")

Edit: If you are too lazy I've copied the commands into the quote Window below :)
> 
First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Hardy (8.04):
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

Then update APT's package information by running 'sudo apt-get update'. 

---

### Post by gameryoshi600 on 2008-05-09
no the line after the wine thing.

---

### Post by Joeb454 on 2008-05-09
Hmm, I'm not sure about that last one, sorry :(

---

### Post by gameryoshi600 on 2008-05-09
it says i need to apt-cdrom or something
edit:
heres what it says
```
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
```

---

### Post by Joeb454 on 2008-05-09
Ok so you can either edit the sources.list the same way as before and comment out the CD-ROM as a source do this by putting a '#' at the beginning of the line.

Or go to System > Adminstration > Software Sources and make sure that the CD ROM is **not** checked/enabled :)

---

### Post by gameryoshi600 on 2008-05-09
what will the second one do? just wondering

---

### Post by Joeb454 on 2008-05-09
The second one will just do the same thing, but in a GUI (graphically) :D

I just wanted to throw it out there so you knew that you could do it more than one way :)

---

### Post by gameryoshi600 on 2008-05-09
what will disabling the CD-rom do?

---

### Post by Joeb454 on 2008-05-09
It just means it won't ask you to insert the CD to install some packages, usually build-essential requires you to insert the CD.

However I disabled mine, as I usually don't have the CD handy when I want to install something. If the CD is disabled it will simply download the packages from the internet instead :)

---

### Post by gameryoshi600 on 2008-05-09
thanks. i do prefer doing the dl from the internet.

---

### Post by Joeb454 on 2008-05-09
Me too, I found I kept wanting to install the odd app while at Uni. Sometimes just to test something for an answer on the forums :p (Yeah I'm nice like that)

---

