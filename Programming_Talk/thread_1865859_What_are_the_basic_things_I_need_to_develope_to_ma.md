---
title: "What are the basic things I need to develope to make an os that works?"
date: 2011-10-20
forum: Programming Talk
---

### Post by /bin/sh on 2011-10-20
What are the basic things I need to develope to make an os that works? It will be based on linux.

---

### Post by deloquencia on 2011-10-20
An own OS, based on Linux? 

Check and start with the project Linux from Scratch ([http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)), it describes the process of creating an own Linux based system.

Why do you need one? For embedding, for studies or for fun? 

The main disadvantage with such an own system will be the lack of some smarter update functionality and updating manually will be a tough hassle to do.

Some years back I created a Linux from scratch, in the project docs it's well described and you'll learn a lot but using such system will be not so smooth like using an already developed and pre-packaged distribution. Just think about all these dependencies you'll stumble upon...


Good luck :)

---

### Post by /bin/sh on 2011-10-20
My os will support updates for other linuxes so thats not an issue. Not for fun, for general use of everybody.

---

### Post by deloquencia on 2011-10-22
Great idea, but how're you going to make it? 

Maintaining an up to date software repository for your new OS means things like retrieving patches, in-cooperating the patches, compiling sources updated that way or another, reasonable packaging, dealing with different dependencies, providing an update infrastructure with enough bandwidth, supporting the users, bughunting and -fixing... 

**It's an issue!**

Just start with the fun and than think about general use :)

---

### Post by haqking on 2011-10-22
> **/bin/sh said:**
> My os will support updates for other linuxes so thats not an issue. Not for fun, for general use of everybody.

other linuxes ?

There is only one linux and there are distros who build there own system around the linux kernel.

You are saying you want to create your own distribution and that will have the updates of all the other distros ?

i think you have some jumbled ideas ;-)

---

### Post by cgroza on 2011-10-22
Wait, do you want to write one from scratch?
Then in this case, you should start with a kernel.

---

### Post by Dangertux on 2011-10-22
Sounds like you have a lot of work cut out. Projects like this usually have multiple (many) members contributing to them. This is probably not something you should venture into alone. Maybe consider getting some experience contributing to another distro first? 

If you want to get really hands on get involved with a smaller project, but at least learn the basics of what other distributions are doing before deciding to branch off and make you're own. That would be my suggestion.

Alternatively you could just repack Ubuntu like so many other distros have done.

---

### Post by gnometorule on 2011-10-22
Have a look at a book on the topic like "Understanding the Linux Kernel" (Bovet/Cesati), usually found in software engineering sections of larger bookstores, and probably decide to choose a somewhat more modest goal within kernel development. This is a gargantuan task, even for a Linux 1.0 kernel, for extremely experienced engineers.

---

### Post by scitron on 2011-10-22
I would start by learning and studying MINIX on which Linus Torvals based Linux.

From reading on their website the new [MINIX 3]("http://www.minix3.org/") has changed some from the goals of the original which was mostly intended as a teaching tool.

The new MINIX is still a relatively small OS and useful for learning with the book _Operating Systems Design and Implementation, 3rd Edition_.

[IMG]http://www.minix3.org/logo.gif[/IMG]

---

