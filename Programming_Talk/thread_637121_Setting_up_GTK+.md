---
title: "Setting up GTK+"
date: 2007-12-10
forum: Programming Talk
---

### Post by tunelabguy on 2007-12-10
What is the minimum I need to do in order to develop C/C++ programs using GTK+ ?

I am new to Linux, having just installed ubuntu 7.10 on a dual-boot machine with WinXP; but I am experienced in Win32 programming with Watcom using DOS command-line tools.  My ubuntu is not on the internet, but my WinXP is.  The Syn. Package Manager seems to be slanted toward on-line use, so I would prefer installation methods that rely on command-line tools and files I have previously download using WinXP.  So far I have downloaded:

  gtk+-2.13.3.tar.gz    and
  gtk+-2.13.3.tar.bz2

I am not sure what to do with them.  I would rather not compile GTK+ from source if I can avoid it.

For the moment I am content to use GEDIT and command-line tooks to develop GTK+.  Later on I may switch over to an IDE, but right now I want to learn the basics.  I have succeeded in compiling and running a non-graphic "hello world" program, so I know gcc is working.

What should I do next to get GTK+ development tools installed, keeping in mind the fact that I cannot download directly from the Internet to ubuntu, but I must go through a WinXP download first.

Robert Scott
Ypsilanti, Michigan

---

### Post by rufius on 2007-12-10
You're better of getting an internet connection and install libgtk2.0-dev package than building from source. At least on Ubuntu thats going to save you a lot of trouble. 

I think there's several dependencies so just downloading that package probably wouldn't be feasible. 

Why not fix your internet connection first?

---

### Post by MicahCarrick on 2007-12-10
Yeah, you're really going to want to get your internet connection because you'll constantly be needing more packages and libraries as you begin to do more things (libxml, libglade, etc.)

But, the GTK+ page will tell you what's needed, but it's probably best to use the Ubuntu packages. If you must do this by manually downloading, start here:[http://packages.ubuntu.com/gutsy/libdevel/libgtk2.0-dev]("http://packages.ubuntu.com/gutsy/libdevel/libgtk2.0-dev") (make sure it's the right distribution such as feisty or gutsy and the right architecture such as i386). It lists all it's dependencies which you will also need to download (and those could in turn have dependencies).

---

### Post by tunelabguy on 2007-12-10
OK, I got ndiswrapper working and I now have the Internet on ubuntu.  In fact I'm making this posting using ubuntu.  So how do I make libgtk2.0-dev appear in Synaptic Package Manager so I can install it?  I see libgtk2.0-common, cil, bin, and 0.  But no -dev.  Does it have something to do with selecting repositories?

Robert Scott
Ypsilanti, Michigan

---

### Post by Hairy_Palms on 2007-12-10
you sure you dont just need to reload the sources in synaptic, there should be a reload button in the top left corner,

---

### Post by tunelabguy on 2007-12-10
> **Hairy_Palms said:**
> you sure you dont just need to reload the sources in synaptic, there should be a reload button in the top left corner,

Yup.  I have hit the reload button and a box briefly appeared saying that something was being updated.  Then I selected "Sections" and "All".  libgtk2.0-dev is still not in the list of packages on the right.  Neither is it present when I select "Status" and "Not Installed".

Robert Scott
Ypsilanti, Michigan

---

### Post by tunelabguy on 2007-12-11
Success!  I found that all four of the internet source (main, restricted, universe, and multivers) were unchecked in synaptic.  When I checked them and hit Reload, libgtk2.0-dev was there and I have installed it.  Thanks for the advice.

Robert Scott
Ypsilanti, Michigan

---

