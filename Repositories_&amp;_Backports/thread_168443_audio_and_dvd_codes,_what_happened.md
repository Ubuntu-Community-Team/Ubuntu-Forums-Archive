---
title: "audio and dvd codes, what happened"
date: 2006-04-30
forum: Repositories &amp; Backports
---

### Post by dnae11 on 2006-04-30
surpriseingly i found the codes for audio and dvd play in the universe or restricted repositories.  They werent there before and it looks like they are not there now.  What happened?  I thought I was set, haha.  Could use totem-xine to listen to realplayer stream as well as watch dvd movies.  And then suddenly no longer.  Thats a major thing, it seems.  Is that the way it is or is it just me?  What I am talking about is w32codecs and libdvdcss.  Whats happened about this?

---

### Post by TitusDalwards on 2006-04-30
The line to add to your /etc/apt/sources.list file would be:
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

After you have done this, do
$sudo apt-get update

Now you can install the following using the PLF repository:
* w32codecs: A package of codecs needed to play multiple formats, notably DivX. (disponible. Maintainer: MirSPCM)
* RealPlayer: Stream player (disponible. Maintainer: keyes)
* libdvdcss2: The library needed to play back encrypted DVDs.(Disponible. Maintainer: MirSPCM)
* Xdtv: [http://xawdecode.fr.st](http://xawdecode.fr.st) - Tv viewer and recorder, the dependancies, and plugins like plug-m (Maintainer: Stéph)

---

