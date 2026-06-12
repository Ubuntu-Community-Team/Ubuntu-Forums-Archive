---
title: "What makes GNU/Linux distribution different apart from its desktop environment?"
date: 2010-03-14
forum: Recurring Discussions
---

### Post by superarthur on 2010-03-14
I've been reading a lot more GNU/Linux recently, but there is still one thing that is bothering me.
What makes GNU/Linux distribution different apart from its desktop environment?
I mean, if you run the terminal, doesn't it make them all the same? (Even the same as all UNIX-like system)
The only other thing I can see is the software that is installed with the system, but you can install any software you like after you install your OS.

---

### Post by pastalavista on 2010-03-14
GNU/Linux is the kernel and there are many of them with many different modules added for different hardware, functions and environments. Configuraation is the key and finding what works best for you is sometimes more difficult when you have too many options. Many experienced Linux users "roll their own" system. It is the most flexible OS because it is free to modify. That's why it comes in so many flavors.

---

### Post by superarthur on 2010-03-14
My point is: how is it different to the average end-user?

---

### Post by pastalavista on 2010-03-14
Different package management systems, boot loaders, etc. but really, I guess you have a point. It's all just ones and zeroes.

---

### Post by srs5694 on 2010-03-14
First, the term "GNU/Linux" is, contrary to what pastalavista suggested, generally applied to Linux distributions as a whole. It's "Linux" *alone* that some people insist on applying only to the kernel (although many others use "Linux" to refer either to the kernel or to a whole distribution). The reason is that many GNU tools go into a Linux (or GNU/Linux, if you like) distribution, but the Linux kernel itself is not a product of the Free Software Foundation's (FSF's) GNU Project.

Second, there are quite a few differences between distributions, which have varying levels of significance to different people. These include, but are by no means limited to:


[list]
[*]Different software versions -- Distribution A may ship with version 1.0 of package X, version 1.2 of package Y, and version 2.7 of package Z, whereas Distribution B may ship with versions 1.1, 1.3, and 2.5 of these packages, respectively. Such differences can affect reliability and overall system feel, although probably only to a limited extent.
[*]Software compilation options -- Distributions can differ in how software is compiled. Sometimes this affects execution speed (although usually only to a limited extent) or features (depending on whether certain compile-time options were enabled). Note that this applies to the kernel, too; one distribution might support a feature like a certain filesystem or hardware driver, whereas another might not.
[*]Package selections -- Sometimes two or more programs can fill the same role. For instance, you can use sendmail, Postfix, Exim, or qmail for an e-mail server. Most distributions will install just one of these as a default. The desktop environment difference noted in the first post is another example of this sort of difference.
[*]Package systems -- Ubuntu uses Debian packages. Fedora uses RPMs. Gentoo uses Portage. Slackware uses customized tarballs. And so on. These differences can affect how users install, uninstall, upgrade, and otherwise manage packages. An extreme example is Gentoo; Portage is a source-based system, so installing or upgrading software on Gentoo usually takes a while to compile the package. This time issue is obviously a drawback, but the local compilation means that Gentoo users can easily customize their compile options for their personal needs.
[*]System configuration GUI -- Most Linux GUI system configuration tools are used by just one, or at most a handful, of distributions. The underlying text-mode systems are usually more similar, but even then....
[*]System startup scripts and configuration layout -- Distributions differ in how they start system services (their SysV startup scripts), and to some extent in where they put some configuration files, or even *what* configuration files they use. For instance, to start or stop X as a GUI login tool on Ubuntu, you fiddle with a SysV startup script; but on Fedora, you change the runlevel to do this.
[*]System target -- Some distributions are targeted to typical desktop users, others for use as servers, or on antiquated or otherwise limited systems, or for scientific data collection, or for other specialized purposes. This is really a combination of several of the above points. A scientific data acquisition distribution, for instance, is likely to include tools to enable real-time use -- you don't want the system to miss a millisecond's worth of data because the system was updating a log file, for instance.
[/list]


Of course, given enough effort, you can change any distribution to work much more like another. You could rip out the Debian package tools on Ubuntu and replace them with RPM, for instance. The amount of effort required to do this would be phenomenal, though, and it probably wouldn't be worth the effort unless you had a compelling reason to create your own distribution. Smaller changes, such as replacing Postfix with Exim, are easier to accomplish if you just want to tweak a distribution a bit.

---

### Post by pastalavista on 2010-03-14
I stand contradicted, but not corrected, exactly... story of my life. 

"Nobody's right if everybody's wrong" ~Stephen Stills

---

### Post by srs5694 on 2010-03-15
> **pastalavista said:**
> I stand contradicted, but not corrected, exactly... story of my life. 

From the GNU Project's [Linux and the GNU Project](http://www.gnu.org/gnu/linux-and-gnu.html) Web page:

> There really is a Linux, and these people are using it, but it is just a part of the system they use.  Linux is the kernel: the program in the system that allocates the machine's resources to the other programs that you run.  The kernel is an essential part of an operating system, but useless by itself; it can only function in the context of a complete operating system.  Linux is normally used in combination with the GNU operating system: the whole system is basically GNU with Linux added, or GNU/Linux.  All the so-called “Linux” distributions are really distributions of GNU/Linux.

From the [Linux System Administrator's Guide](http://tldp.org/LDP/sag/html/gnu-or-not.html):

> Many people feel that Linux should really be called GNU/Linux.   	 	This is because Linux is only the kernel, not the applications that run  	on it.  Most of the basic command line utilities were written by the 	Free Software Foundation while developing their GNU operating system.   	Among those utilities are some of the most basic commands like cp, mv 	lsof, and dd.

If you still believe you're correct in stating that "GNU/Linux is the kernel," please back up your assertion.

---

### Post by pastalavista on 2010-03-15
> **srs5694 said:**
> snip:

If you still believe you're correct in stating that "GNU/Linux is the kernel," please back up your assertion.
I'm correct enough for me. I don't diddle with semantics. So, I'm technically inaccurate... does it make that much difference to somebody using it?

---

### Post by srs5694 on 2010-03-15
[quote=pastalavista]I'm correct enough for me. I don't diddle with semantics. So, I'm technically inaccurate... does it make that much difference to somebody using it?[/quote]

It's an impediment to accurate communication. You've reversed the meanings of "Linux" and "GNU/Linux" (at least, for those who use the latter term), and in so doing will lead anybody who absorbs your incorrect definition to be confused in future discussions about that distinction. The initial error wasn't really that bad; however, instead of acknowledging the correction, or at least letting it stand without comment, you challenged it by saying you "...stand contradicted, but not corrected...", which serves to leave a question about the meaning of "GNU/Linux" in the minds of readers who *do* want to understand the term, even if you don't.

If you want to use the term incorrectly and not "diddle with semantics," go right ahead. I respectfully request, however, that you don't contradict those who correct your errors.

---

### Post by pastalavista on 2010-03-15
> **srs5694 said:**
> It's an impediment to accurate communication. You've reversed the meanings of "Linux" and "GNU/Linux" (at least, for those who use the latter term), and in so doing will lead anybody who absorbs your incorrect definition to be confused in future discussions about that distinction. The initial error wasn't really that bad; however, instead of acknowledging the correction, or at least letting it stand without comment, you challenged it by saying you "...stand contradicted, but not corrected...", which serves to leave a question about the meaning of "GNU/Linux" in the minds of readers who *do* want to understand the term, even if you don't.

If you want to use the term incorrectly and not "diddle with semantics," go right ahead. I respectfully request, however, that you don't contradict those who correct your errors.

I apologize for my impudence. I just felt the distinction was trivial. Is there any other OS besides GNU that can run the Linux Kernel? Aren't all distributions of Linux actually GNU/Linux? Thank-you for taking it upon yourself to put me in my place.

---

### Post by capscrew on 2010-03-15
> **pastalavista said:**
> I apologize for my impudence. I just felt the distinction was trivial. Is there any other OS besides GNU that can run the Linux Kernel? Aren't all distributions of Linux actually GNU/Linux? Thank-you for taking it upon yourself to put me in my place.

It's not you imprudence, it is the inaccuracy of your statements.  Too many times the inaccuracy leads to misconception.  I agree with **srs5694**.  You should try and learn why your conclusions are wrong rather than defending them.


As an example "*Is there any other OS besides GNU that can run the Linux Kernel? *".  GNU is not an OS.  Actually neither is Linux.  Together they make the OS you know as Linux (an inaccurate term in my opinion).  GNU has it's own kernel.  The 100% GNU OS is GNU/theHURD.

As computing is precise, I believe we should be precise when describing it.

Edit: *"Aren't all distributions of Linux actually GNU/Linux?"*.  I believe that all Gnome Desktops are:  Not sure about KDE, but look at it from another point of view.  BSD uses Gnome and it is not Linux; so what is it?  It uses original UNIX code ported to the x86 platform.  Embedded Linux for sure does not have to be GNU.

---

### Post by Elfy on 2010-03-15
moved to recurring discussions

---

### Post by pastalavista on 2010-03-15
I'm not debating this any more. 

[http://www.gnu.org/](http://www.gnu.org/) 

Sorry to have ruffled your feathers.

---

### Post by srs5694 on 2010-03-15
> **pastalavista said:**
> I apologize for my impudence. I just felt the distinction was trivial. Is there any other OS besides GNU that can run the Linux Kernel? Aren't all distributions of Linux actually GNU/Linux? Thank-you for taking it upon yourself to put me in my place.

It's theoretically possible to run the Linux kernel with entirely non-GNU support utilities. This sort of thing would be most likely in embedded or other specialized applications (cell phones, DVRs, etc.).  I don't know how much GNU stuff winds up in most such devices, but that's not really the point; the Linux kernel itself is not a product of the Free Software Foundation (FSF), and the GNU utilities were not written by Linus Torvalds (the Linux kernel's original creator). Saying you run "the GNU/Linux kernel" is like saying you're using an "eMachines/Intel CPU" because your computer has the brand name "eMachines" stamped on it -- eMachines didn't make the CPU, even if their name is on the computer's case.

This can be turned around, incidentally; it's possible to run the usual set of GNU/Linux tools atop non-Linux kernels. There's [Debian GNU/NetBSD](http://www.debian.org/ports/netbsd/), for instance, which takes (more-or-less) the normal Debian GNU/Linux distribution but swaps out the Linux kernel for the NetBSD kernel.

---

### Post by Shining Arcanine on 2010-03-15
> **superarthur said:**
> My point is: how is it different to the average end-user?

Binary distributions and source distributions are significantly different from one another. Install and use Gentoo Linux for a week and you will see what I mean. The experience should be completely different from the Ubuntu Linux experience from the start. There is no GUI installer and all software is compiled from source from the commandline. It is easier than it sounds, but people who insist on doing things the Windows way might have trouble typing commands instead of doing "click forward, click forward, click finish."

---

### Post by superarthur on 2010-03-15
> **Shining Arcanine said:**
> Binary distributions and source distributions are significantly different from one another. Install and use Gentoo Linux for a week and you will see what I mean. The experience should be completely different from the Ubuntu Linux experience from the start. There is no GUI installer and all software is compiled from source from the commandline. It is easier than it sounds, but people who insist on doing things the Windows way might have trouble typing commands instead of doing "click forward, click forward, click finish."

If a person just use the terminal on Ubuntu, and compile all their software from source. What would be the difference?

---

### Post by Shining Arcanine on 2010-03-15
> **superarthur said:**
> If a person just use the terminal on Ubuntu, and compile all their software from source. What would be the difference?

One difference is that a command on Gentoo to compile something will automate hours of manual labor that requires determining dependencies, comparing the required versions with those installed on your system, determining what needs to be upgraded/installed, finding the necessary sources, doing "./configure, make, make install" for each of them, etcetera. The difference is night and day, especially if you instruct Gentoo's package manager to build stuff in parallel with "--jobs". Gentoo's package manager also has support for more advanced features that build on the ability to do all of that, such as a compiler cache, custom binary packages and distributed compilation.

This is by no means an exhaustive list of the differences and you need to install and use both distributions yourself to know the difference, but you can get some appreciation for the stuff it automates if you read Linux From Scratch:

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Gentoo is essentially Linux From Scratch wrapped in a package manager, which automates all of the menial tasks involved. The end result is a Linux installation custom tailored to your specifications. Some benefits are lower memory usage, lower CPU utilization, lower disk space requirements and faster boot-up times than you get with other mainstream distributions.

While you can compile everything yourself on Ubuntu, you will be working outside Ubuntu's package manager, which will make life difficult for you when you need to install updates. If you do not want to use Gentoo to have things automated for you, you might as well not use a distribution at all and do Linux From Scratch.

At the point where all of the software on the system was manually compiled and installed by you, you could probably convert your Ubuntu installation into a Linux From Scratch installation if you delete all of the Ubuntu specific files, which you would no longer need. Of course, you become your own package manager when you compile your own software on Ubuntu, but that happens whenever you go outside the scope of your distribution's package manager. With Gentoo, it is possible to go out of the scope of its package manager, but it is fairly easy to avoid that because updated sources are available for just about any software you could want and when they are not, it is possible to make an overlay for the package manager to make a private extension of Gentoo's equivalent of Ubuntu's repository to get the same effect as having the updated sources available in the main tree. Usually at that point, people submit the package for inclusion into the main tree and if it is made to Gentoo's standards, it is included, so other people can use it too. You could probably get the same thing if you wrote your own package manager for Ubuntu and made your own source based repository, but at that point, you are making a new distribution more than you are extending an existing one.

---

### Post by Chame_Wizard on 2010-03-16
> **srs5694 said:**
> First, the term "GNU/Linux" is, contrary to what pastalavista suggested, generally applied to Linux distributions as a whole. It's "Linux" *alone* that some people insist on applying only to the kernel (although many others use "Linux" to refer either to the kernel or to a whole distribution). The reason is that many GNU tools go into a Linux (or GNU/Linux, if you like) distribution, but the Linux kernel itself is not a product of the Free Software Foundation's (FSF's) GNU Project.

Second, there are quite a few differences between distributions, which have varying levels of significance to different people. These include, but are by no means limited to:


[list]
[*]Different software versions -- Distribution A may ship with version 1.0 of package X, version 1.2 of package Y, and version 2.7 of package Z, whereas Distribution B may ship with versions 1.1, 1.3, and 2.5 of these packages, respectively. Such differences can affect reliability and overall system feel, although probably only to a limited extent.
[*]Software compilation options -- Distributions can differ in how software is compiled. Sometimes this affects execution speed (although usually only to a limited extent) or features (depending on whether certain compile-time options were enabled). Note that this applies to the kernel, too; one distribution might support a feature like a certain filesystem or hardware driver, whereas another might not.
[*]Package selections -- Sometimes two or more programs can fill the same role. For instance, you can use sendmail, Postfix, Exim, or qmail for an e-mail server. Most distributions will install just one of these as a default. The desktop environment difference noted in the first post is another example of this sort of difference.
[*]Package systems -- Ubuntu uses Debian packages. Fedora uses RPMs. Gentoo uses Portage. Slackware uses customized tarballs. And so on. These differences can affect how users install, uninstall, upgrade, and otherwise manage packages. An extreme example is Gentoo; Portage is a source-based system, so installing or upgrading software on Gentoo usually takes a while to compile the package. This time issue is obviously a drawback, but the local compilation means that Gentoo users can easily customize their compile options for their personal needs.
[*]System configuration GUI -- Most Linux GUI system configuration tools are used by just one, or at most a handful, of distributions. The underlying text-mode systems are usually more similar, but even then....
[*]System startup scripts and configuration layout -- Distributions differ in how they start system services (their SysV startup scripts), and to some extent in where they put some configuration files, or even *what* configuration files they use. For instance, to start or stop X as a GUI login tool on Ubuntu, you fiddle with a SysV startup script; but on Fedora, you change the runlevel to do this.
[*]System target -- Some distributions are targeted to typical desktop users, others for use as servers, or on antiquated or otherwise limited systems, or for scientific data collection, or for other specialized purposes. This is really a combination of several of the above points. A scientific data acquisition distribution, for instance, is likely to include tools to enable real-time use -- you don't want the system to miss a millisecond's worth of data because the system was updating a log file, for instance.
[/list]


Of course, given enough effort, you can change any distribution to work much more like another. You could rip out the Debian package tools on Ubuntu and replace them with RPM, for instance. The amount of effort required to do this would be phenomenal, though, and it probably wouldn't be worth the effort unless you had a compelling reason to create your own distribution. Smaller changes, such as replacing Postfix with Exim, are easier to accomplish if you just want to tweak a distribution a bit.
Amen .:lolflag:

---

