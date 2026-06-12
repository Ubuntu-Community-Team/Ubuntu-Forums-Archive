---
title: "Wine on 12.04 (64bit)"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by wormbuntu on 2012-11-12
Hi - any tips gratefully received. I've been googling for a couple of hours but no luck so far.

I'm trying to install Wine on 12.04 64bit (clean install). As you can guess, I get an error...

I tried the usual apt-get and dpkg commands. With no apparent effect. I've also tried "edit / fix broken packages" in Synaptic.


using apt-get install:

 [COLOR="Blue"]wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
[/COLOR]

In Synaptic Package manager I get:
[COLOR="blue"]To Be Removed
libpurple0
libsasl2-modules
telepathy-haze
ubuntu-desktop

To be installed
(lots)[/COLOR]

I haven't OK'd the message in Synaptic, as I'm not sure whether I need those packages for something else. I'm also wondering why the apt-get error message is so vague. The first 3 seem related to IM/Pidgin. But ubuntu-desktop sounds kind of important.

NB I've got a pretty standard system, with the only odd thing that I had to install bumblebee to support optimus video-card. Not sure if this is related.

Thanks in advance
W.

---

### Post by ubudog on 2012-11-12
Don't OK that message, ubuntu-desktop is important.

Open up Synaptic and search for 'wine'.  Try removing all the Wine packages you have currently installed.  Be sure that it does not try to remove ubuntu-desktop or any package other than wine when doing this. 

Then, open Synaptic and try to install wine again.

Best of luck,
ubudog

---

### Post by wormbuntu on 2012-12-09
> **ubudog said:**
> Don't OK that message, ubuntu-desktop is important.

Open up Synaptic and search for 'wine'.  Try removing all the Wine packages you have currently installed.  Be sure that it does not try to remove ubuntu-desktop or any package other than wine when doing this. 

Then, open Synaptic and try to install wine again.

Best of luck,
ubudog

Mate - a belated thankyou - been travelling so only just went through it but all seems ok now.

Cheers

---

### Post by xxmontyxx on 2012-12-09
first update you ubuntu softwares then goto terminal and type "sudo apt-get install wine"
then after following instruction type y:lolflag:



also reply me to my account if  it works or not and add me as friend in ubuntuforam and "facebook as Bhavdeep"

---

### Post by ubudog on 2012-12-09
> **wormbuntu said:**
> Mate - a belated thankyou - been travelling so only just went through it but all seems ok now.

Cheers

Great, glad that worked.  :)

---

### Post by xjas on 2013-01-23
Just thought I'd bump this thread; I was having the **exact** same problem (on a fresh install of 12.04 64 bit), same packages marked for removal and everything. I'm guessing it was something to do with old version dependencies in Synaptic (maybe old data cached for one of the repositories maybe?)

I ended up going into the update manager and installing all the "critical" and "recommended" updates, restarted the PC, ran Synaptic again and Wine installation went fine that time. It had to download about 200 MB of dependencies but nothing marked for removal and no conflicts/errors.

I realize the OP got it working already but I figured I'd post here anyway to help the next person who comes along.

---

