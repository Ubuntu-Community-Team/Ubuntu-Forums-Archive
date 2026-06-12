---
title: "Editing file from ubuntu in another o/s"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by phil66 on 2012-12-08
Ubuntu-10.04

I have Ubuntu-10.04 on sda1 and Mageia2 on sdb5

After mounting Mageia from Ubuntu I want to edit a file that is in the /opt folder

When doing this the file from Ubuntu /opt opens not the one in Mageia

Both files in Ubuntu and Mageia are in the /opt folder

How can I open the one in mageia ??

---

### Post by audiomick on 2012-12-08
Tell us how you are trying to open the file. That may well have a bearing on the problem.

---

### Post by phil66 on 2012-12-08
Audiomick

Thanks for the reply

In Ubuntu I click on places > and mount Mageia it shows on desktop as mounted

In Mageia I click on /opt/Moneydance/Moneydance

It then opens the Ubuntu Moneydance file instead of the Mageia file

---

### Post by audiomick on 2012-12-08
Hmmm, that sounds quite odd.

The first thing I would do is open gedit and try open the file from there instead of clicking on it.

The folder /opt belongs to root, so you will need root privileges to change anything in there. I think you will need to start gedit with
```
gksudo gedit
```
from a terminal and then choose "open" from the file menu and navigate to the location of the file you want to edit.

---

### Post by phil66 on 2012-12-09
Micheal

Using gedit and navigating to the application still opens the Ubuntu one

A suggestion in the irc channel said to use /media/mountpoint /mnt

How would I use that command

Thanks
Ray

---

### Post by audiomick on 2012-12-09
Sorry, can't help you with that.

---

