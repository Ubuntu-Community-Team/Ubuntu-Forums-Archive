---
title: "How do I install SeaMonkey?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by deleyd on 2008-05-28
Ubuntu 8.04 I downloaded the Seamonkey for Linux from [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/) and unpacked the archive. I now have a directory with the following files:
[LIST]
[*]config.ini
[*]installer.ini
[*]MPL-1.1.txt
[*]README (yes I read it)
[*]seamonkey-installer
[*]seamonkey-installer-bin
[/LIST]
Tried double-clicking on a few files with no success. Decided to open a terminal prompt, navigate to that directory, entered: seamonkey-installer

david@david-laptop~Downloads/seamonkey-installer$ seamonkey-installer
bash: seamonkey-installer: command not found

and,... I'm out of ideas.

---

### Post by Oldsoldier2003 on 2008-05-28
> **deleyd said:**
> Ubuntu 8.04 I downloaded the Seamonkey for Linux from [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/) and unpacked the archive. I now have a directory with the following files:
[LIST]
[*]config.ini
[*]installer.ini
[*]MPL-1.1.txt
[*]README (yes I read it)
[*]seamonkey-installer
[*]seamonkey-installer-bin
[/LIST]
Tried double-clicking on a few files with no success. Decided to open a terminal prompt, navigate to that directory, entered: seamonkey-installer

david@david-laptop~Downloads/seamonkey-installer$ seamonkey-installer
bash: seamonkey-installer: command not found

and,... I'm out of ideas.
```
sudo apt-get install seamonkey
```

---

### Post by SunnyRabbiera on 2008-05-28
You do not install software in linux like you do in windows.
we have something called a repository, a vasy library of apllications for you to use...
here is a good guide on how to use them:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Troll_the_Great on 2008-05-28
Hmm...What format is it? Tar.gz? If yes, it's a bit more complicated...Here is a link witch may help you [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by kwacka on 2008-05-28
.deb format are the format used by Debian-based distributions (including X/K/ed/Ubuntu).

If you have repositories enabled .deb files are automatically installed along with all the libraries, etc they depend upon.

See:  [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

Check [http://www.getdeb.net](http://www.getdeb.net) for deb files that aren't in the Ubuntu repositories. 

If there are no .deb files available for a particular application you want you will download (probably) as a tar.gz file. Unpack it and follow the instructions in the INSTALL or README file in that directory.  Usually you will have to go to that directory in a terminal windows, type ./configure, then make, sudo make install & make clean. You may well get error messages about missing libraries which you need to install first.

Probably best to install checkinstall first to enable easy (well easier) uninstallation.

---

### Post by oldos2er on 2008-05-28
> **deleyd said:**
> 
[LIST]
[*]config.ini
[*]installer.ini
[*]MPL-1.1.txt
[*]README (yes I read it)
[*]seamonkey-installer
[*]seamonkey-installer-bin
[/LIST]
Tried double-clicking on a few files with no success. Decided to open a terminal prompt, navigate to that directory, entered: seamonkey-installer

david@david-laptop~Downloads/seamonkey-installer$ seamonkey-installer
bash: seamonkey-installer: command not found

and,... I'm out of ideas.

 Try ./seamonkey-installer

---

### Post by crf on 2008-05-28
> **oldos2er said:**
> Try ./seamonkey-installer

Do that command in the terminal while you're in the directory containing seamonkey-installer. And if it didn't work, you may need to make the seamonkey-installer executable, with the chmod command (like chmod u+x seamonkey-installer).

---

### Post by DoritosBR on 2008-05-28
Seamonkey is on Ubuntu repositories
Click on "System" -> "Administration" -> Synaptic

Click on "Search"
Search for "seamonkey"

Mark the packages you want to install
Suggestions:
seamonkey
seamonkey-browser
seamonkey-gnome-support
seamonkey-mailnews

And then click "Apply"

Wait for it to download and install

---

### Post by P3ngu1n0 on 2008-05-29
Try:
   sudo apt-get install alien
   sudo alien -d [nameofpackage].tar.gz
It will take a while but it will make a .deb
double click the .deb

---

### Post by spiderbatdad on 2008-05-29
> **P3ngu1n0 said:**
> Try:
   sudo apt-get install alien
   sudo alien -d [nameofpackage].tar.gz
It will take a while but it will make a .deb
double click the .deb

Alien is used for converting RPM packages, not tar.gz packages.
Checkinstall is used for making tar.gz packages into deb packages.

---

### Post by Oldsoldier2003 on 2008-05-29
Alien should always be a very  last resort. Even though it works fine in most cases, its better and less likely to cause problems if you compile from source. Alien can inject inconsistencies into your dependencies, which over time can add up and create nasty,unforseen issues.

---

### Post by Oldsoldier2003 on 2008-05-29
> **P3ngu1n0 said:**
> Try:
   sudo apt-get install alien
   sudo alien -d [nameofpackage].tar.gz
It will take a while but it will make a .deb
double click the .deb

Considering seamonkey is in the repos and also available as source, using alien is really not the best option.

---

### Post by P3ngu1n0 on 2008-05-29
> **spiderbatdad said:**
> Alien is used for converting RPM packages, not tar.gz packages.
Checkinstall is used for making tar.gz packages into deb packages.
no it works on those too! i tried it!

---

### Post by kwacka on 2008-05-29
> **P3ngu1n0 said:**
> no it works on those too! i tried it!

Yes, it works.

But why did you try it?

A simple: ```
sudo apt-get install seamonkey
```would have sorted it.

To me, unless it was an educational exercise, there was no point.

---

### Post by tubuun on 2008-06-30
> **kwacka said:**
> Yes, it works.

But why did you try it?

A simple: ```
sudo apt-get install seamonkey
```would have sorted it.

To me, unless it was an educational exercise, there was no point.
thanks much!
tubuun

---

### Post by Papa-san on 2008-06-30
Here... Look at this:
["How to install anything in Ubuntu."]("http://www.monkeyblog.org/ubuntu/installing/")

---

