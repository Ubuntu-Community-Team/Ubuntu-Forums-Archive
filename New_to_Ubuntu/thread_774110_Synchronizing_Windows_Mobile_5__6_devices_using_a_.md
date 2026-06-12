---
title: "Synchronizing Windows Mobile 5 / 6 devices using a USB cable"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2008-04-29
Hi there, I have Mandriva installed on another partition and just discovered [this]("http://wiki.mandriva.com/en/2008.1_Synchronization"): on the mandriva wiki. I was wondering if Ubuntu has a similar attempt to include us Windows mobile users to synch their devices with Ubuntu. I search synaptic for the packages mentioned in that wiki, but could not find any.

Is there a simple howto?

many thanks
S

---

### Post by JazonEsti on 2008-05-05
Bum ping this. I'd like to know too.

---

### Post by mlentink on 2008-05-05
I agree.

I wish I knew how to get hold of such a mandriva metapackage. With Alien, we should be able to transform it into a deb and give it a shot...

---

### Post by AdamWill on 2008-05-05
Just converting the package with alien wouldn't help you much, as the dependent packages don't all have the same name in Ubuntu, and Ubuntu's official repository is lacking several of the patches necessary to make everything work. All the metapackages really do is this:

Requires:       synce
Requires:       sync-engine
Requires:       odccm
Requires:       libopensync-plugin-synce
Suggests:       libopensync-plugin-file
Requires:       libopensync-plugin-kdepim
Requires:       kdepim-kitchensync

But there's a lot of other stuff required to make everything work correctly, which isn't really simply portable from Mandriva to Ubuntu.

For Ubuntu the best approach is to use a PPA which contains better packages than you'll find in the official repositories. [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) has decent, if somewhat concise, instructions.

If you have trouble (which, heh, is probably likely...), I'd suggest you visit #synce on Freenode IRC and ask for help there. Particularly jc2k should be able to help you. I'll try and help if I'm around (I'm AdamW), but I'm obviously a Mandriva guy not Ubuntu, so I can't help too much, I don't have direct experience of doing this stuff on Ubuntu myself. I did all the Mandriva work on this stuff, BTW.

---

### Post by mlentink on 2008-05-05
Thanks for the links, I'll dive in!

---

### Post by shuttleworthwannabe on 2008-05-06
thanks, AdamWill. I follow your post on the mandriva sites (saw the blog you posted about this a while back); that is what  made me try Mandriva. I must say it is beaut to look at. It is very easy on the eyes, even when switching from GNOME app to KDE in gnome and vice versa--the windows are consistent and fonts do not go hay-wire!

Well done!
I will visit the site you psoted and ask help there,
Oh, c'mon! Just been there: man, can some good sumaritan, but this whole setup in one convenient DEB file. I could do it, but I do not know how to. Please help us all.
S

---

