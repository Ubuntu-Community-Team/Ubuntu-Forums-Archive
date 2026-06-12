---
title: "[c++] internet connections?"
date: 2007-02-18
forum: Programming Talk
---

### Post by the_nomad on 2007-02-18
is there any chance to make a program in c++ that works through internet? 
i wanna make a game that can be played on internet... i already have the ideea of the game but i have no ideea how to make it work on internet... i mean is there any header file that might allow me to use internet connections?

thanx in advance.

---

### Post by ansi on 2007-02-18
> **the_nomad said:**
> is there any chance to make a program in c++ that works through internet? 


Of course :). Use sockets. Examples and already cooked library you can find, for example, [[SIZE="3"]here[/SIZE]]("http://linuxgazette.net/issue74/tougher.html") and [[SIZE="3"]here[/SIZE]]("http://www.alhem.net/Sockets/").

---

### Post by lnostdal on 2007-02-18
i know you say C++ but if you want to learn how sockets work at a low level in linux you could google for a tutorial called "beej" (also check the man-pages of functions mentioned in that tutorial)

---

### Post by Choad on 2007-02-18
i did some socket programming when i used gamemaker (there was a wrapper for sockets called gmsock) and its not too difficult actually. you would expect "low level" to mean insanely hard and unfriendly, but its pretty decent actually.

altho that was winsock... so perhaps the win api made things easier for me?

---

### Post by lnostdal on 2007-02-18
[quote=choad]altho that was winsock... so perhaps the win api made things easier for me?[/quote]
..they have similarities actually. Yeah, at least the things winsock and Linux socket APIs have in common (bsd'ish stuff#1) isn't impossible or extremely hard to understand and use(#2).

But even if they where hard or do have some quirky parts it is in some cases useful to understand and be aware of the "direct" APIs -- so that's why I mentioned beej and the suggestion to see man-pages for details.

#1: [http://en.wikipedia.org/wiki/Berkeley_sockets](http://en.wikipedia.org/wiki/Berkeley_sockets)

#2: ..but of course build or use abstractions/libraries where you can as usual. :)

---

