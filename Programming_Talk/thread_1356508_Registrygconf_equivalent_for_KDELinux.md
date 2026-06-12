---
title: "Registry/gconf equivalent for KDE/Linux"
date: 2009-12-16
forum: Programming Talk
---

### Post by WitchCraft on 2009-12-16
Is there a Registry/gconf equivalent for KDE?

I realize gconf is what's used by gnome, but does KDE have something like this ?

And more importantly, is there any general linux program, for example in core-utils, that replaces the registry ?

(I mean as a CENTRAL place for configuration/settings.)

---

### Post by akashiraffee on 2009-12-16
> **WitchCraft said:**
> 
And more importantly, is there any general linux program, for example in core-utils, that replaces the registry ?

(I mean as a CENTRAL place for configuration/settings.)
No.  Notice linux/GNU is very modularized -- the kernel is a completely separate beast from the OS.

AFAIK, the only "configuration" you can do with the kernel post-compile is by passing it command-line switches at start-up, which this can affect a range of things, such as whether to use atime in a traditional manner with the filesystem, etc, etc.

Then, the GNU programs which form the base of the OS (such as core-utils and the shell) are also separate from the window manager which is it's own layer on top of the Xorg server.  All these things have configuration, but they are not centralized, they remain discrete like the components themselves.  Gconf is just configuration for the DE and it is gnome specific.  I don't know if there is an exact KDE equivalent.  Gnome and KDE also both use the XDG standard for configuration, which you can investigate that.

---

### Post by Reiger on 2009-12-16
Apart from /etc/ and $HOME/.<app>... In KDE there is ksyscoca (**k**de-**sys**tem-**co**nfiguration-**ca**che).

But that is not necessarily the same as a central registry.

---

### Post by WitchCraft on 2009-12-16
> **Reiger said:**
> Apart from /etc/ and $HOME/.<app>... In KDE there is ksyscoca (**k**de-**sys**tem-**co**nfiguration-**ca**che).

But that is not necessarily the same as a central registry.

Good, ksyscoca and kregistry. 
And apart from /etc, there is /boot /dev  uname and some others..

---

