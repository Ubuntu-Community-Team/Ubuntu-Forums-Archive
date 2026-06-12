---
title: "Synaptic or Add/Remove"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by kneewax on 2008-04-30
Simple Question that only a newbie would ask!  :-) 

What actually is the difference between the Synaptic Package Manager and the Add/Remove Applications manager?

I notice that for example, I can install Wine from either....

Is there specific tasks it is better to use one or the other for?

Ta

Kneewax

---

### Post by rubicon on 2008-04-30
Add/Remove *Applications* adds or removes *applications* ;)

Synaptic manages every single package. Anyways, Add/Remove is just easy frontend for Synaptic.

---

### Post by Paqman on 2008-04-30
> **rubicon said:**
> Anyways, Add/Remove is just easy frontend for Synaptic.

Sort of, yes.

The actual package management system is Apt (Advanced Packaging Tool). From the command line you can use Apt through the commands "aptitude" or "apt-get". Both Synaptic and Add/Remove are GUI front-ends for Apt.

So Synaptic, Add/Remove, apt-get, apturl, aptitude, etc are all really the same thing. It's just different ways of using the same system.

---

### Post by kneewax on 2008-04-30
> **Paqman said:**
> Sort of, yes.
[snip]

So Synaptic, Add/Remove, apt-get, apturl, aptitude, etc are all really the same thing. It's just different ways of using the same system.

So all the same apps appear in both?  I have assumed, perhaps wrongly, that using the 'update' function of the Synaptic Package Manager, will update the list of apps in the repos, where as Add/Remove, will just install from the most recent lists.  

Is there anything that one does that the other doesn't?

---

### Post by Paqman on 2008-04-30
> **kneewax said:**
> 
Is there anything that one does that the other doesn't?

Synaptic can do tons that Add/Remove can't. For example, you can force the system to use a particular version of a package and you can create custom filters to sort through your installed packages. Basically Add/Remove was designed as more streamlined way of doing  basic (un)install tasks, whereas Synaptic was designed to allow you to complete control over your system.

---

### Post by kneewax on 2008-04-30
Brilliant, that helps a lot - thanks! :)

---

### Post by vishzilla on 2008-04-30
Synaptic you have more control over the programs you want to install or remove. Add/Remove is a simpler form and caters towards the newer Linux users

---

### Post by end-user on 2008-04-30
These are all right, but I feel there is a sort of tendency to undersell Add/Remove. One way I've heard Add/Remove described more specifically, is that Add/Remove includes only packages that include a...now I'm going to forget the filetype name... well anyway it is only packages that include an Icon and Launcher that will immediately go into your Applications Menu.

Oftentimes in synaptic, especially when just starting out, you will download a program and then have no indication of how to actually start the program. 

I love Add/Remove, it is an ideal way to browse applications,

---

### Post by sayakb on 2008-04-30
I don't know, might be my personal experience. I have a very slow internet (<256kbps) at my college. I find that apt-get downloads the package faster than synaptic.

---

### Post by sujoy on 2008-04-30
with add remove you can only install applications, with synaptic you can install library files only or developments packages only, if you want. yes offcourse synaptic also allows you to install applications its way more featured than add/remove

---

