---
title: "[SOLVED] can't change network settings"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by omkarwagh on 2008-11-04
well intrepid has gotten better in look and feel but for some reasons, upgrading from a previous version still doesn't work perfectly.

this time, i am completely unable to change my settings in any way that i know of.
the network settings manager gives me the following message:-
Updating connection failed: nm-ifupdown-connection.c.82 - connection update not supported (read-only)..

is there any way out except for a fresh install?

i must say though that ubuntu is improving. this is the only issue i have faced within two days of the upgrade...

---

### Post by pmsumner on 2008-11-04
Try this, worked for me...

In a terminal type:

> sudo cp /etc/network/interfaces /etc/network/interfaces.bak
gksudo gedit /etc/network/interfaces

Enter your password and in the file, comment out (put a # in front of) any lines which ARE NOT one of:
> 
auto lo
iface lo inet loopback
auto wlan0
auto ath0


Save the file, and either restart the PC or type:
> sudo /etc/init.d/NetworkManager restart

Try that and see if you can edit the networks in Network Manager.

---

### Post by plntbrt on 2008-11-04
I have the same problem but the solution proposed doesn't work. 
When I try to change my wired connection I get the same message. I upgraded form ubuntu 8.04 to 8.10. My wired connection was with a crossover connection to another computer.

:confused:

---

### Post by plntbrt on 2008-11-04
hi,
I rebooted with the changes suggested above and now it works,
thank you):P

---

### Post by omkarwagh on 2008-11-05
hey yeah same experience as plntbrt.
thanks a lot man.

---

