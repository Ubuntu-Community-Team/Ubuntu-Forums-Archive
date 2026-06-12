---
title: "Mono 1.1.13 install on ubuntu breezy"
date: 2006-01-31
forum: Programming Talk
---

### Post by ifeelcool.com on 2006-01-31
Is there any repository for mono 1.1.13, this is the latest stable release for mono!
I found one, but it is not installing because of some dependencies wich didn't install!

Why are these dependencies so hard to fix? Isn't there some install script?

---

### Post by Viro on 2006-01-31
The problem is that the new version of Mono depends on libs that are newer than what is shipped with Ubuntu. The backport team aren't too keen on simply updating to the latest version of any library as it could jeopardize the stability of the system. The repository on the Mono site is for Debian 'unstable', so that should clue you in to why it's called 'unstable' :).

You could wait for the next version of Ubuntu, or you could just compile Mono and required libraries yourself from source.

---

### Post by public_void on 2006-01-31
If you want the latest mono, then remove the previous one and compile from source. You may find some dependency problems, but theres a good guide [here]("http://www.howtoforge.com/node/887").

---

### Post by ifeelcool.com on 2006-02-01
Ok, sound logic, so these new libraries may damage my system. And there for it is not possible to install it from synaptic!

Are there more packages available from the debian repositories? And could i install these packages? Or do they depend on new/other libraries, wich are not supported by ubuntu?

Thanks for the help!

---

