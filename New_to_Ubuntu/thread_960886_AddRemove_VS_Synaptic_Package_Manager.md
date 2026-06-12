---
title: "Add/Remove VS Synaptic Package Manager"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by ericmtnbkr on 2008-10-27
Hello group.

I'm new to Ubuntu, but love it so far.  Can someone explain the difference between the Add/Remove command from the Applications menu and Synaptic Package Manager from the System>Administration menu?

Also, how do I tell what programs are actually installed and what aren't but are available in the add/remove and synaptic manager.

Thanks gang!

Eric :KS

---

### Post by chrisamiller on 2008-10-27
This is roughly the difference, as I understand it:

- Add/remove lists applications that you can install/uninstall
- synaptic lists all packages.  

Often installing a program requires functionality contained in several libraries, besides main program's package.  These are 'dependencies'.  Add/remove takes care of installing those behind the scenes.  Synaptic does too, but lets you get down and dirty with the details.

---

### Post by sayems on 2008-10-27
The Thread already exit
[http://ubuntuforums.org/showthread.php?t=433516](http://ubuntuforums.org/showthread.php?t=433516)

---

### Post by kansasnoob on 2008-10-27
> **ericmtnbkr said:**
> Hello group.

I'm new to Ubuntu, but love it so far.  Can someone explain the difference between the Add/Remove command from the Applications menu and Synaptic Package Manager from the System>Administration menu?

Also, how do I tell what programs are actually installed and what aren't but are available in the add/remove and synaptic manager.

Thanks gang!

Eric :KS

I NEVER use Add/Remove! You can't see what dependencies you're changing that way!

Use synaptic! When you're adding and removing things use a notepad to keep track of what dependencies are changing. Then when something breaks you'll know what's changed!

After a while you'll know just what the package names and dependencies are and you'll be more comfortable using apt!

---

### Post by Keen101 on 2008-10-27
Basically the ADD/REMOVE is a simple GUI for installing/removing programs. In short it does not list all of them.

Synaptic is a much more powerful GUI, and in my opinion works better.

There is also the command line install

> sudo apt-get install "package"

---

### Post by d_skillz on 2008-10-27
> **kansasnoob said:**
> I NEVER use Add/Remove! You can't see what dependencies you're changing that way!

Use synaptic! When you're adding and removing things use a notepad to keep track of what dependencies are changing. Then when something breaks you'll know what's changed!

After a while you'll know just what the package names and dependencies are and you'll be more comfortable using apt!

You truly wont realise just how useful Synaptic is at identifying deendencies and removing programs until you have tried other distros OpenSuse and redhat will make you wonder how they wade through that stuff. Just keep a notepad handy and watch the dependencies then you will really learn how the application correlate.

---

### Post by SunnyRabbiera on 2008-10-27
Add/remove is a very basic installer, its good to get one started though its far more primitive then synpatic.
In the future though I wish there would be something like Mandriva's installer as a in between of synatpic and add/ remove.
Something with icons and screenshots to help beginners but advanced enough for long time users.

---

### Post by Paqman on 2008-10-27
Personally i'm finding myself using Add/Remove more and more often instead of Synaptic. It's quicker. Although I do like the fast search feature in the new version of Synaptic that's in Intrepid.

---

### Post by JawsThemeSwimming428 on 2008-10-27
Is there anything wrong with using Add/Remove vs Synaptic?

---

### Post by SunnyRabbiera on 2008-10-27
> **JawsThemeSwimming428 said:**
> Is there anything wrong with using Add/Remove vs Synaptic?

Well the biggest issue with add/remove is that it only lists a certain amount of packages and many newcommers run for the hills if its not in the list thinking they have to compile to gwt what they need.
I really feel that add/remove needs to display more applications

---

### Post by ericmtnbkr on 2008-10-29
Thanks everyone.  And thanks sayems for pointing out a past thread to help shed more light on this topic.

:)

Eric

---

