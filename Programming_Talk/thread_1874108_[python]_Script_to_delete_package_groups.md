---
title: "[python] Script to delete package groups"
date: 2011-11-02
forum: Programming Talk
---

### Post by Fabioamd87 on 2011-11-02
If I give apt-get remove ubuntu-desktop instead of all packages of the group will be deleted only the metapackage, with no real effect to the system.

So I gave the command apt-cache show ubuntu-desktop | grep Depends:
and get all the dependencies package.

I wrote a little python script to remove the , is:

```

import string
f = open("source","r")
s = f.read()
print s
s = s.replace(",","")
print s
```

but now I've seen that:

```
The following packages have unmet dependencies:
 libkpimutils4 : Depends: libkemoticons4 (>= 4:4.6) but it is not going to be installed
 openjdk-6-jre-headless : Depends: openjdk-6-jre-lib (>= 6b23~pre10-0ubuntu5) but it is not going to be installed
                          Depends: ca-certificates-java but it is not going to be installed
                          Recommends: icedtea-6-jre-cacao (= 6b23~pre10-0ubuntu5) but it is not going to be installed
                          Recommends: icedtea-6-jre-jamvm (= 6b23~pre10-0ubuntu5) but it is not going to be installed
```

there is a cascade option for apt-get like pacman -Rc packagename
that remove all the target dependencies?
thanks

---

### Post by 11jmb on 2011-11-02
```
sudo apt-get autoremove <package_name>
``` removes a package and its dependencies if they are safe to remove

---

### Post by Fabioamd87 on 2011-11-02
```
fabio@abulafia:~$ sudo apt-get autoremove ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 61.4 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 180672 files and directories currently installed.)
Removing ubuntu-desktop ...
fabio@abulafia:~$ 

```

---

### Post by Sworddragon on 2011-11-03
Theoretically apt-get autoremove should remove all packages that are set to automatic and haven't any package that is a reverse dependency of this package on any iteration which is set to manual.

But there is currently a bug that precents apt-get autoremove to find all this packages: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/667468](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/667468)

I have written my own scripts in python that maintain my system. They scan the state of dpkg with it's own routines and can find all these packages. They can even set all packages of the system to a minimal "manual" state. This makes it easier to keep the system clean. But they are unfriendly to --install-recommends and will remove these packages too because there is a concept missing in apt for a good handling of "optional dependencies".

---

### Post by 11jmb on 2011-11-03
It will not delete any packages that are a dependency for others. So I'm guessing that removing Java is going to kill at least one other package

---

### Post by Sworddragon on 2011-11-03
> **11jmb said:**
> It will not delete any packages that are a dependency for others.

It will as explained in my post (that is why I pointed explicitly to automatic and manual packages).

---

### Post by cariboo on 2011-11-03
If you use the purge option with apt get it will remove everything a package installs. From man apt-get:

 > purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).

---

### Post by 11jmb on 2011-11-03
> **Sworddragon said:**
> It will as explained in my post (that is why I pointed explicitly to automatic and manual packages).

You sure?

from the man page:

> 
autoremove is used to remove packages that were automatically
installed to satisfy dependencies for some package and that are no
more needed.

I thought that meant that if there were other dependencies, the package would remain.

---

### Post by Sworddragon on 2011-11-03
> **11jmb said:**
> I thought that meant that if there were other dependencies, the package would remain.

This is true if these dependencies lead somehow to a manual package (or if they are self a manual package).

---

### Post by 11jmb on 2011-11-03
OK that makes sense, thanks for the clarification.

---

### Post by Sworddragon on 2011-11-03
> **11jmb said:**
> OK that makes sense, thanks for the clarification.

No problem :)

I have analyzed a long time how apt and dpkg works to write these scripts that help me to maintain my system. The logic there is very complex especially if you try to programm something with it. Recursions, loop dependencies, conditional dependencies and so on. I have many times fixed my scripts because there are often programming errors appearing (this is not rare on this "higher" difficulty). But currently I can't find any errors anymore (which doesn't mean there are no potential bugs).

---

### Post by Fabioamd87 on 2011-11-03
So you are the right person to help me. :)

I dont know that automatic or manual package is, but in archlinux there is a **simple** option, called cascade.

if a depends on b and b depends on c, giving pacman -Rc a

delete b and c too.

another thing that i like of pacman is that if I remove a group, like ubuntu-desktop it remove all the package of that grop, is what I want to do.

i would like to rewrite a sort of pacman for ubuntu if necessary.

---

### Post by Sworddragon on 2011-11-03
> **Fabioamd87 said:**
> if a depends on b and b depends on c, giving pacman -Rc a

delete b and c too.

As already said "apt-get autoremove" is the solution. But as I already said this part of apt is a little broken and there is another problem that prevents a real cleaning.


> **Fabioamd87 said:**
> another thing that i like of pacman is that if I remove a group, like ubuntu-desktop it remove all the package of that grop, is what I want to do.

I don't know what these groups from pacman are but apt hasn't such a construct. There are virtual packages that are resolved to conditional real packages but this shouldn't be the same. I think autoremove from apt matches "group" in pacman at the most too. It removes packages (dependencies) in the "Depends-group" of the package file if some conditions match.


> **Fabioamd87 said:**
> i would like to rewrite a sort of pacman for ubuntu if necessary.

Maybe my scripts do already the jobs that you want to do. They are in the attachements and you can try them if you want. But for security reasons you should make a backup before using them.

For explanation: dpkg.py is the core of all scripts. It is a library that contains all methods for the other scripts.

clean.py will look for packages that are not needed anymore (this will solve your "pacman -Rc a" problem). Beware that it will be also unfriendly to packages that are installed with --install-recommends if they are not a real needed dependency of a manual package). clean.py -u (uninstall) looks for these packages. clean.py -p (purge) will look for configuration files of already uninstalled packages. You can even combine these arguments like clean.py -pu.

nested_packages.py will set manual packages to automatic which have already a higher level package that is set to manual. After doing this clean.py will maybe find even more packages.

installed_packages.py will show you all packages that are set to manual. This is usefull after nested_packages.py was executed. It is like a software list in windows.


These are all scripts that I have written around dpkg. Some scripts will call sudo at the beginning because they need it for some actions (for example removing old configuration files).

---

### Post by Fabioamd87 on 2011-11-03
thanks, now I think i deleted all the ubuntu-desktop related files. (I'm on kubuntu-desktop right now)

now I don't know if I should continue playing with python-apt or stop :)

---

### Post by Sworddragon on 2011-11-03
> **Fabioamd87 said:**
> now I don't know if I should continue playing with python-apt or stop :)

Install Ubuntu in a virtual machine and do some experiments :)

---

### Post by gsmanners on 2011-11-03
Those scripts could stand to have some options for a dry run (i.e. apt-get -s something).

---

