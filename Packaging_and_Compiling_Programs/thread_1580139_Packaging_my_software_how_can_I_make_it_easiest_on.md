---
title: "Packaging my software: how can I make it easiest on the user?"
date: 2010-09-22
forum: Packaging and Compiling Programs
---

### Post by papillion on 2010-09-22
So I'm just about done creating what I think it going to be a fantastic piece of software for Linux.  My target audience though is not terribly tech savvy and I want to make it as easy as possible for them to install and start to use the software.

The program might have some dependencies that aren't on everyone's system, but I don't want to put my users through the pain of 'go get this library and this software, and blah, blah, blah". I want to include and install everything they'll need to run my software when they download it.

What is the best way to package it so that this can be accomplished? If simply creating a DEB package going to make sure all dependencies are satisfied?

Thanks!
Anthony

---

### Post by TNT1 on 2010-09-23
Dunno what your software is, but a lot of us would be cautious of a .deb from a new/unknown source...

---

### Post by SevenMachines on 2010-09-23
I'm guessing it might depend on what exactly your package depends on but debian packages and through them the apt packaging system will handle all the dependency issues. The simplest way i can imagine of packaging something that requires things not available in the main repositories is

* Create a launchpad ppa
* Add unavailable dependency packages to ppa
* Add main package to ppa
* Main package will use ppa dependency packages to build successfully
* Main package and dependencies will be installed when people add your ppa and install your main package

---

### Post by papillion on 2010-09-24
> **TNT1 said:**
> Dunno what your software is, but a lot of us would be cautious of a .deb from a new/unknown source...

I wondered about that. So .deb is probably out. I see someone mentioned a ppa which is probably better anyway. Thanks for the input.

---

### Post by Bachstelze on 2010-09-24
> **papillion said:**
> I wondered about that. So .deb is probably out. I see someone mentioned a ppa which is probably better anyway. Thanks for the input.

That doesn't change anything. A package on a PPA is a DEB too. ;) Is someone won't install a DEB downloaded from your website, they won't install it from your PPA either.

---

