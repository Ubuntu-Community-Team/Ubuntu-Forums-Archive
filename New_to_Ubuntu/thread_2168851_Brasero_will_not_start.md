---
title: "Brasero will not start"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by ed5 on 2013-08-19
When I click on the Brasero button it just quickly flashes onto the
screen then disappears.  Everything else on the computer is working fine.
Anyone have any idea what is causing this? I tried reinstalling Brasero but
that didn't help

---

### Post by GwL3eNC on 2013-08-19
Hello,

can you try starting brasero over terminal. Yust open a terminal and
type

brasero

so we can hopefully see an error message. If so, please post it here.

---

### Post by ed5 on 2013-08-19
> **GwL3eNC said:**
> Hello,

can you try starting brasero over terminal. You open a terminal and
type

brasero

so we can hopefully see an error message. If so, please post it here.

It says "command not found". I am use to using terminal and have never seen it act like this.

---

### Post by GwL3eNC on 2013-08-19
Hmm,

what do you have under

sudo dpkg -l | grep brasero

I have

ii  brasero                                   3.4.1-0ubuntu1.1                                    CD/DVD burning application for GNOME
ii  brasero-cdrkit                            3.4.1-0ubuntu1.1                                    cdrkit extensions for the Brasero burning application
ii  brasero-common                            3.4.1-0ubuntu1.1                                    Common files for the Brasero CD burning application and library
ii  libbrasero-media3-1                       3.4.1-0ubuntu1.1                                    CD/DVD burning library for GNOME - runtime

---

### Post by ed5 on 2013-08-19
> **GwL3eNC said:**
> Hmm,

what do you have under

sudo dpkg -l | grep brasero

I have

ii  brasero                                   3.4.1-0ubuntu1.1                                    CD/DVD burning application for GNOME
ii  brasero-cdrkit                            3.4.1-0ubuntu1.1                                    cdrkit extensions for the Brasero burning application
ii  brasero-common                            3.4.1-0ubuntu1.1                                    Common files for the Brasero CD burning application and library
ii  libbrasero-media3-1                       3.4.1-0ubuntu1.1                                    CD/DVD burning library for GNOME - runtime

ii  brasero                                    2.30.2-0ubuntu1.1                                 CD/DVD burning application for GNOME
ii  brasero-common                             2.30.2-0ubuntu1.1                                 Common files for the Brasero CD burning appl
ii  libbrasero-media0                          2.30.2-0ubuntu1.1                                 CD/DVD burning library for GNOME - runtime
ii  python-brasero                             2.30.0-0ubuntu1.1                                 Python module for brasero

---

### Post by GwL3eNC on 2013-08-19
looks like all packages are there. I found brasero in 

/usr/bin/brasero
/usr/share/menu/brasero

because of your message the /usr/bin/brasero is missing, i think. Evtl you can copy
/usr/share/menu/brasero to /usr/bin/brasero. If you got /usr/share/menu/brasero.

---

### Post by ed5 on 2013-08-19
> **GwL3eNC said:**
> looks like all packages are there. I found brasero in 

/usr/bin/brasero
/usr/share/menu/brasero

because of your message the /usr/bin/brasero is missing, i think. Evtl you can copy
/usr/share/menu/brasero to /usr/bin/brasero. If you got /usr/share/menu/brasero.

Tried it and it didn't work. Thanks for trying.

---

### Post by GwL3eNC on 2013-08-19
was a sily idea, i'm sorry. the thing in /usr/share/menu/ is naturaly ony a link. I'm a fool.
Now the ony thing i coud do would be

sudo apt-get purge brasero
sudo apt-get update
sudo apt-get install brasero

but i believe you have already done that. Good luck.

---

### Post by ed5 on 2013-08-19
> **GwL3eNC said:**
> was a sily idea, i'm sorry. the thing in /usr/share/menu/ is naturaly ony a link. I'm a fool.
Now the ony thing i coud do would be

sudo apt-get purge brasero
sudo apt-get update
sudo apt-get install brasero

but i believe you have already done that. Good luck.

I found the problem.  I always thought when you shut-down Ubuntu it ended all process...apparently not.
I looked in System Monitor and there was already a copy of Brasero running despite the computer having been rebooted
several times.  I ended the running copy of Brasero and now it works fine again. Hope this helps out someone
with a similar problem. Again, thanks for your help.

---

### Post by Zill on 2013-08-20
There are several bug reports on this problem.  e.g. See [Bug #907311]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/907311")

---

