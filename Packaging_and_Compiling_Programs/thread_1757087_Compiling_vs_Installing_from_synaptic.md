---
title: "Compiling vs Installing from synaptic"
date: 2011-05-13
forum: Packaging and Compiling Programs
---

### Post by Spitted on 2011-05-13
Hi
I hope I'm writing this thread in the right forum.

Say I have the source of a program I wish to compile. I install it's dependencies from Synaptic. Then I compile the program (or even make install it) from the source, without Synaptic.
Since it is not a package, I can't later remove it with regular apt-get remove. Its dependencies look like they are unnecessary and unused (maybe Janitor will advise me to get rid of them?). 
Finally I get into the situation where my system, which is built to be aware of everything installed, has software that it cannot track. This mess is one thing a somewhat-newbie like me don't really get. Am I missing something or is this problem really isn't solved globally yet?

---

### Post by MadCow108 on 2011-05-13
there are solutions to this problem.
To install build dependencies I usually do not use apt-get build-dep but instead I download the package source and execute *mk-build-dep* from the devscripts package in the source directory.
This will create a meta package pulling all the build depends.
When you remove this package again all unneeded depends will be orphaned and can be removed with *apt-get install autoremove*.

To install self compiled packages you can use e.g. *checkinstall* which monitors *make install* and creates a personal package which can easily be removed again.

---

### Post by Spitted on 2011-05-13
checkinstall seems like a good tool. Thanks for the tip.
But I didn't quite understand how does mk-build-dep helps. I use checkinstall to simulate a package from the make install script. Then when I delete this package, it removes the compiled files but I still have to remember to manually remove the "meta dependencies package" created unrelated with mk-build-dep, right?

---

### Post by MadCow108 on 2011-05-13
yes but thats easy:
```
$ dpkg -l | grep build-deps
ii  cheese-build-deps                     1.0                                        build-dependencies for cheese
ii  ipython-build-deps                    1.0                                        build-dependencies for ipython
ii  libmatheval-build-deps                1.0                                        build-dependencies for libmatheval
ii  smuxi-build-deps                      1.0                                        build-dependencies for smuxi
ii  soya-build-deps                       1.0                                        build-dependencies for soya

$ sudo apt-get autoremove smuxi-build-deps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cli-common-dev libart2.0-cil-dev libgnome-vfs2.0-cil-dev libgnome2.0-cil-dev libindicate0.1-cil-dev
  liblog4net-cil-dev libnini-cil-dev libnotify-cil-dev libxml-dom-perl libxml-perl libxml-regexp-perl mono-utils
  mono-xbuild python-editobj smuxi-build-deps
0 upgraded, 0 newly installed, 15 to remove and 0 not upgraded.
After this operation, 5,304 kB disk space will be freed.
Do you want to continue [Y/n]
```

---

