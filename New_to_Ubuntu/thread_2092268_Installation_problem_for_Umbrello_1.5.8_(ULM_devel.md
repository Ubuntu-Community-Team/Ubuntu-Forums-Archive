---
title: "Installation problem for Umbrello 1.5.8 (ULM developping interface)"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by Yonel on 2012-12-07
Hi there,

My computer in running with Ubuntu 12.04. I am pretty new with linux and I would like to install Umbrello 1.5.8. So I have downloaded it on the website. On the file INSTALL, they give all the instructions to install it. They first say to type the following command: ./configure
I do it but the answer is "permission denied"... when I type the command, I am in the right folder. 

What can I do??

Thank you for your aswers.;)

---

### Post by audiomick on 2012-12-07
Hallo.

The problem you are having probably means that you need root privileges, and would need to use sudo to make the install command work. I would like to know a little more before just leaving it at that, i.e. exactly what commands you are using, exactly which directory you are in, and so on.

A simpler way might be just to search for Umbrello in the software centre. I found it in there on this 10.04 install. If there is no reason why you urgently need exactly the version you have down loaded, I strongly suggest you just install from the software centre. You may find that it is not quite the same version as is on the Umbrello site for download, but that should not be a problem, I think.

Installing from the software centre has the advantage that it is definitely easier for you as a beginner with Ubuntu, letting you get on with your "real" work quicker, and that it should not confuse your packet management system. The system knows what it installed, the update manager knows to look for updates, and so on. If you install in a manner that does not involve apt, either from the command line or in one of its guises as synaptic, the software centre or whatever, the system package management doesn't know it is there, can't keep it updated, and so on.

---

