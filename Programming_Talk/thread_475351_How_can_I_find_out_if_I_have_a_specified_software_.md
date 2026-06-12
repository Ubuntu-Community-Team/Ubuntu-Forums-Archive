---
title: "How can I find out if I have a specified software package installed?"
date: 2007-06-16
forum: Programming Talk
---

### Post by yinglcs2 on 2007-06-16
How can I find out if I have a specified software package installed?

I would like to know if I have installed these packages on my ubuntu

- xmms-devel
- SDL & SDL-devel

Thank you.

---

### Post by spockrock on 2007-06-16
apt-cache policy xmms-dev

will tell you

---

### Post by meatpan on 2007-06-16
The 'dpkg' command is one way to browse and verify installed packages (as well as the contents of packages).

If you know the name of the package, run 'dpkg -l | grep <package>'.  So, in your case, run 'dpkg -l | grep xmms-devel'.  The output should be a few header lines, and then a list of all matching or partially matching packages.   Another useful appication of dpkg is to list the contents of installed packages.  Run 'dkpg -L <package-name>' and all files related to the project will be listed.

---

### Post by pmasiar on 2007-06-16
start synaptic, search for package. It will show you which version is available in repositories you enabled, and which version you haveinstalled, if any. With nice GUI :-)

---

### Post by RedSquirrel on 2007-06-16
On Ubuntu, the development packages end in "-dev", so xmms-dev is what you would search for.

As for SDL, see what a search for "libsdl" turns up.

---

