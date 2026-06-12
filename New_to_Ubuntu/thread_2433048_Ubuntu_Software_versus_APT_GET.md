---
title: "Ubuntu Software versus APT GET"
date: 2019-12-12
forum: New to Ubuntu
---

### Post by yaminb on 2019-12-12
Maybe this is a silly question, but what exactly does the 'Ubuntu Software' contain and not contain?

I've been using Ubuntu for a short time now and in general, most of what I need to install, I can find in the 'Ubuntu Software' store.
Today, I just went to install mysql-server to play around with some stuff, and I couldn't find it in the store.

It was easy enough to install via the terminal: sudo apt install mysql-server

But then it got me wondering. Why was mysql-server not something I could install from the 'Ubuntu Software' store?
Is there a clear line? Like only 'client' applications are found in the store?

---

### Post by guiverc on 2019-12-12
Ubuntu gets it's software for the most parts from repositories ([https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu))  the lists of which are 'updated' with the command `apt-get update` (or `apt update`).  Some package tools (eg. synaptic, aptitude) provide the full list of packages available which you can then use `apt-get` (or `apt`) to install, or install via the front-end provided by `synaptic` or `aptitude` etc.

Software stores such as Ubuntu Software, Discover, Software Boutique & many many others provide lists of only some of these tools (some like Software Boutique provide what is supposed to represent the 'best of the best' but any such list will be subjective!). They also can provide packages that are available in other ways, eg. snaps, which `apt` tools will not see.

Most end-users find lots of choices confusing, distracting and a negative.. The GUI software tools (Ubuntu Software) try and deal with this by providing fewer options, particularly hiding technical packages end-users may not want.  Technical users tend not to use user tools, but package tools anyway, eg. instead of 'discover', they'll use 'muon package management', 'synaptic instead of 'Ubuntu Software' etc.

We have many tools available to us, most overlap (eg. apt-get & Ubuntu Software), but this is a good thing in my opinion anyway.

---

### Post by yaminb on 2019-12-13
I get you. It's an arbitrary list.

It was just confusing at first as I had assumed it contained all packages. What made it more confusing was there was a mysql (Server/client) SNAP in the store, but it got bad reviews. So I kept looking for the mysql 'real package' thinking it was being hidden by the SNAP or something like that.

I guess it's going to get confusing especially with SNAPs and flatpaks as those don't seem to be filtered at all (or I could be wrong, but that's how it looks to me).
Meanwhile useful DEBs are filtered.

Just FYI. I'm not complaining about it. I get the complexity of it all. I just didn't know the list of DEBs was arbitrary in the software store. I made the incorrect assumption it was a front end just like synaptic or something.

---

### Post by webaake on 2019-12-13
I'm an old user and when  I first got my eyes on Software Center I immediatley went back to Synaptic. So my recommendation is to install Synaptic and use that. And furthermore, I use aptitude instead of apt (apt-get) which is also installable. Sometimes User Friendliness is the opposite. :)

---

### Post by oldrocker99 on 2019-12-13
Synaptic shows **EVERY** available package, and categorizes them as to type. It was once a part of every Ubuntu release, but now you have to install it. There is a way to add a Quick Search box, which greatly enhances its use, which I highly recommend.
[https://askubuntu.com/questions/763857/how-to-get-quick-filter-back-in-synaptic-ubuntu-16-04-and-later](https://askubuntu.com/questions/763857/how-to-get-quick-filter-back-in-synaptic-ubuntu-16-04-and-later).

---

