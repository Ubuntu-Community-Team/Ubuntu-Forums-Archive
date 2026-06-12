---
title: "How does it all fit together"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by harmingcola on 2008-08-28
Hi, I'm a noob, I'm a little familiar with Ubuntu at this stage, but I'm completely confused as to how the whole thing fits together. So here are my questions.

Where does the Linux kernel end and Ubuntu Start? If the kernel is the same [roughly] then where do all the variations come from.

What does Nautilis do? Where does Ubuntu stop and Gnome start? If Metacity and Compiz do the same thing, manage windows?, then what gnome do? 

So basically, what do Metacity, Compiz, Gnome, Nautilis all do? Coming from windows, this is all a little structurally confusing.

Ubuntu is an operating system, Is it just the standard Linux kernel and a collection of other pieces?

---

### Post by ffmpegfailure on 2008-08-28
Nautilus is a file browser

---

### Post by billgoldberg on 2008-08-28
**Where does the Linux kernel end and Ubuntu Start? If the kernel is the same [roughly] then where do all the variations come from.**

Ubuntu is everything you see/get, kernel included.

Kernels can be adjusted for distro's or for specific hardware.

**What does Nautilis do? Where does Ubuntu stop and Gnome start? If Metacity and Compiz do the same thing, manage windows?, then what gnome do? **

Nautilus, besides being the file manager does some other things, like drawing your wallpaper.

Gnome is an DE (desktop environment), that means it's the whole package (metacity, nautilus, gnome-panel, network-manager, most of the default installed packages on Ubuntu).

**So basically, what do Metacity, Compiz, Gnome, Nautilis all do? Coming from windows, this is all a little structurally confusing.**

You either use Metacity or Compiz as a window manager (there are a lot more, think fluxbox, openbox, ...).

Gnome is just a collection of packages. Nautilus is the file manager.

**Ubuntu is an operating system, Is it just the standard Linux kernel and a collection of other pieces?**

Ubuntu comes with a modified kernel, but other than that, yes.

Note that the "other pieces" are adjusted to perform better with Ubuntu.

--

It was confusing for me too when I started using Ubuntu.

--

To break it down.

You have the kernel that speaks with the hardware.

You have the X server that makes sure you can see graphical things on you pc.

Then you have either a DE or you can add stuff yourself.

The standard DE is gnome. 

Gnome comes with Metacity to manage the windows. It also includes things like a file manager (nautilus), the gnome-panel (the one on the top and bottom) and pretty much all other installed packages.

Ubuntu tweaks the kernel, gnome, ... and all of those things together is Ubuntu.

--

A quick note. Everything you got installed that comes with the DE, you can change.

There are other DE's like KDE or XFCE, Enlightenment. But if you read my post carefully you don't have to use a DE.

For instance you can install Fluxbox (window manager), use PCmanFM or Thunar as a file manager, use WICD to manage your internet connection, use Epiphany as a internet browser instead of Firefox, ...

---

### Post by mocoloco on 2008-08-28
Windows has all the same parts: boot loader, kernel, login manager, file manager, window manager, compositor, etc.  The difference is that a Linux-based OS is modular so you can swap out any of these components for a similar piece of software that does the same thing.  People and organizations do that to their liking, thus there are many different combinations or distros.
Windows only offers one of each of those components and won't allow you to change most of them (and won't support changing any of them). So with either system a user doesn't have to know or care about the different pieces, but in the [FOSS]("http://en.wikipedia.org/wiki/Free_and_open_source_software") world you can more easily see/change/improve each part so they're more talked about.

Sometimes there's confusion over the term Linux, since people say it meaning
1) A kernel that many operating systems use
2) Any OS that uses this kernel  (unfortunately the most widespread usage)

I prefer to say "Linux-based", which eliminates this confusion.

---

### Post by lovinglinux on 2008-08-28
I'm a Linux newbie too and I agree that all this modularity is overwhelming for a Windows user. Nevertheless, once you understand each piece of the puzzle you will realize how good it is.

Another thing that is confusing for me is that on Windows we usually download and install a software for a specific use that is completely different from others that perform the same functions. Linux in the other hand explore more the backend/frontend modularity approach. This not only means that you can run an applet without a GUI, but that there are several GUI applications that use the same backend or that there is different versions of the same GUI applications that use different backends (Please someone correct me if I'm talking BS here). This is the case of Movie Player which versions for totem backend or xine backend. As a Windows user I first thought that totem and Movie players were completely different standalone applications. 

Another thing that I just realized recently is that applications for KDE works fine, but sometimes they don't blend with your system theme. I guess if we want a perfect integrated environment, including the visual part, we should stick with gnome applications.

BTW, does someone knows a tutorial or web site with a flow chart connecting things like Kernel, X Window, GNOME, Metacity and so on? billgoldberg post was very helpful, but I would like to understand this a little bit further (without too much technical explanations).

---

