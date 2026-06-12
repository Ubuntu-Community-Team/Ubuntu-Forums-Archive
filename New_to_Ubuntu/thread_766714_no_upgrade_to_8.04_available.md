---
title: "no upgrade to 8.04 available"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by abraxas334 on 2008-04-25
Hi there,
i would like to upgrade from 7.10 to 8.04 but for some reason when i go to the update manager i do not get the option to do so. I also tried it using the command line, but it just keeps telling me, that my system is up to date.
I also dl the iso and burned it onto cd but my cd drive will not recognise the cd. I don't really want to reinstall from scratch as my home and root are on the same partition and i have not enough hd space to backup my home.

Any ideas?
Thanks for the help

---

### Post by Joeb454 on 2008-04-25
Did you do ```
gksudo update-manager -d
``` from a terminal?

If so let us know, and are you sure you are not already running 8.04 ;) :lolflag:

---

### Post by StOoZ on 2008-04-25
im yet to update, but I downloaded the alternate CD.
updating from a CD is more reliable from a web server which can "fall" etc...

---

### Post by forestpixie on 2008-04-25
Do ALt+F2 and paste this into the terminal

```
gksu "sh /cdrom/cdromupgrade"
```

---

### Post by abraxas334 on 2008-04-25
when i type:
```
gksudo update-manager -d 
```,
i get warning could not initiate debus.
And no I am still on gutys.
When i type 
```
cat /etc/lsb-release 
```
i get:
DISTRIB_ID=Ubuntu

DISTRIB_RELEASE=7.10

DISTRIB_CODENAME=gutsy

DISTRIB_DESCRIPTION="Ubuntu 7.10"
so not sure what is happening

---

### Post by tom56 on 2008-04-25
If I were you I'd wait a few days then try again - the servers are swamped at the moment anyway.

---

### Post by abraxas334 on 2008-04-25
I know that the servers are swamped and its not about doing the update straight away i would just like to be able to have the option in the first place. :)

---

### Post by ptcbus on 2008-04-25
If you are upgrading using an alternate CD, then you need not go to the terminal and type commands. The CD should autorun and show you options for upgrading. See [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by abraxas334 on 2008-04-25
I know the CD should auto run, which it does on my ubuntu system i burned it from at lowest possible speed, however the CD drive from the computer i am trying to upgrade does not seem to recognise the CD, its spinning but not mounting it (or whatever u call it ) :(. Audio CD work fine just any burned CD's will not work.

---

