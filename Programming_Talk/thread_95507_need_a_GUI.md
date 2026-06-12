---
title: "need a GUI"
date: 2005-11-26
forum: Programming Talk
---

### Post by Specialsauce on 2005-11-26
is there any frontend for G++ or something that will add a gui, one thats available through apt-get? i would like to be able to compile C++ stuff without having to go into the command line. it would just be alot nicer to use a graphical thing rather than the terminal. can anyone recommend anything

---

### Post by David Marrs on 2005-11-28
I'd be surprised if a stand-alone interface exists, although I've seen weirder things in the open-source world. Most IDEs have interfaces to the make utilities built in, which makes the most sense for a graphical interface. Ajunta is probably the most popular example for gnome, but even text editors like vim and emacs do it.

---

### Post by otake-tux on 2005-11-28
[http://www.bloodshed.net/download.html](http://www.bloodshed.net/download.html)

thats just what you want.  it compiles with the click of a button that says "compile".

though I dont really get why you want this feature.  whats so dificult about typing "g++ filename.cpp -o filename"?

---

### Post by thumper on 2005-11-28
or even a two line makefile and
```
make
```

---

### Post by Drakx on 2005-11-28
Just a quick question

Whats the best x-platform C gui tool kit must be x-platform as i intend to develop in windows as well also an easy to use and install gui toolkit too please 

thanks

---

### Post by Biased turkey on 2005-11-28
[QUOTE=Specialsauce]is there any frontend for G++ or something that will add a gui, one thats available through apt-get? i would like to be able to compile C++ stuff without having to go into the command line. it would just be alot nicer to use a graphical thing rather than the terminal. can anyone recommend anything[/QUOTE]

Anjuta is available via apt-get, so is Kdevelop ( KDE required )

---

