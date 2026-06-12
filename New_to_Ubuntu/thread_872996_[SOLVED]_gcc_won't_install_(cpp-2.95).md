---
title: "[SOLVED] gcc won't install (cpp-2.95)"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by gudgip on 2008-07-28
Hi,

I'm trying to install the gcc compiler, so I enter in the terminal
> sudo apt-get install g++
I get an error about the package that replace it: cpp-2.95
so I try:
> sudo apt-get install cpp-2.95
cpp-2.95 is already the newest version,
so I think my system is ready to handle this one:
> g++ first.cpp -o test
but then I get this error:
> The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>
so I try the first step again.. with no result

does anyone know how to let the g++ compiler work?

many thanks, gudgip

---

### Post by ConMan318 on 2008-07-28
```

sudo apt-get install build-essential

```

---

### Post by t0p on 2008-07-28
You want to install the app **g++** (not cpp). So try:

```
sudo apt-get install g++
```

Alternatively do it through Synaptic.  g++ is in the repos.

**EDIT:** Ah yes, as ConMan318 says above, you'll also need **build-essential**. I don't know if that includes g++, or if you'll need to install the compiler too.

---

### Post by gudgip on 2008-07-28
when I try the build essential, I get an error like: build-essential isn't at your disposal

---

### Post by ConMan318 on 2008-07-28
Use Synaptic (System > Administration > Synaptic package manager), click search and search for 'build-essential'.  Check the box for the right package and click 'apply'.

---

### Post by gudgip on 2008-07-28
i already tried, but now I get the error:
> sbuild:
 Vereisten: dpkg-dev  but it is not installable
 Vereisten: dctrl-tools  but it is not installable
 Vereisten: schroot but it is not going to be installed

---

### Post by oldos2er on 2008-07-28
Check System, Administration, Software Sources to see that all repositories are enabled.

---

### Post by gudgip on 2008-07-28
Thank you! It solved this, and several other problems!

---

