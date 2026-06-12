---
title: "nm-applet broken"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Lolicon on 2008-04-22
Something happened to my nm-applet and I can't restore it, because it needs the internet. I tried wicd, but it told me I needed to get rid of two dependencies: something with network manager. So I tried, but it needs the internet to do it for some reason (tries to upgrade them)! So how do I restore my internet?

---

### Post by Lolicon on 2008-04-23
please help

---

### Post by Anicka on 2008-04-23
Check which packages you need and go to this webpage [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/) There you can download any package you need and see what dependencies they have. Put them on a USB-stick and transfer to your Ubuntu. Install them either by double-clicking or from the terminal.

Quite obvious is that the network-manager is essential for the network to function.

---

### Post by Lolicon on 2008-04-23
The problem is it told me I needed to upgrade them, but I used the upgraded ones.

---

### Post by Anicka on 2008-04-23
Sorry for my ignorance, but what is wicd, where did you get it from and how did you install it? If it is a deb-package, make sure it is for you version of Ubuntu. Second issue could be if you don't have all the repos in your source file.

---

### Post by taavikko on 2008-04-23
> **Anicka said:**
> 
Quite obvious is that the network-manager is essential for the network to function.
Actually network-manager isn't crucial to network to function.
It tries to keep connection, at all times.

You could use **ifup ifdown dhclient** commands to fire up connection.

---

### Post by Tom--d on 2008-04-23
Uninstall nm-applet from Synpatic Package Manager and re install it.

Then in termainal type:

```
nm-applet
``` 

That then should sort it.


> It tries to keep connection, at all times.

It does?? 
My wireless cuts out at around 3 to 5 hrs up time.
I do not run nm-applet as I don't need it (manual configuration). 

If I run nm-applet. Would this stop the cuttage?

---

### Post by Lolicon on 2008-04-23
The problem is that I cannot connect to the internet, therefore restoring it is problematic. Here is wicd
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Lolicon on 2008-05-07
help please

---

### Post by Lolicon on 2008-05-08
> **Lolicon said:**
> help please

b u m            p

---

### Post by glennric on 2008-05-08
Do you have a wireless or a wired network that you use to access the internet?

---

### Post by GrantsV on 2008-05-09
Hi there, you need to give a few more details.

Is nm-applet actually still installed (the network manager icon near clock)?

Is your problem is getting to the nm-applet then try this:
Open System > Preferences > Sessions and a few down on the list should be Network Manager.  Make sure a tick is in this box.

If the nm-applet is available but you just cant connect to your internet, please let us know more detail so we can help future.

All the best,
Colin

---

