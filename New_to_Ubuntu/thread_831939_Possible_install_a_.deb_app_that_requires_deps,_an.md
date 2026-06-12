---
title: "Possible install a .deb app that requires deps, and then uninstall EVRITHING?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Kosimo on 2008-06-17
I've just downloaded the latest GNOME-DO from getdeb. When installing the system automatically installed some dependencies.  I'm sure that when uninstalling GNOME-DO from synaptic I will keep all the dependencies installed. I don't need them anymore. This makes me feel my system as (dirty).  Question is, it is possible to follow somehow those dependencies and then uninstall everything?

Thank you

---

### Post by rraj.be on 2008-06-17
You can use 


complete removal option if you dont want any more that packages.

or use this in terminal

sudo apt-get remove --purge <application name>

---

### Post by Troll_the_Great on 2008-06-17
And I think if you run this command you will get rid of unneeded software:

```
sudo apt-get autoremove
```

---

### Post by ChameleonDave on 2008-06-17
> **rraj.be said:**
> You can use 


complete removal option if you dont want any more that packages.

or use this in terminal

sudo apt-get remove --purge <application name>
Nah.  That'll only get rid of config files.  He wants to get rid of dependent packages.

As far as I know, there is no way to do this perfectly, because the system cannot know what dependent packages you might actually want.

All you can do is go to Synaptic and see if anything is marked as being autoremovable.

---

També hi ha la possibilitat de mirar (en el Synaptic) quines són les dependències del programa, i anar cercant-les per a borrar-les, si és que les altres solucions que et donem no et funcionen.

---

### Post by oldos2er on 2008-06-17
Use deborphan.

---

### Post by Kosimo on 2008-06-17
Uhm...
Thank you all for answering.. But now I'm a bit more lose than before :P

So, I knew that doing a (COMPLETE REMOVE) doesn't really delete all dependencies installed by that particular program.  

So, by doing sudo apt-get autoremove what is exactly what I'm doing?

---

### Post by oldos2er on 2008-06-17
"man apt-get" says: autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

---

### Post by Kosimo on 2008-06-18
> **oldos2er said:**
> "man apt-get" says: autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

Cool, that is the answer I've been looking for.

---

