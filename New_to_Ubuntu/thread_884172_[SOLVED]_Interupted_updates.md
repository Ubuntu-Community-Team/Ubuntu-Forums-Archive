---
title: "[SOLVED] Interupted updates"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by hopkinsjeni on 2008-08-08
Could someone please help me. A few days ago I was installing some updates and they got interrupted. Ever since my little update icon has been like a red stop sign. When I hover over it it says the package 'deskbar-applet' needs to be re-installed. My system can't find the original package and I don't know what it is or where it comes from. Can someone please advise me as to what I can do? 
Thank you

---

### Post by bump_ on 2008-08-08
Try this:

Go to Applications -> Accessories -> Terminal

In the terminal, type

```
sudo apt-get install -f
```

and see what happens

---

### Post by Ryadt on 2008-08-08
Type in terminal
```
sudo apt-get install deskbar-applet
```

---

### Post by InfinityCircuit on 2008-08-08
```
dmr@skynet:~$ rmadison deskbar-applet
deskbar-applet | 2.14.1.1-0ubuntu3 |        dapper | source, amd64, i386, powerpc
deskbar-applet | 2.14.2-0ubuntu1 | dapper-updates | source, amd64, i386, powerpc
deskbar-applet | 2.18.1-0ubuntu2 |        feisty | source, amd64, i386, powerpc
deskbar-applet | 2.20.0-0ubuntu2 |         gutsy | source, amd64, i386, powerpc
deskbar-applet | 2.20.1-0ubuntu1 | gutsy-updates | source, amd64, i386, powerpc
deskbar-applet | 2.22.1-0ubuntu1 |         hardy | source, amd64, i386
deskbar-applet | 2.22.3-0ubuntu1 | hardy-updates | source, amd64, i386
deskbar-applet | 2.22.3.1-0ubuntu1 | hardy-proposed | source, amd64, i386
deskbar-applet | 2.23.6-0ubuntu1 |      intrepid | source, amd64, i386

```

Please try:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get install --reinstall -f deskbar-applet
```

---

### Post by hopkinsjeni on 2008-08-08
Please try:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

I got this far with it working beautifully and the little red stop sign disappeared but the next bit didnt work -

sudo apt-get install --reinstall -f deskbar-applet
```[/QUOTE]

The terminal said:

E: The package deskbar-applet needs to be reinstalled, but I can't find an archive for it.


any ideas what's going on?

---

### Post by hopkinsjeni on 2008-08-22
Thanks everyone for your advice. I just wanted to let you know, incase anyone else should have this problem that I solved it weirdly enough by going to 
System > Administration > Services: I fiddled around with the update options and it re-installed deskbar-applet and all is well again.

---

