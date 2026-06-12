---
title: "How do I make package manager intelligently handle programs compiled from source?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by laptoplinux on 2008-11-11
In my case, I have two programs, emacs and gnuplot, that I have compiled from recent sources because the ones in the repositories have bugs or deficiencies that either can't be corrected (pdf terminal support), or haven't been corrected in the hardy repositories yet (emacs xft bolding bug)

These programs were installed in /usr/local/bin.

But when I'd like to install a package from synaptic that depends on these packages, synaptic insists on installing the repository versions of the programs as well.  Furthermore, when the dependent programs are called, they only use the repository versions, so the bugs/deficiencies are still there.

Is there any way to make the package manager recognize the programs that were compiled from source and get dependent programs to use those versions?

---

### Post by Pro-reason on 2008-11-11
No, package managers can only manage packages.  If you want to compile stuff and have it interact with packages, then you need to package what you have compiled.  There are various guides to creating .deb packages.

---

### Post by louieb on 2008-11-11
**checkinstall** may do what you want it to. its ib the repositories
> CheckInstall keeps track of all the files created or
modified by your installation script ("make install"
"make install_modules", "setup", etc), builds a
standard binary package and installs it in your
system giving you the ability to uninstall it with your
distribution's standard package management utilities.

 Homepage: [http://asic-linux.com.mx/~izto/checkinstall/]("http://asic-linux.com.mx/%7Eizto/checkinstall/")

---

### Post by Patrick793 on 2008-11-11
> **louieb said:**
> **checkinstall** may do what you want it to. its ib the repositories
I was going to suggest that.
All you do is install checkinstall (sudo apt-get install checkinstall), and then when compiling things, instead of doing sudo make install, do sudo checkinstall. Checkinstall also makes a nice little deb incase you need to install it on multiple PCs.

---

### Post by zvacet on 2008-11-11
[CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

