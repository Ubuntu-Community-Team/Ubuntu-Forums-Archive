---
title: "Will upgrading from 11.04 to 11.10 make stuff buggy?"
date: 2011-07-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cheesekiller on 2011-07-28
Will upgrading from 11.04 to 11.10 make stuff buggy and not work?

When i upgraded from 10.10 to 11.04 i had to go through and fresh install and back data up on all my computers....  i really dont wanna do that and considering the amount of stuff i have on this one right here i certainly don't want to do that.  will upgrading from 11.04 to 11.10 be any easier? It would be awesome if it "just worked"

---

### Post by EgoGratis on 2011-07-28
It depends. I upgraded from 10.10 to 11.04 without problems. What problems did you have? 

Is it possible yes that the same problem will happen again if for example was hardware related.

---

### Post by cheesekiller on 2011-07-28
everything was laggy and the launcher didnt work and alot of programs didnt work. as for hardware this computer is a brand new system76 so i guess it will be ok?     i also have an acer aspire netbook which runs unity 3d just fine but the 10.10 to 11.04 killed it, and last but not least a DEll inspiron with a touch screen and it runs ubuntu 11.04 fine but idk if it will survive the upgrade without a fresh install....

---

### Post by EgoGratis on 2011-07-28
I can't say for sure but upgrading should not be a problem. If u have some "closed source" drivers installed try removing them before upgrading the system and if u have lot of software from PPA sources you should enable PPA sources after upgrading and update software from PPA sources too. PPA sources are disabled before upgrading. And of course install closed source driver back.

BUT don't upgrade before Ubuntu 11.10 is officially out for now it is just for testing purposes! Try to upgrade the system that is less important to you first and see if it goes well. Then move up to the more important one!

---

### Post by fjgaude on 2011-07-28
No matter what we do let us make sure we have one or more backups of all important data, photos, and the like.

---

### Post by cariboo on 2011-07-28
I'd suggest you create a separate home partition, that way you won't lose your important data, but doing daily backups is always a good idea if your data is important to you.

---

### Post by cheesekiller on 2011-07-29
well most of my stuff like pictures music documents are backed up on ubuntu one. however for the other stuff (games) I guess I'll use like an external 1TB and back up my home folder beforehand. I think after 12.04 hits I'm going to stick with the LTS and change every LTS (or atleast try to... the new features are always too tempting)

---

### Post by PhantmKllr on 2011-07-29
> **cheesekiller said:**
> well most of my stuff like pictures music documents are backed up on ubuntu one. however for the other stuff (games) I guess I'll use like an external 1TB and back up my home folder beforehand. I think after 12.04 hits I'm going to stick with the LTS and change every LTS (or atleast try to... the new features are always too tempting)
I think that you should stick to the stable releases if you're worried about breakage, because you'd have to put up with it frequently.

I too, was tempted to go LTS only, but I never really had problems with upgrading my setup, so, yeah.

---

### Post by EgoGratis on 2011-07-30
It would just be to hard to stay on LTS on home computer. ;)

---

### Post by 3rdalbum on 2011-07-30
Things will usually "just work", it's just a matter of what other packages and PPAs you have that might cause the upgrade process to get bollocks'ed.

Really, we're at alpha 2 stage. It's difficult to say exactly what Ubuntu 11.10 will be like, because none of the big changes have landed yet.

---

### Post by lucazade on 2011-07-30
> **3rdalbum said:**
> 
Really, we're at alpha 2 stage. It's difficult to say exactly what Ubuntu 11.10 will be like, because none of the big changes have landed yet.

Kernel 3.0.x, Gnome3, Unity3D/2D ported to gtk3, new indicator-applets, lightdm, gtk3 unico engine... are all big changes.
What else should land?

---

### Post by walt.smith1960 on 2011-07-30
I would not recommend 11.10 yet for anything that matters.  It is much better than it was but is still a ways from "ready for prime time".  Remember, it's not even to Beta yet.  Starting to look pretty promising though -- Unity 2D & 3D, Gnome, Gnome classic and I think Gnome classic -no effects.

Edit:  Upon updating, Gnome Classic and Gnome Classic - no effects is now missing on my install.  I hope this is temporary or an anomaly on my system.

---

### Post by tghe-retford on 2011-07-30
> **cariboo907 said:**
> I'd suggest you create a separate home partition...
Even that may not be enough. I have known of a bug which happened to me during testing a couple or so years ago which wiped unrelated data on a different partition. Bugs can relate from mild annoyance (often) to hardware failure (extremely rare).

With development software, you takes your chances. You'll be fine on the whole as long as you are aware of what you are doing (particularly so when upgrading), keep an eye on what's happening and take precautions.

---

