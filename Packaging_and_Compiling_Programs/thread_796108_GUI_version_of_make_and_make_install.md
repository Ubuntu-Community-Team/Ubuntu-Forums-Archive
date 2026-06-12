---
title: "GUI version of make and make install?"
date: 2008-05-16
forum: Packaging and Compiling Programs
---

### Post by diafygi on 2008-05-16
Hey all,

I am doing a presentation Ubuntu in a few weeks and need some help. In particular, I'm trying show that you don't have to use the command line anymore. One of the main things my friends cite when I ask them to try Ubuntu is that they are scared of the terminal. Yes, I know the terminal is extremely useful, and a cli is infinitely more flexible than a gui. But it's still scary for casual and new users.

So far, I've been able to find a gui for everything I want to demonstrate except "make" and "make install".

Is there a gui way to "make" and "make install"? Are there alternatives?

Thanks guys! I love these forums.

---

### Post by EXCiD3 on 2008-05-16
Not that I know of, but you can mention that Ubuntu has almost ALL the software they would need precompiled in a repository somewhere, it might not be in the official repositories but it is probably somewhere (getdeb.net for example). Most of the time you dont have to compile from source anymore. You could show how easy it is to compile stuff from source (pidgin for example) and that only a few commands are needed for this.

---

### Post by ad_267 on 2008-05-16
You could try creating your own. You could use a nautilus script and use zenity so if you're in a directory it you can just right click and select the make script, then zenity dialogs could guide the user through the process and report any problems.

---

### Post by diafygi on 2008-05-16
> **EXCiD3 said:**
> Not that I know of, but you can mention that Ubuntu has almost ALL the software they would need precompiled in a repository somewhere, it might not be in the official repositories but it is probably somewhere (getdeb.net for example). Most of the time you dont have to compile from source anymore. You could show how easy it is to compile stuff from source (pidgin for example) and that only a few commands are needed for this.

Right, the only reason I needed to compile anything was to get the latest eyecandy from compiz-fusion (aquarium2 is just too cool). However, you have to compile the plugins from source. Very easy, but no GUI method.

> **ad_267 said:**
> You could try creating your own. You could use a nautilus script and use zenity so if you're in a directory it you can just right click and select the make script, then zenity dialogs could guide the user through the process and report any problems.

I was afraid of that. I'm sure I can slap something together, but it won't be available on the repositories for the people I'm presenting to.

---

### Post by Joeb454 on 2008-05-16
Well you could always mention that for the average user, you would never need to use make and make install (personally I prefer checkinstall, though I'll leave that for another time ;)).

I hardly ever need to compile stuff from source, though I sometimes choose to :)

---

