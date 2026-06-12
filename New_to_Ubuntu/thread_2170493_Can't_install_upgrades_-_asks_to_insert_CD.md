---
title: "Can't install upgrades - asks to insert CD"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by micox2 on 2013-08-26
Was told to re-install 12.04 to access other disc on my Toshiba Satellite. Got 12.04 download onto a CD as instructed - took hours and hours to download and was useless.
 
Upgrades asks for this CD when told to install upgrades and fails when the CD is installed. Not inserting the CD has the same effect. I now have over 300 upgrades waiting! How do I get past this?:mad:

---

### Post by The Cog on 2013-08-26
Welcome to the forums.

Updates don't come from a server unless the PC knows there are updates waiting. There are two phases to doing an update. On the command line, the first is
```
sudo apt-get update
```
which tells the PC to go to the servers to download a list of the latest versions of all the packages - update its database. Then 
```
sudo apt-get upgrade
```
which tells it to go ahead and download/install all those updates, upgrading everything that can be upgraded.

Until it has updated its list from the database from the net, the only software sources it knows about is the CD it installed from.

If "sudo apt-get update" gives youi any error messages, report them back here and we will try to figure out why.

---

### Post by ahmad3 on 2013-08-26
try to do
 ```
Sudo su
```
then
```
Apt-get update && apt-get upgrade
```
if it didnt work post the errors it gives you

---

### Post by Elfy on 2013-08-26
> **micox2 said:**
> Was told to re-install 12.04 to access other disc on my Toshiba Satellite. Got 12.04 download onto a CD as instructed - took hours and hours to download and was useless.
 
Upgrades asks for this CD when told to install upgrades and fails when the CD is installed. Not inserting the CD has the same effect. I now have over 300 upgrades waiting! How do I get past this?:mad:

You might need to disable the cd in your sources. 

Open Software Sources from the menu or dash - go to the Other Software tab - disable the cdrom.

Then try updating and upgrading again

> **ahmad3 said:**
> try to do
 ```
Sudo su
```
then
```
Apt-get update && apt-get upgrade
```
if it didnt work post the errors it gives you
Why use su? 

Why not just 

```
sudo apt-get update && sudo apt-get upgrade
```

In addition your command will fail, you need apt-get not Apt-get ;)

---

