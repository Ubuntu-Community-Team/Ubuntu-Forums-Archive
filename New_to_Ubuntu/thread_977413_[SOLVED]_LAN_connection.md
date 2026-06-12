---
title: "[SOLVED] LAN connection"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by ashurd10 on 2008-11-10
hi all
i want to connect 2 windows computers thru LAN.
wht al i hav 2 do??
m using ubuntu 8.10
thanx in advance

---

### Post by Peter09 on 2008-11-10
In Places->network can you see the other computer?

---

### Post by superprash2003 on 2008-11-10
so you just want to connect the 2 windows pcs?? not the ubuntu one?? the ubuntu has nothing to do with it?? do you want to share files??? what do you intend to do after connecting them via LAN?

---

### Post by ashurd10 on 2008-11-11
ya i want to connct to ubuntu comps too..
i wany share files too
n i want tht to access other pc's n i shud be accesbl by them..

---

### Post by ashurd10 on 2008-11-11
no i cant c any computers in 
Places->network

---

### Post by Liviu-Theodor on 2008-11-11
On Windows, you should enable the [COLOR="Blue"]File and Printer Sharing[/COLOR] service. On Ubuntu, you should install the [COLOR="DarkOrange"]Samba[/COLOR] service.

---

### Post by ashurd10 on 2008-11-11
i installd samba
sudo apt-get install samba
is it enough or there r som more..
thanx

---

### Post by Liviu-Theodor on 2008-11-12
You should modify the properties for the files/folders you want to use in common on more than one computer to be shared, on each system you want. That should work.

---

### Post by Kellemora on 2008-11-12
Hi ash

Yes there IS more!

```
sudo apt-get install smbclient
```
```
sudo apt-get install smbtree
``` (it's a handy tool)

In order to SEE shares, you must have something shared to see.
So create a folder on each machine that says something like SharedFiles, then SHARE IT.

From a Terminal, if you type just smbtree it should list all of your shared folders, a shared printer if you shared a printer, etc.

Sometimes you have to reboot to get the shares to show up!

TTUL
Gary

---

### Post by ashurd10 on 2008-11-13
thank u all...
job done...

---

