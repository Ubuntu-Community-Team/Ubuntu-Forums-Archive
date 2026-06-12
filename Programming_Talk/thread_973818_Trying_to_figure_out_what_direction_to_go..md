---
title: "Trying to figure out what direction to go."
date: 2008-11-07
forum: Programming Talk
---

### Post by Arukas on 2008-11-07
Right now, I'm know C++.  But most of my programing has been done in command line/terminal settings.  I've done Visual Basic.


So here's what I'm wanting to do.  I like to do two things.  I wanting to write applications like data processing.  (Non-games)  However, I also want to program games.  

I've been reading tutorials and learning about IDEs.  I would like to write an application with GUI interface instead of terminals.  

I've been doing a KDevelop tutorial and KDevelop is a multi language IDE.  Also, I use Ubuntu and have a gnome environment.  Is Kevelop mainly for KDE desktops?

Also, is C++ a viable language for games and applications?  I've been reading back up on C++ and it has changed.  I don't think I have any problem learning any other programing languages.

---

### Post by cl333r on 2008-11-07
C++ _is_ ok for games, especially if these are large ones. But also remember there's no perfect solution.

---

### Post by Ferrat on 2008-11-07
C++ is more than ok for games, specially if you build modular games with a standard, that way the more games you make the less work you have to put in to the next because you just throw in that module with the right class/classes and it works "out of the box", you don't have to change anything not to meantion porting will be easy, just make a new module for the new target hardware/software and so on. 

I know some other languages might be "easier" for some games etc. but C++ gives you a easy way to go from a small simple game and reuse the same code for your MEGA ULTRA MASTER MMORPG. 

But it also comes down to a matter of taste, I like C++ ^^ and I'm not a very big fan of any of the interpreter languages, sure I fully understand how useful they can be in many ways but I just don't like them, same as I don't like Pepsi, Coca Cola or any other soft-drink really, I'm ok with sparkling water but I prefer tap water to be honest. 
I'm not saying liking Pepsi for ex. is wrong, I, me! just don't like it as much as tap water, but I would be a fool if I was in the desert, had lots of pepsi but no tap water and still didn't drink Pepsi.

---

### Post by Arukas on 2008-11-07
There may not be a perfect direction to go.  But there are things that don't work well.  

Is KDevelop okay to use for making programs for Ubuntu?  

Also, one of the thing I would like to do is write games that you can play over the internet.  I haven't really done anything like that before.  

There's also one more thing.  There just so many programing languages, I don't know what most of them are for.

---

### Post by LaRoza on 2008-11-07
> **Arukas said:**
> 
There's also one more thing.  There just so many programing languages, I don't know what most of them are for.

Check out my site and wiki. It can be easy to be confused, but hopefully, my language selector will help.

---

### Post by Arukas on 2008-11-07
> **LaRoza said:**
> Check out my site and wiki. It can be easy to be confused, but hopefully, my language selector will help.

Which is your site?  Anything in particular?  Believe it or not, I've click on many link you posted, but not nessarly the correct one.


Edit:
Also, I find a few things that was "coming soon", so that wasn't helpful at the moment.

---

### Post by Arukas on 2008-11-07
Under programing for Ubuntu, Kdevelop is listed.  From what I read Kdevelop is for the KDE, but Ubuntu has gnome.  So does it do both?  I read a tutorial on it, and makes stuff for the KDE.

---

### Post by escapee on 2008-11-08
Just install KDevelop from Synaptic.  It is made for KDE, but runs perfectly fine under Gnome, synaptic will handle the dependencies for you.  Just download it and try it out.

---

### Post by nvteighen on 2008-11-08
> **Arukas said:**
> Right now, I'm know C++.  But most of my programing has been done in command line/terminal settings.  I've done Visual Basic.


So here's what I'm wanting to do.  I like to do two things.  I wanting to write applications like data processing.  (Non-games)  However, I also want to program games.  

I've been reading tutorials and learning about IDEs.  I would like to write an application with GUI interface instead of terminals.  

I've been doing a KDevelop tutorial and KDevelop is a multi language IDE.  Also, I use Ubuntu and have a gnome environment.  Is Kevelop mainly for KDE desktops?

Also, is C++ a viable language for games and applications?  I've been reading back up on C++ and it has changed.  I don't think I have any problem learning any other programing languages.
Just be aware of the following: IDEs **can** be a trap when you don't know what the IDE is automating what you once did manually. If you just want a place to design GUIs easily instead of coding them manually, use a GUI designer: Glade for GTK+ or Qt Designer for Qt. 

On GUI toolkits, Qt is native C++, so it may be the best option. GTK+ is written in (and meant for) C, but you have bindings for C++.

---

### Post by nvteighen on 2008-11-08
> **Ferrat said:**
> 
But it also comes down to a matter of taste, I like C++ ^^ and I'm not a very big fan of any of the interpreter languages, sure I fully understand how useful they can be in many ways but I just don't like them, same as I don't like Pepsi, Coca Cola or any other soft-drink really, I'm ok with sparkling water but I prefer tap water to be honest. 
I'm not saying liking Pepsi for ex. is wrong, I, me! just don't like it as much as tap water, but I would be a fool if I was in the desert, had lots of pepsi but no tap water and still didn't drink Pepsi.

I completely disagree in your taste ;)

But you have a point: taste is not necessarily bound to knowledge. IIRC, Kant has a whole theory on this...

---

### Post by pmasiar on 2008-11-08
> **Ferrat said:**
> but C++ gives you a easy way to go from a small simple game and reuse the same code for your MEGA ULTRA MASTER MMORPG.

Pure BS. Writing games in low-level language is harder. MMORPG is **huge** project: [http://sol.gfxile.net/mmorpg.html](http://sol.gfxile.net/mmorpg.html) so the **only** way to succeed is to use highest level language possible to get high productivity. C/C++ is for libraries, not apps.

> But it also comes down to a matter of taste, I like C++ ^^ and I'm not a very big fan of any of the interpreter languages, sure I fully understand how useful they can be in many ways but I just don't like them,

So you are not much concerned about **solving** the problem and building the app: you prefer to fiddle around and push bits back and forth. Fine, if that is what you prefer - but then don't mention MMORPG. ;-)

---

### Post by nvteighen on 2008-11-08
If I'm not illerate enough, I'm pretty sure that MEGA ULTRA MASTER MMORPGs use C++ (please, "C/C++" doesn't exist!) for the core and speed critical stuff and the rest is done in some higher level language, usually Tcl or Lua, IIRC.

Can someone confirm this?

---

### Post by LaRoza on 2008-11-08
> **nvteighen said:**
> If I'm not illerate enough, I'm pretty sure that MEGA ULTRA MASTER MMORPGs use C++ (please, "C/C++" doesn't exist!) for the core and speed critical stuff and the rest is done in some higher level language, usually Tcl or Lua, IIRC.

Can someone confirm this?

I see no product named "MEGA ULTRA MASTER MMORPGs", so I can't say ;)

And yes, the last I checked, they (MMORPG's) used a mix of languages, as you stated.

---

