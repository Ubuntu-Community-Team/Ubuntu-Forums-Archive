---
title: "packaging my game into .deb"
date: 2007-01-20
forum: Packaging and Compiling Programs
---

### Post by Sasa_Ivanovic on 2007-01-20
:guitar: 
I made a game in Java. What do i need to do in order to package it into .deb and show it to Ubuntu developers who shall decide will it be in the depository or not ?
Do i need to licence my game under something ( i don't know nothing about this )

---

### Post by K.Mandla on 2007-01-21
(Moved to Packaging forum.)

---

### Post by xtacocorex on 2007-01-21
I still haven't figured out packaging, but you do need figure out a license. 

Choosing a license depends on what you want the end users to be able to do with the code/program.  If you want to give the source out to anyone and let them freely modify it, you can use the GPL.

There are also the Creative Commons Licenses (multiple types that cover different things), BSD License, and the LGPL.

You can even make up your own if you want, as long as it's distributed with the code, so the end-user knows about it.

Here are some links:
[http://www.gnu.org/licenses/](http://www.gnu.org/licenses/)
[http://creativecommons.org/](http://creativecommons.org/)

---

### Post by simplyw00x on 2007-01-22
Packing is fairly simple, especially if you build with autoconf/automake. If not (and probably not, if you're using java) there's a beginners' HOWTO available from the Ubuntu help menu on the Desktop. PM me if you'd like further instruction or help.

In terms of submitting for inclusion, you'd probably (depending on license) want to aim for Universe, which means through REVU, though it can't hurt to test-run the package on Getdeb and so on first because REVU and the MOTU are quite pedantic.

---

### Post by Sasa_Ivanovic on 2007-01-23
this seems to be too complicated, i'm just gonna quit.
thanks for the info though...

---

