---
title: "[SOLVED] another &amp;quot;CLI - interperetation challenge&amp;quot;"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-12
So I want to try this game.  I don't understand which one I would want:

adamogardner@CRONUS:~$ sudo apt-get install nethack
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nethack is a virtual package provided by:
  nethack-x11 3.4.3-10.2ubuntu1
  nethack-qt 3.4.3-10.2ubuntu1
  nethack-lisp 3.4.3-10.2ubuntu1
  nethack-gnome 3.4.3-10.2ubuntu1
  nethack-console 3.4.3-10.2ubuntu1
You should explicitly select one to install.
E: Package nethack has no installation candidate
adamogardner@CRONUS:~$

I chose the gnome one since I have gnome but I get :

adamogardner@CRONUS:~$ sudo apt-get install nethack-gnome 3.4.3-10.2ubuntu1
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 3.4.3-10.2ubuntu1
adamogardner@CRONUS:~$

---

### Post by adamogardner on 2008-08-12
i can get the answers I need in synaptic.  It has the gnome version but I don't know why it won't install.

---

