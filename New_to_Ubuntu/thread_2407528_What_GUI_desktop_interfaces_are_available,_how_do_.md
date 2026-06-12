---
title: "What GUI desktop interfaces are available, how do I get them and develop one?"
date: 2018-12-05
forum: New to Ubuntu
---

### Post by k9r4n on 2018-12-05
Hey guys!

Still slightly new to Ubuntu, but what GUI desktops are available for Ubuntu? Are there any tools or guides on creating your own GUI? What terminal requests or packages can I get to install these GUI's?

Thanks to anyone that helps!

k9r4n

---

### Post by freemedia2018 on 2018-12-05
That's a pretty broad request, but to get you started here is a broad listing of software available for Ubuntu: [https://packages.ubuntu.com/cosmic/](https://packages.ubuntu.com/cosmic/)

And that's important because it includes sections for GNOME, KDE and Xfce, which are all relevant to your question. 

To some degree, rather than targeting a single Desktop you can design around the underlying libraries-- GTK for GNOME and Qt for KDE. How you would develop for these depends on which desktop you choose, whether you want to contribute directly to the relevant projects (if you were developing for KDE they would probably have tips on the KDE website about which tools are best to use) but other than that it would depend on which language you are working in. 

Most users of KDE will still have the GTK libraries installed, so as a developer you can target a specific Desktop Environment though as long as the libraries are available, you don't have to. Leafpad is a GTK-based text editor and GTK is part of the GNOME project, but everyone with GTK installed can use Leafpad whether they are using a GNOME desktop or not.

As for installing, I can't help you there. If you know the name of a package you can say:

```
sudo apt-get install packagename
```

But other than that, I would just use aptitude-- which isn't always the installer I would recommend to first-time users. So I would suggest waiting around for a better answer to that part of the question.

---

### Post by k9r4n on 2018-12-05
Thanks, I'll check out the list, but I'm not sure how many packages will be supported for my device, as I'm using 14.04 Trusty Tahr because my device is quite old. 18.10 doesn't run well either, especially with dual-boot Windows 10. 

What languages could I write it in? Also, would it be better or easier to target the libraries? Is there any other way to target the GUI?

I've heard of Xfce, KDE, and GNOME, and I actually already know how to install those desktop GUI's, but I had a look at Pantheon from Elementary OS and was wondering what the package name for that would be and if there was a specific process I had to undergo in order to get it working on Ubuntu. 

Lastly, is aptitude the apt command shown above? Just curious...

Thanks for the help! Greatly appreciated!

k9r4n

---

### Post by freemedia2018 on 2018-12-05
> **k9r4n said:**
> Thanks, I'll check out the list, but I'm not sure how many packages will be supported for my device, as I'm using 14.04 Trusty Tahr because my device is quite old.

That's no problem, simply change the "cosmic" in the url to "trusty". I'd do it for you but it's good practice and you'll be more likely to remember it.

> What languages could I write it in? Also, would it be better or easier to target the libraries? Is there any other way to target the GUI?

The GUI situation is a bit complex-- you would be using either X11 or Wayland, but that's probably something you can ignore because you would instead target the Desktop or Library that runs on top of that-- GNOME (desktop) vs. GTK (library) or KDE (desktop) vs. Qt (library.)

Targeting the library is probably the way most everyone would do it, unless the goal is to develop as an official part of GNOME or KDE (if that's the idea, you would want to sign up on their mailing lists and ask how to get involved.)

> I've heard of Xfce, KDE, and GNOME, and I actually already know how to install those desktop GUI's, but I had a look at Pantheon from Elementary OS and was wondering what the package name for that would be and if there was a specific process I had to undergo in order to get it working on Ubuntu. 

I'm not sure about that one, I'd have to do some searching.

> Lastly, is aptitude the apt command shown above? Just curious...

The apt-get command is the apt-get command. It's part of the apt family of tools, which is the traditional package system used by Debian and Ubuntu. aptitude is a text-based tool that lets experienced users (or people who love that sort of thing) mess around with the installed packages and install new ones. Ubuntu has some friendlier tools, but I don't use them so I can't recommend them (hopefully someone will.)

If you are asking which language to get started with, I'd start by looking for a Python tutorial for GTK or Qt. These libraries are also available for C++ and other languages, depending on your experience developing.

---

### Post by TheFu on 2018-12-05
There are probably at least 50 different  GUI environments.  Most can be highly, highly, customized to appear completely different from anything you've seen anywhere else.  I don't know of any list.

Also, understanding how the different desktops work on Linux will be helpful.  The typical Ubuntu releases include both a Window Manager, WM, and a Desktop Environment, DE.  Nothing says you must have a DE. Nothing.

[https://en.wikipedia.org/wiki/Window_manager](https://en.wikipedia.org/wiki/Window_manager) - about Window Managers
[https://en.wikipedia.org/wiki/Desktop_environment](https://en.wikipedia.org/wiki/Desktop_environment) - about Desktop Environments

Ok, so here's a list off the top of my head. I didn't validate that all of them are in the package management systems.  Let's start with a list:[LIST]
[*]MWM
[*]TWM
[*]FVWM
[*]Fluxbox
[*]openbox
[*]blackbox
[*]icewm
[*]mutter
[*]i3
[*]CDE
[*]KDE
[*]Gnome2
[*]Gnome3
[*]LXDE
[*]LXQt
[*]XFCE4
[*]Mate
[*]Cinnamon
[/LIST]

That's off the top of my head.
[https://en.wikipedia.org/wiki/Comparison_of_X_window_managers](https://en.wikipedia.org/wiki/Comparison_of_X_window_managers)
If you drop to the bottom, [https://en.wikipedia.org/wiki/Desktop_environment#See_also](https://en.wikipedia.org/wiki/Desktop_environment#See_also) .. there are some broken out by main type.

A warning.  Many of these are forks of each other, so the configuration files might be the same and have conflicts. While installing 50 of these isn't an issue, running some under the same userid can cause conflicts which will break the login.  For this reason, whenever trying out new GUIs it is strongly recommended that you create/reset a test account between every login. Don't use your main or admin accounts for the system.

And I would backup my HOME directory before starting this, as a precaution.

If you want to make your own GUI, check out the "suckless" team.  [https://dwm.suckless.org/](https://dwm.suckless.org/)

Just for fun, start with fvwm-crystal to get a feel for what was possible 25 yrs ago. It really was amazing and much lighter.

---

### Post by k9r4n on 2018-12-05
Thanks for the tips!

k9r4n

---

### Post by oldrocker99 on 2018-12-05
My personal favorite desktop is MATE, which can look like Windows (Redmond), MacOS (Cupertino), and Unity (Mutiny). Or the good old GNOME 2.3 interface, which I started with in '08. I can't recommend it highly enough.

And, BTW, it's pronounced mah-TAY, after yerba mate, the caffeinated Argentinian herb. Pronouncing it as mayte refersto one's spouse, or a really good friend. Check Ubuntu MATE out.

[https://www.ubuntu-mate.org](https://www.ubuntu-mate.org)

---

### Post by mastablasta on 2018-12-06
> **TheFu said:**
> 

A warning.  Many of these are forks of each other, so the configuration files might be the same and have conflicts. While installing 50 of these isn't an issue, running some under the same userid can cause conflicts which will break the login.  For this reason, whenever trying out new GUIs it is strongly recommended that you create/reset a test account between every login. Don't use your main or admin accounts for the system.



for that reason i would do it in virtualbox (or similar). then take a snaphsot of the OS, install the DE or window manager, try it out and then restore the snapshot of the OS and then install another one on fresh.

---

