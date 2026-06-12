---
title: "[SOLVED] The CUPS server could not be contacted."
date: 2008-04-22
forum: New to Ubuntu
---

### Post by rlogan on 2008-04-22
Hi All

I have been having issues with setting up printers on this for a while and have decided one way or another to get this working.

When I try and run system-config printer, I get the error message pop up in a window saying "The CUPS server could not be contacted."

The problem is that whenever I try to run system-config-printer, gnome-cups-manager they seem to take an eternity to either do nothing or actually load after what seems 10 mins.

Likewise I have issues when attemopting to run my-default-printer and gnome-default printer.

I have tried so many suggestions or how to's to configure the various config files but with no luck to date. I was hoping that the upgrade to Hardy on the client machine would help resolve some issues but no such luck.

Help please..... I am really sick of not having this pc not linked to the network printer (attached to the other pc on the ethernet/ router and connected by usb).

Any help greatly appreciated

---

### Post by rlogan on 2008-04-24
Hi all

Got the problem fixed, it was a two stage problem.

First the router was blocking the host and mac id , as I did not have the pc names resolved under Ubuntu within the router... thus why no host not found.

Silly me also unplugged the ethernet cables a while back so it also changed the ip address on the router. What silly things to grind things to a halt. 

So all in all, router settings fixed and cups client conf file edited correctly and all working

Thanks all

---

