---
title: "how to install KDE khelpcenter"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-09-27
New to Ubuntu, installed Kbattleship, need Khelpcenter (evidently).  Tried using synaptics but when I click on help (in Kbattleship) I still get the pop up window saying "cannot find khelpcenter".  After using synaptics, is it necessary to also use "sudo apt -get" etc.?

---

### Post by Xiong Chiamiov on 2008-09-27
[It looks like]("http://packages.ubuntu.com/hardy/khelpcenter") khelpcenter is available without having to install *all* of KDE, although you'll have to install some of KDE libs and such.  Just install it through Synaptic.

You should take a look at [this page]("http://www.psychocats.net/ubuntu/installingsoftware") on installing software.  Apt-get is a command-line interface for apt, just as Synaptic is a graphical interface for apt - they both access the same underlying thing, just different ways.

---

### Post by C0p3rn1c on 2009-01-23
sadly "sudo apt-get install khelpcenter" does not fix it

---

### Post by 484northern on 2011-10-09
This worked for me "sudo apt-get install khelpcenter4"

---

### Post by oldos2er on 2011-10-10
Closed for necromancy.

---

