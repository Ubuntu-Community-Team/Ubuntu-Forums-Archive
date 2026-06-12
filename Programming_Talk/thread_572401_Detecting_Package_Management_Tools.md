---
title: "Detecting Package Management Tools"
date: 2007-10-10
forum: Programming Talk
---

### Post by thomasaaron on 2007-10-10
Hey, folks.

I need to write a program that will detect if any package management tools are running (apt-get, aptitude, synaptic, etc...).

I know I could look at running processes and grep out key words. But is there a more sophisticated way to do this?

If you try to run two package management tools at the same time, it throws this error...

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

...but I'm having a little difficulty understanding how to take advantage of this built-in mechanism in my own program.

As always, thanks much for your insight.

Best,
Tom

---

### Post by thomasaaron on 2007-10-12
*bump*

No ideas?

---

### Post by moma on 2007-10-13
Can you check the Synaptic's source code. Get the source 

$ [COLOR="SeaGreen"]apt-get source synaptic[/COLOR]

$ [COLOR="SeaGreen"]cd synaptic*[/COLOR]

Open the "gtk/gsynaptic.cc" file and search for function names [COLOR="DarkRed"]check_and_aquire_lock[/COLOR]() and [COLOR="DarkRed"]TestLock[/COLOR]() or just search for the [COLOR="DarkRed"]dpkg[/COLOR] word.
$ [COLOR="SeaGreen"]gedit gtk/gsynaptic.cc[/COLOR]

Note: apt-get source needs "dpkg-dev" package. and the deb-src... (source code) repositories must be activated in /etc/apt/sources.list

---

### Post by thomasaaron on 2007-10-13
Sweet. Thank you.

I'll do that. I'm pretty good with java and python. Never messed with C/C++. I will probably take you up on help analyzing the code.

Best,
Tom

---

