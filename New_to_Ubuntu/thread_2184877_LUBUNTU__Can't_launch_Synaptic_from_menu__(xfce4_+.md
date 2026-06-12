---
title: "LUBUNTU:  Can't launch Synaptic from menu  (xfce4 + lubuntu 13.10 alternate)"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by Remten on 2013-10-30
I have a fairly fresh install of lubuntu 13.10 from just a few days ago, with the xfce4 and xfce-goodies metapackages installed in addition.

I can launch Synaptic package manager just fine from the lubuntu session's drop-down menu.
But I cannot launch Synaptic from the Applications drop-down menu in xfce sessions. Synaptic does appear in the menu, but when I click on it, nothing happens.

Synaptic is installed and I can use it if I launch it from terminal.

What is causing this and how can I fix it?

(Not sure where the best place is to ask for help on this? Not even sure which is the proper forum here - desktop environments? absolute beginners? etc)

laptop  ASUS N550JV
Lubuntu 13.10 amd64 installed via alternative installer (encrypted Windows & encrypted linux)
linux 3.11.0-12-generic
xfce4 4.10.1
xfce4-goodies 4.10
Synaptic 0.80.2

---

### Post by Remten on 2013-10-31
Solution is to install policykit-1-gnome package (as described [here]("http://askubuntu.com/questions/162011/synaptic-wont-launch-from-menu-in-panel-in-fresh-lubuntu-minimal-desktop-12-04")).
I installed policykit-1-gnome package from the xfce session using Synaptic (which I had launched from the terminal with
```
gksudo synaptic
```
which allowed me to authenticate and then to launch and run the Synaptic GUI.
(The person who had been previously complaining about a problem with this was trying to launch Synaptic from the menu on a newly-installed lubuntu 12.04, installed with the minimal desktop.)

I don't yet know whether having done this has introduced any new problems though.

---

