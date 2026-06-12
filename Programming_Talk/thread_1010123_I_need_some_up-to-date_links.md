---
title: "I need some up-to-date links"
date: 2008-12-13
forum: Programming Talk
---

### Post by gjoellee on 2008-12-13
I am trying creating an Ubuntu based distro called Zippex Linux, but to reach my goals I have to learn a programming language. I have dicided that language would be Python, becuase it is simple.

I can't however find any up-to-date links learning me how to write python software. I wonder if I could get some links to different websites offering tutorials for learning Python.

---

### Post by mentallaxative on 2008-12-13
What sort of software are you looking to write, and what sites do you already know of that you feel are outdated?

---

### Post by drubin on 2008-12-13
> **gjoellee said:**
> I am trying creating an Ubuntu based distro called Zippex Linux, but to reach my goals I have to learn a programming language. I have dicided that language would be Python, becuase it is simple.

I can't however find any up-to-date links learning me how to write python software. I wonder if I could get some links to different websites offering tutorials for learning Python.

What makes you think the stickies are outdated?? 

Also you need to be specific as to what you would like to do with the OS. writing an os in python is not posible.

---

### Post by snova on 2008-12-13
Technically, I think you *could*...

If you want to learn Python, I suggest going to their home page ([www.python.org](www.python.org)) and reading the tutorial.

---

### Post by drubin on 2008-12-13
> **snova said:**
> Technically, I think you *could*...

How so? Python is not a compiled lang and needs an interpreter to run. That interpreter needs to run on an OS.

Similar reason that you could never write an OS in java.

---

### Post by snova on 2008-12-13
OS in Java? [http://en.wikipedia.org/wiki/JavaOS](http://en.wikipedia.org/wiki/JavaOS) -- Done. :)

The kernel, obviously, could not, and neither could libc and various other low-level libraries, but for the most part, you could write a large amount of an OS in any language. Not the entire thing, though.

---

### Post by drubin on 2008-12-13
> **snova said:**
> OS in Java? [http://en.wikipedia.org/wiki/JavaOS](http://en.wikipedia.org/wiki/JavaOS) -- Done. :)

The kernel, obviously, could not, and neither could libc and various other low-level libraries, but for the most part, you could write a large amount of an OS in any language. Not the entire thing, though.

Never seen that before.. :)

> All device drivers are written in Java and executed by the virtual machine.

That is scary, I take my previous statement back, If java can do it python defiantly can, Python is slighly more lowerlevel.

---

### Post by pmasiar on 2008-12-13
> **drubin said:**
> How so? Python is not a compiled lang and needs an interpreter to run. That interpreter needs to run on an OS.

Similar reason that you could never write an OS in java.

You would be advised to learn a little before issuing such strong statements. Because you are wrong on all counts. :twisted: 

The only fact you got right is that "interpreter needs to run on an OS" :-)

Python **can** be compiled, by Shed Skin, Psyco, and other tools - or transformed to Cython or RPython.

So if anyone cares, writing OS in [http://en.wikipedia.org/wiki/Cython](http://en.wikipedia.org/wiki/Cython) and compiling it to C is open for talented wunderkinds, as we have on this forum plenty :-)

And while Python is not suited for writing an OS, OLPC GUI [http://en.wikipedia.org/wiki/Sugar_(GUI](http://en.wikipedia.org/wiki/Sugar_(GUI)) is written in Python, and runs OK on such a slow CPU as XO has.

BTW, OP: see wiki in my sig :-)

---

### Post by drubin on 2008-12-13
> **pmasiar said:**
> You would be advised to learn a little before issuing such strong statements. Because you are wrong on all counts. :twisted: 

The only fact you got right is that "interpreter needs to run on an OS" :-)

Ye haven't worked that much with low level programming on an OS level. So this was my understanding... (clearly wrong)

woohoo I got something right. Match point :)

---

### Post by pp. on 2008-12-13
> **drubin said:**
> How so? Python is not a compiled lang and needs an interpreter to run. That interpreter needs to run on an OS.

Similar reason that you could never write an OS in java.

Since all languages use some kind of run-time support, that is just a matter of degree and not of kind. You could easily write a kernel in java and link the run-time environment with your program to produce a liveable if not lively kernel.

I don't know if it is worthwile. There might be reasons why it's not routinely done.

---

### Post by ankursethi on 2008-12-14
@OP
To create a distro, you must first understand how a Linux distro actually works. Here are some resources to help you learn just that (in order of increasing level of difficulty) :

