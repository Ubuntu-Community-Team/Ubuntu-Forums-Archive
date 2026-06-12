---
title: "Diff between DPKG and apt-get ..."
date: 2013-11-28
forum: New to Ubuntu
---

### Post by Siva_Krishna_K on 2013-11-28
Hi,

I have noticed that few of the installers in Ubuntu will have an extension of .deb file where we need to install using "dpkg ..." command through terminal
Few of them which are system defined packages are installed through "sudo apt-get install <XXXXX>" through terminal

I would like to know what is the difference between these two scenarios. I have noticed that few of the files which i have tried to install through terminal using "apt-install" command will have an dependency issues.

Please clarity the on this query.

-SK

---

### Post by alan-pater on 2013-11-28
**dpkg** is used to install files you have already downloaded from somewhere. **apt-get** downloads and installs the package directly from Ubuntu or other approved package providers. **apt-get** automatically installs any dependencies, **dpkg** does not. 

It is a bit strange that your experience is the opposite. 

Here is how I use each option:

1) :~$ sudo apt-get install gnome-sushi

1) Download a packge from some website
2) ~$ cd Downloads/
3) :~/Downloads$ sudo dpkg -i gnome-sushi.deb
4) If dpkg gives dependency error, give up and search for a ppa with the package.

---

### Post by oldos2er on 2013-11-28
What type of "installers" are you talking about, if not *.deb files?

---

### Post by tgalati4 on 2013-11-28
"Installers" are typically scipts that install stuff.  Debian packages (*.deb) are simply files that are compressed with a collection of files that go into specific places in the file system--this is the definition of "installed."  Apt is simply a framework or a front-end for handling Debian packages.

There is an order to user-friendliness:

Software Center-->synaptic-->aptitude-->apt-get-->dpkg

They all do the same thing.  Open a terminal:

```
man apt
man dpkg
sudo apt-get moo
```

Practice using each method above, and you will quickly see the differences.

---

### Post by squakie on 2013-11-28
For a newbie, I would suggest Synaptic Package Manager as mentioned above.  In 13.04 up (I don't remember about 12.xx) you have to install it:  sudo apt-get install synaptic

Once that is installed you can look through thousamds of packages available.

---

### Post by Siva_Krishna_K on 2013-11-29
Alen, Thank you for your responce on my query.

I am confused about dependency issue that i have mentioned in this email thread earlier. Yes are right.. **dpkg** is asking for dependencies to be installed rather **'apt-get'**.
this is issue i have noticed while i was tried to installed "google video plugin" for enabling video chat option.

I will try suggested options.

Thank you.
-S

---

### Post by philinux on 2013-11-29
Gdebi is great for installing deb packages or even checking them too.

---

### Post by squakie on 2013-11-30
If you use the package manager it will get the dependencies for you.

You can also do:  sudo apt-get build-dep  to have apt find and install the dependencies for you.

---

