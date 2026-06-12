---
title: "Problems installing Netbeans 6.0"
date: 2007-12-27
forum: Programming Talk
---

### Post by rsteckly7 on 2007-12-27
Hi Everybody,

I'm trying to install Netbeans 6.0 on my machine.  The trouble is it doesn't put a shortcut on my desktop and I can't find the program.  Any ideas?  I had installed Netbeans 5.5.1 from Synaptic, but I believe version 6.0 only works with Ruby, which is the language I'd like to develop in.  Thoughts?

---

### Post by jaspreet on 2007-12-28
> **rsteckly7 said:**
> Hi Everybody,

I'm trying to install Netbeans 6.0 on my machine.  The trouble is it doesn't put a shortcut on my desktop and I can't find the program.  Any ideas?  I had installed Netbeans 5.5.1 from Synaptic, but I believe version 6.0 only works with Ruby, which is the language I'd like to develop in.  Thoughts?

Invoke it using netbeans command from terminal.

---

### Post by samjh on 2007-12-28
> **rsteckly7 said:**
> Hi Everybody,

I'm trying to install Netbeans 6.0 on my machine.  The trouble is it doesn't put a shortcut on my desktop and I can't find the program.  Any ideas?

How did you install it?  You need to install it under your own account, not as root or under sudo.

---

### Post by rsteckly7 on 2007-12-31
Hmm....that could be the problem.   I might have installed it a sudo.  I'll try that.  When I type netbeans from the terminal, I just get 5.5.1, not 6.0.

---

### Post by Majorix on 2007-12-31
First uninstall the repo version so the symlink netbeans no longer points to that. Then try installing the version you downloaded off the net.

However, I cannot understand how you can install netbeans without sudo? I mean does it only install in user's home folder?

If it doesn't work without sudo then after making sure the repo version is uninstalled, install netbeans using sudo.

---

### Post by bemcho on 2008-01-04
Hi if you didn't change the install paths in the installation wizard, netbeans6.0 
can be found here (at least on my comp) 
/usr/local/netbeans-6.0-200711050000/bin

---

### Post by samjh on 2008-01-05
> **Majorix said:**
> However, I cannot understand how you can install netbeans without sudo? I mean does it only install in user's home folder?

When using the Netbeans installer, it will install to the user's home directory if you don't run it under sudo.

---

