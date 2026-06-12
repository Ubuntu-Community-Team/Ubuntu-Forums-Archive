---
title: "Beginner to ubuntu, advanced questions"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by metroedged on 2014-01-29
I am looking to "Break down" a distro and extract the packages that are installed in that distro (based on tiny core linux), and install them on ubuntu 12.4.

Can anyone link me to some general guides on how to do this?

The only reason I ask is because:

*packages work 100% on this distro (packages are also on several other distros, including ones that aren't based on tiny core linux)

*Sources seem to have been removed from latest 12.4 repository

*I can easily just boot from USB, but I would rather have these packages installed on the desktop.

Edit: I have the image file (.iso) of the disto. Could I simply open the contents and find the packages in .deb form and simply open with software center/synaptic package manager for easy installation?

---

### Post by sudodus on 2014-01-29
I think what you ask is quite complicated. What you can do is

- install Tiny Core Linux into an internal drive instead of a USB drive

- identify the program packages (their names), and find the corresponding packages for Ubuntu, and install those, if they are not already installed.

- reinstall sources (do you mean source code or do you mean repositories with program packages)?

But the packages are tweaked and compiled for each distro (Tiny Core and Ubuntu) and cannot be expected to work if you just copy them from one distro to another one unless they are based on the same repositories (made to use the same packages).

---

