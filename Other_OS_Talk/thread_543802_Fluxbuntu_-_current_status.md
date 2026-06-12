---
title: "Fluxbuntu - current status"
date: 2007-09-05
forum: Other OS Talk
---

### Post by Kowalski_GT-R on 2007-09-05
Hi to all fellow forum dwellers, I am gathering info on Fluxbuntu, but since the official forums are in maintenance mode, I thought about asking on here...


did my homework and found this:
[http://ubuntuforums.org/showthread.php?t=301689&highlight=FLUXBUNTU]("http://ubuntuforums.org/showthread.php?t=301689&highlight=FLUXBUNTU") 


My old P166 has become a 233MMX, but still maxes out at 64Mbs of 72pin Simm, and Xubuntu alternate from the command line just doesn't cut it. DSL and Puppy are viable solutions, but I'd like the idea of sticking with Ubuntu( and the repositories.... and the wonderful support....etc)


How things are going for the diminutive and zippy -buntu distro? (also read: "when the official forum will be restored?")

ciao,

Andre

---

### Post by kerry_s on 2007-09-05
just do the ubuntu base install and build up from there.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

for your install line->
sudo apt-get install xorg gdm synaptic fluxbox
reboot(ctrl+alt+delete)
select fluxbox in the session menu and login
open synaptic and continue getting what you want/need.

---

### Post by Kowalski_GT-R on 2007-09-05
thanks kerry,

I knew about that possibility, but never dig into some research.

This makes Fluxbuntu redundant to say the least....

I keep reading Fluxbuntu isn't just Ubuntu with Fluxbox, what's frying in the pan then?

ciao,

Andre

---

### Post by kerry_s on 2007-09-05
fluxbuntu is okay, but for most people it's a bloated fluxbox install. much better to do it yourself with just what you need, that way you get only what you want. with your specs you really want to go custom, otherwise just go for those mini distro's, which won't be any faster than what you can do, plus it will have things you might not ever use just taking up space. you might also want to consider straight debian instead, as it is much better for old low resource hardware. ubuntu is slower, has a bigger base install and just really don't care about the old stuff.

---

### Post by Kowalski_GT-R on 2007-09-05
> **kerry_s said:**
> those mini distros  ---> won't be any faster than what you can do


now THIS is what I was looking for...

PC will serve dad's simple tasks, I want it to be as simple as it can be for him to operate it.

thanks much for your hints,

big ciao from Italy,


Andre

---

### Post by wolfen69 on 2007-09-05
it seems fluxbuntu is still in beta. can't wait to try it out.

---

### Post by RedSquirrel on 2007-09-07
> **Kowalski_GT-R said:**
> This makes Fluxbuntu redundant to say the least....

I keep reading Fluxbuntu isn't just Ubuntu with Fluxbox, what's frying in the pan then?

I think Fluxbuntu (when it's ready) will be a reasonable solution for people who don't feel like doing the custom install. It will have everything ready to go. Some people wouldn't know what lightweight applications they want to install on a minimal install. Fluxbuntu will take care of that.

Fluxbox is quite plain when one first installs it, so the advantage of something like Fluxbuntu is that it will look really nice "out of the box". I guess it also has a pleasant configuration by default (e.g., the menu, desktop icons, and so on). I think it will come with some nice artwork.

Like kerry_s, I'm very happy with my custom install and I don't think I need something like Fluxbuntu, but for some people it might be ideal.

Oh, and here's another link... ;)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Tux Aubrey on 2007-09-07
The current Fluxbuntu beta is based on Dapper and it seems the devs have had a hard time keeping up with the Ubuntu release schedule.  The next release is supposed to come out just after Gutsy, but I haven't seen a beta of that yet.

OTOH, the fluxbox version of Simply Mepis -[ antiX]("http://antix.mepis.org/index.php/Main_Page") - is powering along and pretty much keeping up with the Mepis release cycle (there is currently a beta for the next version which uses Debian, rather than Ubuntu, repos).  

Like fluxbuntu, antiX is a great ready-rolled version of a fluxbox distro (and it comes with ICEWM as a default alternative).

---

### Post by crzyakta on 2007-09-07
When reading about you guys doing a 'custom' installation, what exactly is that?

Like could Puppy Linux be installed in custom mode, with Fluxbox over as a GUI?

or Does PL have its own GUI?

thanks

---

### Post by dizee on 2007-09-08
A custom install is when you install basically a server edition of linux and then add the packages you want on top of that, so it's extremely lean and does what you need it too.

I'm not sure how easy it would be to do with puppy, but there is probably some way (there's a non-gui install of puppy if my memory is right but installing the additional packages is probably more of a challenge). Ubuntu makes it easy enough however.

---