1. ArchLinux ([http://www.archlinux.org](http://www.archlinux.org)) - start with a bare bones system and work your way up to a full featured desktop. The Arch wiki is very helpful and contains all the resources you need to get up and running with your Arch install. Just make sure you read the manpages for every tool and configuration file you come across.

2. Gentoo Linux ([http://gentoo.org](http://gentoo.org)) - compile a Linux distro from scratch. Gentoo provides nicely packaged software in the form of source code. Even though getting Gentoo to install is a little tough, their user guide (included on the install CD) provides friendly step-by-step instructions to help you compile your system. The Gentoo wiki contains loads of information, too.

3. Linux From Scratch ([http://linuxfromscratch.org](http://linuxfromscratch.org)) - build a Linux distro from scratch. When they say "scratch", they *mean* scratch. You will have no user friendly LiveCD by your side, and neither will you have dependency-resolving package managers. You will have to download and compile every single package yourself. Not for the weak of heart.

As for the programming language, go for Python. The tutorial at Python.org is the best and the most concise introduction to the language. I doubt you'll use much of Python initially, though, since you will mostly be adapting other people's packages to fit your distro.

---

### Post by gjoellee on 2008-12-14
> **mentallaxative said:**
> What sort of software are you looking to write, and what sites do you already know of that you feel are outdated?

there are websites with tutorials written for very old versions of Python. I have plans for this at the moment:

-A tool that allows you to use terminal commands an a GUI so you can, Ex: Edit GRUB menu or just update your system

-A new menu that works in GNOME 

-Make something not to different form this: [http://gnome-look.org/content/show.php/New+Distribution?content=92134](http://gnome-look.org/content/show.php/New+Distribution?content=92134) (not any GNOME-panel integration or dock)

at the moment that's it, I do not have any more ides at the moment

---

### Post by ankursethi on 2008-12-14
Why create a new distro for just adding 3 new features? Just learn Python and write the code for your new menu and tool. Then test it on a few other distros to make sure it portable and release it to the public. If your code is bug free, reliable and has enough people wanting it included in their distro of choice, you'll be famous :)

(It takes a while to get to that level of proficiency, though.)

---

### Post by nvteighen on 2008-12-14
> **gjoellee said:**
> there are websites with tutorials written for very old versions of Python. (...)
I doubt the official tutorial is outdated ;)

> -A tool that allows you to use terminal commands an a GUI so you can, Ex: Edit GRUB menu or just update your system

Interesting. There was someone here some time ago that wanted to something like that but had no idea what he wanted... and surely quitted.

> 
-A new menu that works in GNOME 


That's not distro-dependent, but GNOME. Either it is something you should be able to set from a config file or you should fiddle with GNOME's source code (in that case, you'd be just distributing a custom GNOME). Nothing to do with a distro

> 
-Make something not to different form this: [http://gnome-look.org/content/show.php/New+Distribution?content=92134](http://gnome-look.org/content/show.php/New+Distribution?content=92134) (not any GNOME-panel integration or dock)


Yuck... that may even require a new GUI toolkit... I really doubt GTK+ 2.0 can handle such refined stuff...

---

### Post by gjoellee on 2008-12-14
> **ankursethi said:**
> Why create a new distro for just adding 3 new features? Just learn Python and write the code for your new menu and tool. Then test it on a few other distros to make sure it portable and release it to the public. If your code is bug free, reliable and has enough people wanting it included in their distro of choice, you'll be famous :)

(It takes a while to get to that level of proficiency, though.)

I haven't said that I am just adding 3 new features "mr."...

---

### Post by gjoellee on 2008-12-14
You know, all your critics gave me and idea, I managed yesterday to install Arch Linux on my laptop (could not make it work on my desktop computer).

Here are some ideas for a new distro, give me some tips please, don't be shy:

-Feature GNOME desktop modified to be light (can not get the required functionality with Xfce)
-Keeping most Arch Linux features
-Configure the system to work as a live cd with working sound and that stuff
-Out-of-the-box
-Include some features I will write
-PcmanFM as window manager
-As user friendly as possible, still not designed for beginner
-Include a guide which learns a user how to use different tools (I am not sure if I will write it in HTML and CSS or if I will make it in python
-more...

do you think this will be something "new"?

---

### Post by mentallaxative on 2008-12-14
> **gjoellee said:**
> there are websites with tutorials written for very old versions of Python.

I have not seen a Python tutorial targeted at a version older than the 2.xx series. Anything 2.xx is still relevant--I have a manual and a reference book that was written for 2.4 and I still look at them. The Python documentation is fairly good at notifying you of deprecated features so you can avoid using anything that has been phased out.

---

