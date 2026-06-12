---
title: "Any one here uses CNR from www.cnr.com?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by legolas_w on 2008-04-29
Hi
Thank you for reading my post
What is differences between CNR [www.cnr.com](www.cnr.com) and current ubuntu package manages and repositories?

which one is preferred and why?


Thanks

---

### Post by gn2 on 2008-04-29
Synaptic Package Manager and the official repositories is preferred.

CNR is basically a shop front originally created to sell software.

Avoid it like the plague.

---

### Post by Tux Aubrey on 2008-04-29
As a general rule, I think its way better to stick with your own distro's repositories whenever you can - use add/remove, synaptic or (from the command line) apt-get.  Synaptic is an amazingly powerful and useful utility once you learn to use it right.

If you need something that's not listed in synaptic, try [getdeb]("http://www.getdeb.net/") - at least those packages are built for Ubuntu.

Otherwise, search for debian (.deb) package via Google if there is a particular package you want.  You can always ask on these forums if anyone else has used that particular (non-standard) package.

There is a lot of controversy about CNR - and not just for the reason given by gn2.  There seem to be doubts about the methods it uses to get information about your setup (and what happens to that information later) - a bit like the concerns people have about Microsoft collecting info about your computer without telling you what they are doing and why.

---

### Post by compiledkernel on 2008-04-30
A few reasons not to use CNR

Reason #1
The fact that it uses SETUID. If you dont know what this is, no big deal, just be aware that its really considered very insecure and unsafe. 

Reason #2
Dodgy 64-bit. The 64bit client can cause issues, be aware of that. 

Reason #3
Some software listed on cnr.com is outdated , in many cases stuff like Flash, and even outdated server packages. 

Reason #4
Not Easily Searchable for obvious things. Type in Codecs and you get a bunch of things that have the word codec in it, to a beginner this can be very confusing and daunting. 

Reason #5
When you upgrade from Gutsy to Hardy CNR-client gets removed , so you have go through the whole process over again of installing it.

Reason #6 
Dependency generation and awareness. If you install something with CNR, you arent made fully aware of what dependencies your downloading or installing, this can lead to confusion. 

Reason #7 
Add/Remove (actually called gnome-app-install), Synaptic, and even aptitude (if you learn to use it right) utterly negate the need for the use of CNR.

Reason #8 
NOT supported here. You need support for it , cnr.com is your game.

---

### Post by dstorrez on 2008-09-01
I will second that motion...stay away from CNR.  I think the concept was a good idea but I think we should stick with ubuntu supported software. Let the linspire people use the CNR. It is designed for them. Just my opinion.

---

### Post by Oldsoldier2003 on 2008-09-01
CNR isn't endorsed or supported by the forums and this topic will likely degenerate into flaming. Thread closed since the OPs question has been sufficiently answered.

---

### Post by Bachstelze on 2008-09-01
Just a quick side-note:

> **compiledkernel said:**
> Reason #1
The fact that it uses SETUID. If you dont know what this is, no big deal, just be aware that its really considered very insecure and unsafe. 

To everyone: SETUID is not insecure in itself. It exists for a reason, and many very useful (and secure) things wouldn't work without it (sudo is a good example). So while it is true that CNR uses it in a horribly insecure way, don't go around running and shouting "Insecure!" whenever someone mentions it ;)

---

