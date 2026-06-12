---
title: "Version of Ubuntu to install to learn the Command Line"
date: 2015-12-30
forum: New to Ubuntu
---

### Post by soresger on 2015-12-30
First of all: I want to use Ubuntu in a virtual machine environment, and after getting the hang of it/grasping it I would like to dual-boot it with Windows 10.

My question is: which version of Ubuntu must I use? And why?

Ubuntu 14.04.3 LTS, or, Ubuntu 15.10?

My system specification:

Intel Core i5 4460 @ 3.20GHz
8.00GB RAM
Intel HD Graphics 4600
2047MB NVIDIA GeForce GTX 750 Ti 

Thanks for all the support.

---

### Post by grahammechanical on 2015-12-30
Ubuntu 15.10 has support in the form of Linux kernel security fixes for 9 months starting from the end of October 2015.

Ubuntu 14.04 (LTS) when it was first released was given support for Linux kernel security fixes for 5 years starting from the end of April 2014.

Ubuntu Long Term Support (LTS) releases come out every 2 years and are kept up to date by having what are called Point releases. So, Ubuntu 14.04 point 3 (14.04.3) has the Linux kernel (3.19) that came with Ubuntu 15.04 and it has Linux kernel support for 12 months starting April 2015.

So, your choices are this

a) Install Ubuntu 15.10 and upgrade to Ubuntu 16.04 (LTS) 2 - 3 months after Ubuntu 16.04 is released end of April 2016.
b) Install Ubuntu 14.04.3 and upgrade to Ubuntu 16.04 (LTS) 2 - 3 months after Ubuntu 16.04 is released end of April 2016.
c) Install Ubuntu 14.04.3 and upgrade to Ubuntu 14.04.4 in February 2016 and then upgrade to Ubuntu 14.04.5 about the summer of 2016 and get support for the remainder of the specified 5 year support period that begun in April 2014.

It is your choice. You might wish to download a more recent ISO at the time that you are ready to dual boot. You will need to re-install to the hard disk anyway. 

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

### Post by pence-rc on 2015-12-30
Thank you for your thorough response.  Very informative.

---

### Post by brian-mccumber on 2015-12-30
Here are some tutorials and references for writing shell scripts and using the terminal. Some people would get mad at you for calling the terminal a command line.

If you're wanting to learn to use the terminal to do things and write shell scripts the version of Ubuntu wouldn't really matter. You could learn this stuff on any Linux based operating system that uses bash.

[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

[http://ss64.com/bash/](http://ss64.com/bash/)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by DuckHook on 2015-12-31
In the Linux world, "version" has a very precise meaning, and *grahammechanical* answered your question properly with said precision, focusing exclusively on the version. However, in your case, it is also important to install the right flavour, which is what I suspect you were more interested in with your initial query.

The 'buntus come in many flavours, all with different Desktop Environments (DE). The biggest difference between them are their look and feel, which vary quite a bit. *Ubuntu* is the flagship flavour, but there is also *Kubuntu*, *Xubuntu*, *Lubuntu* and now *Ubuntu-MATE*.

You stated that you would like to run some version/flavour in a Virtual Machine. While Ubuntu will work in a VM, unless you have a gorilla of a system, it tends to be quite slow. You may prefer a lighter flavour instead. This means either Xubuntu, Lubuntu or Ubuntu-MATE.

You also state that the intent is to learn the command line. If so, then you may even prefer the simplest flavour of all: a pure Command Line Interface (CLI). There are two CLI flavours: the *mini.iso* and *Ubuntu Server*. Either of them will suit your stated purpose because they come with no GUI; they are pure jump-in-with-both-feet CLI. No namby pamby hand holding, pretty desktops, or graphical nannies.

Since you are going the VM route anyway, I would suggest that you install one of the GUI flavours as well as a separate VM with nothing but one of the CLI flavours. This will give you the chance to play with and learn from both.

---

### Post by buzzingrobot on 2015-12-31
The "command line" is a program -- a "shell"  that interprets the commands you enter there, either at the keyboard or in a script. Before computer displays were able to display GUI interfaces, the command line was the interface everyone used.  The "Terminal" we see in today's GUI interfaces is simply a program that emulates that interface.  

You can learn the "command line" just as well on any of those interfaces. I'd let other factors decide which one.

---

