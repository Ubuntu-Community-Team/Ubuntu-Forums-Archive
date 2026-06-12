---
title: "tools of the trade?"
date: 2007-01-11
forum: Other OS Talk
---

### Post by fuscia on 2007-01-11
i don't know if this is possible, but i'm wondering if i can edit an .iso of a live cd to include firmware for my wireless card (ipw2915). as i was starting to think about this, i realized i had no clue how to open an .iso file. what do i need to use to do this? and, while i'm at it, are there a bunch of useful tools for exploring other distros that i also don't know about?

---

### Post by rowanparker on 2007-01-11
Just use archive manager.

---

### Post by 3rdalbum on 2007-01-12
> **rowanparker said:**
> Just use archive manager.

It doesn't work like that, sorry.

[https://help.ubuntu.com/community/LiveCDCustomization/6%2e06]("https://help.ubuntu.com/community/LiveCDCustomization/6%2e06")

That page tells you how to do it manually. It revolves around extracting the ISO and then extracting the SquashFS filesystem, making changes to it, then putting it all back together again. Or, if the drivers are available from the repos, you could use Reconstructor to help you do it automatically.

---

### Post by rowanparker on 2007-01-12
> **3rdalbum said:**
> It doesn't work like that, sorry.

[https://help.ubuntu.com/community/LiveCDCustomization/6%2e06]("https://help.ubuntu.com/community/LiveCDCustomization/6%2e06")

That page tells you how to do it manually. It revolves around extracting the ISO and then extracting the SquashFS filesystem, making changes to it, then putting it all back together again. Or, if the drivers are available from the repos, you could use Reconstructor to help you do it automatically.
Oh right.

Sorry, I was just talking a stab in the dark :)

---

### Post by fuscia on 2007-01-12
ark wouldn't open it, but xarchiver did.

---

### Post by mips on 2007-01-12
The easy way to modify iso images:
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

---

### Post by slimdog360 on 2007-01-12
go into synaptic and search for 'bootcd'. I havent used it but it looks good, or at least from the description it looks good.

---

### Post by happy-and-lost on 2007-01-17
It's not ideal, but what I've done to ease reinstallation blues is write a bash script which executes everything I like to be done on a fresh install. Stuff like installing Automatix, AIGLX, changing default shell to back to bash, reinstalling my themes and copying them to /usr/share/themes... you get the point. I've just got it in a folder full of sources for the stuff I like, and let it rip whenever I do a fresh install.

---

