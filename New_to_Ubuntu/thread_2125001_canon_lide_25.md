---
title: "canon lide 25"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by brinzoo on 2013-03-12
Just installed 12.10 desktop. Was using XP.  
Samsung printer ml1665 working ok, but struggling to install Canoscan 25 and Canon Lide 25 scanner ! My cd-rom is for Windows or Macintosh.
Can anyone help?

---

### Post by pdc on 2013-03-12
SANE is the website to look on for scanning support;

if I drill into it, for manufacturer's support: Canon 

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

the Lide 25 is not mentioned; however support for the 35 and 40 is good ....one can only hope the 25 is the same ..

Most folks use the programme xsane as a frontend GUI programme to drive sane, the backend

on the ubuntu hardware wiki

[https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon)

it seems it worked "out of the box" in 2010;

can you check you have xsane installed; and the USB port you connect to is fine; and you connect directly from scanner to computer (ie avoiding usb hub).......

if you type

> [COLOR="#FF0000"]lsusb[/COLOR]

in a terminal.............. you should see 

> ID 04a9:2220 Canon Inc ........I believe that is the ID of the scanner; if you do not see that, there is some hardware connection

There is a programme called synaptic which manages the installation and deletion of programmes: I enclose a snapshot of what mine shows when I search on "sane"

can we see how we do with the above, and move from there as needed

---

### Post by brinzoo on 2013-03-13
pdc--many thanks for your reply;lots for me to checkout. will post if I sort it

---

