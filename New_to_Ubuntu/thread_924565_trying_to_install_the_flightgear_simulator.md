---
title: "trying to install the flightgear simulator"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by fignig on 2008-09-19
so i'm having a bit of a problem. b/c in the .deb package it says that:

Error: Dependency is not satisfiable: libopenal1

does this mean i don't have it? or i need to install it?

---

### Post by fignig on 2008-09-19
> **fignig said:**
> so i'm having a bit of a problem. b/c in the .deb package it says that:

Error: Dependency is not satisfiable: libopenal1

does this mean i don't have it? or i need to install it?

and i if i do need it. where do i put it exactly?

---

### Post by nickgaydos on 2008-09-19
Search it in Synaptic

---

### Post by fignig on 2008-09-19
> **nickgaydos said:**
> Search it in Synaptic

don't u think i would've already done that. it's not in there.

---

### Post by nickgaydos on 2008-09-19
> **fignig said:**
> don't u think i would've already done that. it's not in there.

Just tryin' to help...

---

### Post by henryjm206 on 2008-09-19
try reinstalling it

[http://packages.ubuntu.com/intrepid/libdevel/libopenal1-dbg](http://packages.ubuntu.com/intrepid/libdevel/libopenal1-dbg)

henry
good luck
I had that problem before

---

### Post by fignig on 2008-09-19
> **henryjm206 said:**
> try reinstalling it

[http://packages.ubuntu.com/intrepid/libdevel/libopenal1-dbg](http://packages.ubuntu.com/intrepid/libdevel/libopenal1-dbg)

henry
good luck
I had that problem before

i d/l'd the .deb package and tried installing the package from that site and it keeps giving me the same error message. it's kinda weird when i'm trying to install it.

---

### Post by fignig on 2008-09-19
someone needs to come up w/ better install directions for these games. b/c i want:

racer
flight sim
and sauerbraten

but all of them seem to be messing up during the "directions" given. seems like none of them work, but i want them to. can anyone help me out on these 3 or games that will actually install?

---

### Post by henryjm206 on 2008-09-19
hm 
Im not sure then 
sorry :(
henry

---

### Post by nkri on 2008-09-19
It should be in Synaptic.  Do you have all repositories enabled?  Make sure that in Settings>Repositories, universe and multiverse repositories are checked.  Also, try searching "flightgear" (without the quotes) instead of "flightgear simulator."

Good luck!
-nkri

PS: you probably didn't mean to come across like that, but just so's you know: it is clearly outlined in the forum rules that you shouldn't assume that people know something if you don't say it.  Not everything is obvious to everyone, and you should always explain things like it isn't:)

---

### Post by henryjm206 on 2008-09-19
try the ubuntu gaming area it helped me [http://gaming.gwos.org/doku.php](http://gaming.gwos.org/doku.php)
henry

---

### Post by henryjm206 on 2008-09-20
also how did you install it?
try apt-get
henry

---

### Post by egalvan on 2008-09-20
> **nkri said:**
> It should be in Synaptic.  Do you have all repositories enabled?  Make sure that in Settings>Repositories, universe and multiverse repositories are checked.  Also, try searching "flightgear" (without the quotes) instead of "flightgear simulator."



Just checked, "flightgear" comes up in Synaptic.

Quote from the info window...

[B]Flight Gear Flight Simulator
Flight Gear is a free and highly sophisticated flight simulator.

This package contains the runtime binaries.[/B]

---

### Post by egalvan on 2008-09-20
> **fignig said:**
> someone needs to come up w/ better install directions for these games. b/c i want:

racer
flight sim
and sauerbraten

but all of them seem to be messing up during the "directions" given. seems like none of them work, but i want them to. can anyone help me out on these 3 or games that will actually install?

From Synaptic information....

[B]3D first-person game engine
Sauerbraten is a networked fast-paced 3D first person first-person shooter
game. It supports rather modern graphic effects and a some nice graphic
details.

The game client also works as the map editor. It is even possible to create
and/or edit a map together with other people over a network connection.

Sauerbraten might be considered unsuitable for children.

This package installs the game client and map editor.[/B]

and

[B]Futuristic racing game
Xracer is a Wipeout clone, distributed under the GPL. It should be able to use
any OpenGL 1.1 compliant library. A 3D accelerator card is required.

This is the game data and binary.

If you want to build new tracks or other game data, you may also want to
install the xracer-tools package.
[/B]

---

