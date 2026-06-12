---
title: "compiling lifeograph"
date: 2010-11-20
forum: Packaging and Compiling Programs
---

### Post by slwx on 2010-11-20
Hi,
I posted this question earlier under general help, but I didn't get any reply, maybe it fits more here.
I would like to adjust the journal program called lifeograph. I was wondering if i could get some help.. 
First I would like to build it, clean without any adjustments.

I'm using this version: [https://launchpad.net/lifeograph/0.6/0.6.3](https://launchpad.net/lifeograph/0.6/0.6.3) 

Readme file says:

Requirements
-----------
Lifeograph requires the following modules to be built:
    * gtkmm,
    * gconfmm,
    * gtkspell, and
    * gcrypt.

Installation
------------
Type "make" to build and "make install" to install (all without quotes).
No configuration atm.

I tried make, but it doenst really work. So i think i dont have good requirements. 

-> how do I install the required modules?
-> I've found some in packet manager, but some appear to be librarys. Can some1 explain the difference?

Thanks,
Mathi

---

### Post by SevenMachines on 2010-11-22
To build things you need the development packages, libraries will usually be precompiled binaries whereas dev packages will usually have headers amongst other useful development stuff for the library. These usually end in a -dev extension. So if something says you need gconfmm to compile, then search for 'gconfmm dev' in your package manager like synaptic

> $ apt-cache -n search .*gconfmm.*dev
libgconfmm-2.6-dev - C++ wrappers for GConf (development files)

---

### Post by slwx on 2010-11-26
Hi,
thanks for the reply! I had givin up, but now it compiled, and im translating the program in dutch :)
The problem was in gcrypt.
So one last question, when I type "gcrypt" in package manager, I dont find any hit. 
but when i search with terminal like you explained, I did find it... How is this?

thx, 
Mathi

---

### Post by SevenMachines on 2010-11-26
Hi, if by package manager you mean synaptic (main menu->system->administration->synaptic) then you should get a few hits with a 'gcrypt' search. If you mean 'ubuntu software centre' you won't get any, its a simpler user-friendly app-store thing, not for more advanced uses.

---

### Post by slwx on 2010-11-26
I retried it, and i get nothing!
(see screenshot)
i opened packet resources to.
thx,
Mathi

---

### Post by SevenMachines on 2010-11-26
Try it using edit->search or ctrl-F, the search box in the top right is xapian indexed or something, like it says, it needs to index :) i tend to find it buggy myself but ctrl-f always works

---

### Post by slwx on 2010-11-26
:-o   ooooh, figures! now it works.
Thanks for replys ;)
Mathi

---

