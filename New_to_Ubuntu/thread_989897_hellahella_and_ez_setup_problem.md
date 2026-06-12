---
title: "hellahella and ez_setup problem"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by TripitakaUK on 2008-11-22
A week into ubuntu and I'm feeling quite proud of my bad self! I have it streaming to my xbox360 via fuppes and I have hellanzb configured and working. However...

This whole python thing has me beat. I am trying to get the hellahella front end working but failing repeatedly.

I have installed the python stuff through synaptic and grabbed the ez_setup.py script but have no idea where to put it. If I run the command:

sudo python ez_setup.py -U hellahella==dev

I get the following:

python: can't openfile 'ez_setup.py': [Errno 2] No such file or directory

I'm assuming that I don't have it in the right place - where should it be?

---

### Post by TripitakaUK on 2008-11-22
ended up going with the .deb install of LottaNZB which may have been the better choice but I still have the python problem.

Any ideas?

---

### Post by stolk on 2009-04-02
> **TripitakaUK said:**
> A week into ubuntu and I'm feeling quite proud of my bad self! I have it streaming to my xbox360 via fuppes and I have hellanzb configured and working. However...

This whole python thing has me beat. I am trying to get the hellahella front end working but failing repeatedly.

I have installed the python stuff through synaptic and grabbed the ez_setup.py script but have no idea where to put it. If I run the command:

sudo python ez_setup.py -U hellahella==dev

I get the following:

python: can't openfile 'ez_setup.py': [Errno 2] No such file or directory

I'm assuming that I don't have it in the right place - where should it be?

you have to download the "ez_setup.py" file: download it here:

[http://hellanzb.com/trac/hellanzb/wiki/HellaHella](http://hellanzb.com/trac/hellanzb/wiki/HellaHella)

then go to the directory you've downloaded this file and run the command again

regards,

---

