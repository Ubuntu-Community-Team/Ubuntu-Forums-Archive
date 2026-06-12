---
title: "How do I access powertweakd"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by jacatone on 2008-05-19
I use Synaptic to install "powertweakd" and "powertweak-gtk", but I don't seem to be able to launch it. Don't see it in the menu anywhere. Anyone know the answer? Thanks.

---

### Post by brujoand on 2008-05-19
alt + F2 --> type gpowertweak  

Dont know how they messed this up, but they did.

You can create your own menu item by clicking "add/remove" in applications.

---

### Post by jacatone on 2008-05-19
Said I needed to be root to access gpowertweak. When I tried launching it using a terminal, I got the following:

root@eMax:/home/jacatone# gpowertweak
Error creating socket to : /var/run/powertweakd Connection refused
2: tweak 11060305_00:00:00_FAST_BACK_2_BACK doesn't have a description.
Segmentation fault (core dumped)

Any idea what I do next? Thanks.

---

### Post by nowshining on 2008-05-20
try reporting a bug - seg fault. :) on launchpad.

---

