---
title: "Install Gnome to Kubuntu 14.04"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by stevecrt on 2014-06-06
Hi Guys

Can someone kindly post any commands, instructions or advise regardiing the installation of Gnome to Kubuntu 14.04.

Many Thanks

Best Wishes & Thanks in advance

Steve

---

### Post by Rob Sayer on 2014-06-06
Gnome is more than just one thing.  Do you mean gnome 3.10 or gnome-session-fallback?

I can't advise anyone as to which is better since I'm actually mostly a KDE user, but this netbook runs xubuntu.  You'll have to figure that out yourself.  Though I will say that gnome-session-fallback uses less hardware resources.

If you do search the topic you'll find a ton of stuff telling you how to add gnome 3.12, which isn't in the repos but requires you to add a 3rd party ppa.  And it hasn't been beta tested like the one in the repos (3.10).

Frankly, if you don't already know how to do this, don't install the bleeding edge version.  Stick with the one in the repos.  Bleeding edge software isn't as reliable.

Once you decide, you  can use the ubuntu software center or something else like synaptic or the terminal.  I use synaptic mostly ... it's definitely worth learning ... or the terminal.  Haven't fired up software center in ages myself.

ALWAYS update first before installing.  In terminal I'd do ...

sudo apt-get update && sudo apt-get dist-upgrade

... then either ...

sudo apt-get install gnome

(for gnome 3,10)

... or ...

sudo apt-get install gnome-session-fallback

... and reboot.  You'll be able to select a gnome or kde session when you log in.

Actually, while you can have multiple desktop environments on the same machine, be very careful about loading up DEs.  Common noob mistake.  I've done it.  Having both a gnome and KDE on the same machine should be OK because they're based upon different libraries.  But multiple GTK DE's can cause problems.

---

