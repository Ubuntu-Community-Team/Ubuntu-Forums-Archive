---
title: "What's the difference between Ubuntu and Gnome?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by surfsunadam on 2008-09-06
I was very impressed with my ubuntu installation. 
Not long ago I I read that the user interface - windows, workplaces, file manager etc are all attributed to Gnome

So I'm wondering, if you take away all those things, I don't know what's left. What does ubuntu actually do?

---

### Post by scragar on 2008-09-06
it's hard to explain, but I'll try my best.
at the bottom you have the kernel, this is the very core of linux, it's the operating system, but you can't do anything with it, the kernel itself doesn't even have a command line.
Then above that you have a command line(or 7), you could access these using ctrl+alt+F1-F6, with F7 being the the one your using right now with X running on it, and X is...
Above the command line is X, a layer acting to allow graphics
gnome is your login window, it's what let's you see your desktop, and a lot of the programs can be directly traced back to gnome or parts of it(the same could also be said about KDE, XFCE, or any other desktop enviroment).
On top of that you've got your programs, so you've got the file manager which gives you a desktop you can interact with, your browser which let's you surf the internet, the menu to let you run programs etc.
Ubuntu is a distribution, that means that it's a collection of all of the above stuff that has been tested to work well together, and packaged(with some just for ubuntu adjustments where required).

Hope this isn't too confusing, I did try to get it as simple as possible.

---

### Post by alienexplorers on 2008-09-06
Ubuntu is the OS for the system and gnome is the desktop enviroment.

---

### Post by crispy_420 on 2008-09-06
Ubuntu is the foundation, just like a house. Gnome is what is placed on top to add the visual enviroment. But, if you don't like gnome; you can move something else onto the same foundation.

---

### Post by iaculallad on 2008-09-06
Posters above this post gave you what Ubuntu and GNOME are. If you're interested in knowing more about the commonly used Desktop Environments, try reading this [Wiki]("http://en.wikipedia.org/wiki/Desktop_environment") page.

---

### Post by surfsunadam on 2008-09-06
Thanks guys, that made it a bit clearer to me. I'll check out that wiki
I'm learning new things every day, I didn't realise the command line is actually above the kernal.
So how much does the under the hood stuff - the 'linux kernal' differ between distributions? Does Gnome differ between distros?

---

### Post by scragar on 2008-09-06
The kernel is the same at it's core, but between distributions it undergoes a few changes for various reasons.

You can run a range of different command lines(and long ago people did), but now bash(the **b**ourne **a**gain **sh**ell) is so common that it's pretty much assumed to be the only one anyone will be using.

While gnome itself doesn't change much(if at all) between the different distributions some may not even use gnome, choosing something else in it's place, KDE is a very common choice(and in many ways offers more of a windowsy(I know I know, not a word, live with it) feel), while I like XFCE(built from gnome, but designed to be much lighter in terms of ram and CPU usage so it runs better on older hardware). There is a pretty large list of popular alternatives available on wikipedia, but KDE and GNOME are the 2 most common(by a fair distance), while the *box(fluxbox, blackbox and openbox), IceWM(which is pretty much at the extreme end of lightweight) or XFCE are normaly used on older computers(or laptops, although knopix developers and users will argue with me over that).

you can install KDE, any of the *box WMs or XFCE(I'm not sure if IceWM is there by default...) into ubuntu if you wished, nothing stops you(in fact, they are in the repositories, so it's made very easy), although I wouldn't recommend playing about with multiple managers without a good tutorial and possibly a geeky friend to help out should anything go wrong.

---

