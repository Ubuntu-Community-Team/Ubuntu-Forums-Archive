---
title: "three Mythbuntu questions"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by GSZX1337 on 2008-06-06
I just installed Mythbuntu on my Media Center PC, and I have three questions (right now).

1. How do I play DVDs? When I tried to play Chronicles of Riddick, I get to the DVD menu, hit play and it just brings me back to the MythTV front end.

2. Do I really need a connection to the Internet to use Mythbuntu (besides downloading games and apps)?

3. Can I use Gnome in Mythbuntu?

---

### Post by kvizz on 2008-06-06
1) I guess you should install some necessary multimedia codecs to play your dvd. Don't know exactly which one but i think that google would help you
2) You don't need a connection to the internet to watch predownloaded movies or to listen music or whatever. Just to watch TV and surf Web, i guess.
3) you can use gnome in mythbuntu, but in that case you should install and configure some mythtv stuff manually. Checkout this [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by Cadmus on 2008-06-06
[QUOTE=kvizz;5127638]2) You don't need a connection to the internet to watch predownloaded movies or to listen music or whatever. Just to watch TV and surf Web, i guess.QUOTE]

Surely that depends on how you get your TV? I've just got a card for Digital Terrestrial and I can't see why I'd need a web connection to use that.

---

### Post by shad0w_walker on 2008-06-06
If you want TV listings then most people will need an internet connection (Unless you are lucky enough to get Over the air listings)

---

### Post by Cadmus on 2008-06-06
Ah, didn't think about listings. I'm pretty sure you get listings over the air on DVB-T, but I don't know what the OP's using.

---

### Post by shad0w_walker on 2008-06-06
I'd imagine any TV input he has won't have Over the air listings, the majority don't unless you are using freeview stuff, I have to get my listings from the radiotimes as I have Sky (Can't connect directly into the system sadly) so it's a needed thing.

At the OP.

1. The easiest way to deal with the codec issues (Which sounds like you're issue) is to install the package:

ubuntu-restricted-extras

That should give you all the codecs you need to play back videos, music and DVDs.

2. You don't need a net connection for Myth, just for updates, downloads and the like, but if you don't need to use it to get TV listings or don't care about patches (They are security patches and don't need to be worried about if it's not connected to anything)

3. You shouldn't have any problem with using Gnome in Mythbuntu, should just be as easy as installing the appropriate package (Should be easily found in synaptic with a search for gnome desktop) then just select Gnome as the session type before you login.

---

