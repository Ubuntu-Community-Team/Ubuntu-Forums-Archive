---
title: "Fluxbox vs Other?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by DMinard on 2008-05-15
i tried installing fluxbox but was greeted with an error
checking for strftime... yes
checking for iconv_open in -liconv... no
checking for libiconv_open in -liconv... no
checking for iconv declaration... no
checking for t_open in -lnsl... no
checking for socket in -lsocket... no
checking for X... no
configure: error: Fluxbox requires the X Window System libraries and headers.

so i ran this to try to fix it

$ sudo apt-get install xlibs-dev

and was met with yet another issue:
Package xlibs-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xlibs-dev has no installation candidate


geeze im stumped......im running Ubuntu 8 with the latest nvidia xserver drivers and gnome desk

does any1 have any possible solutions/other programs that provide roughly the same services??

---

### Post by eriqjaffe on 2008-05-15
Why not just install fluxbox from the repos?

```
sudo apt-get install fluxbox
```

If you're determined to build from source, try...

```
sudo apt-get build-dep fluxbox
```

...which should (in theory) install all the necessary dev libraries you'll need.

---

### Post by sunexplodes on 2008-05-15
Yeah, I'd agree, just grab it from the repos.. Fluxbox has a slow enough development cycle that there'll be VERY little difference between the repository version and the bleeding edge source.


With that said, in case you still want an answer to that question.. Openbox is very similar to Fluxbox, although it does not have a panel by default like Flux does. Otherwise it's similarly lightweight, and if you're familiar with one, you should have very little problem adapting to the other. 

With THAT said, I still think Fluxbox is the best lightweight WM out there.

---

### Post by tjwoosta on 2008-05-15
fluxbox is awesome!

i installed fluxbuntu the other day on my other machine that has  only 256mb ram (it made a huge difference in speed compared to xubuntu with xfce) and i still get the full functionality of ubuntu)

---

### Post by DMinard on 2008-05-15
alright so the obvious eluded me, i installed from the repo. ty for that

so no i killed my compiz and ran fluxbox but i have no type control panel or anything, is this the way it runs or did something eff up?

---

### Post by tjwoosta on 2008-05-15
control panel?   

if you right click the desktop do you get the menu?

---

### Post by DMinard on 2008-05-15
just the default menu ubuntu menu

---

### Post by tjwoosta on 2008-05-15
hmm, well i cant see what you have right now but it sounds to me like you have it working correctly.

have you ever used fluxbox before?

if not this link might help you 
[http://www.linux.org/lessons/short/fluxbox/index.html]("http://www.linux.org/lessons/short/fluxbox/index.html")

also there are alot of other helpful resources out there for fluxbox, just google it

---

### Post by TenPlus1 on 2008-05-15
I installed Openbox instead, with obconf and obmenu and it seems a lot easier to use than Fluxbox to me...  Especially the windowmaker plugins available, very nice :)

Also, select pypanel if you want a program panel at the bottom.

---

### Post by sunexplodes on 2008-05-15
All of fluxbox's configuration is done via text-based configuration files. They're very simple, but can be intimidating at first.  There are a couple good utilities you can get to help out a bit through a GUI, but there's no easy way to get it configured completely without editing those files by hand.

---

