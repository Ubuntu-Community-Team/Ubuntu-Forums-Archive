---
title: "Gparted shuts down Oneiric"
date: 2011-08-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-08-28
sudo gparted
then system shuts down.
There are about 10 lines of failure info that appear for a fraction of a second on the terminal screen then disappear as oneiric shuts down fast.

Is the info reported on the terminal screen saved anywhere?  I couldn't find it in any of the /var/log or /var/crash files that I looked at.

Thanks, Jerry

p.s.
This is daily build 27 august installed on hardware and apt-get updated & upgraded.

---

### Post by fjgaude on 2011-08-28
Works correctly here, x64, 3D, either from command line or from the Launcher.

I'm sure it has to do with GTK3 and gnome 3 not being fully implemented yet. Soon...Beta 1. <smile>

---

### Post by kansasnoob on 2011-08-28
I'm using Lubuntu but I'm curious why you'd launch gparted via terminal, and if you do why wouldn't you use "gk"?

By "gk" I mean gksu or gksudo - since gparted is the gui front-end to parted.

---

### Post by cariboo on 2011-08-28
If you start gparted from the dash, it automagically asks you to enter a password.

---

### Post by jerrylamos on 2011-08-28
Works O.K. now, installed today's daiy build.  Gparted didn't work from yesterday's.

Thanks, Jerry

---

### Post by jerrylamos on 2011-08-28
Tried install of: 

27 August daily build, Dash Gparted, password, shuts down immediately.

28 August daily buildm Dash Gparted, password, works.

I have them both installed on the same hard drive (along with Narwhal & Lynx) so I can switch back and forth verifying the failure and the success.

Solved...

Jerry

---

