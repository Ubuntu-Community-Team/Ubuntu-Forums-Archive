---
title: "Compiz Fusion - Doesn't work on 8.10?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by firemaker272 on 2008-10-31
Hey all, I've got a little problem trying to install compiz-fusion on ubuntu 8,10

Earlier in the year I installed the older version of ubuntu and got all the features working fine, i uninstalled it due to lack of diskspace and now i've got my external, i've been able to re-install it.
But I can't seem to add the compiz-fusion features back? :confused:

Please someone help me, with either telling me what to type in terminal or what I need to download.

Thanks

-Firemaker272

---

### Post by spiderbatdad on 2008-10-31
8.10 comes with compiz. You shouldn't have had to install it. Just install compizconfig-settings-manager and launch it from your system preferences menu.

---

### Post by poldie on 2008-10-31
> **spiderbatdad said:**
> 8.10 comes with compiz. You shouldn't have had to install it. Just install compizconfig-settings-manager and launch it from your system preferences menu.

For some reason Ubuntu never ships with the fusion icon or the settings manager, both of which are required.  Install both of those and you can use compiz properly.

---

### Post by firemaker272 on 2008-10-31
And how excatly do I install compizconfig-settings-manager?


Sorry im a noob :(

---

### Post by th89 on 2008-10-31
go to terminal and type in:
sudo apt-get install compizconfig-settings-manager

---

### Post by RequinB4 on 2008-10-31
> **firemaker272 said:**
> And how excatly do I install compizconfig-settings-manager?


Sorry im a noob :(

We were all new once :)

go to system - administration - synaptic package manager

and install the package (you can use the search function)

Edit: th89, it's better to recommend synaptic, especially to newer users.  There are always multiple ways of doing things.

---

### Post by spiderbatdad on 2008-10-31
> **poldie said:**
> For some reason Ubuntu never ships with the fusion icon or the settings manager, both of which are required.  Install both of those and you can use compiz properly.

Fusion icon is not required.

---

### Post by firemaker272 on 2008-10-31
Humm, I've seemed to install it, and I can go to System > Preferences > CompizConfig Settings Manager, I've selected the settings I'd like to use, but nothing happens when i trigger the key commands.... and when i go to my desktop, right click > change desktop background > visual effects > extra - it says "Desktop effects could not be enabled"

:/

---

### Post by th89 on 2008-10-31
Sounds like a driver issue. Try going to System > Administration > Hardware Drivers and see if there are any proprietary drivers you can enable.

---

### Post by Orwell on 2008-10-31
Never apologize for asking a question mate, we've all been there!

Once you get it up and running, check out the 'Cube Reflection and Deformation' setting under Effects...makes a cool change to the infamous desktop cube.

---

### Post by firemaker272 on 2008-10-31
Thank you very much, th89, I had an older version of the driver installed :p

Thanks again,

-Firemaker

---

### Post by th89 on 2008-10-31
Noo problem. Glad to help. :P

---

