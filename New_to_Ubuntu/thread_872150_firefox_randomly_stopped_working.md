---
title: "firefox randomly stopped working"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-07-27
it just wont load, it tried running it via terminal and this is what i get

joe@joe-laptop:~$ firefox
Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.
joe@joe-laptop:~$

---

### Post by gjoellee on 2008-07-27
try this and then run firefox...
> sudo apt-get install firefox
have you tried running it from the menu?

---

### Post by WinterMadness on 2008-07-27
> **gjoellee said:**
> try this and then run firefox...

have you tried running it from the menu?


i ususally  run it from the menu, its just the terminal lets you know whats going on a little better

anyway i tried reinstalling it and i got this

joe@joe-laptop:~$ sudo apt-get install firefox
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox-3.0: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
               Depends: xulrunner-1.9 (>= 1.9.0.1) but 1.9+nobinonly-0ubuntu0.8.04.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
joe@joe-laptop:~$

---

### Post by gjoellee on 2008-07-27
try this:
> sudo apt-get -f install

---

### Post by WinterMadness on 2008-07-27
> **gjoellee said:**
> try this:

dosent work.
i even tried reinstalling firefox and i get errors.

---

### Post by sengines on 2008-07-27
What are the errors?

since you say its reinstalled why dont you do a "sudo killall firefox", and try to start it, maybe theres an instance running in the background.

---

### Post by WinterMadness on 2008-07-28
> **sengines said:**
> What are the errors?

since you say its reinstalled why dont you do a "sudo killall firefox", and try to start it, maybe theres an instance running in the background.

its not even on my system anymore for some reason.
when i try to reinstall it, it says something about broken packages

---

### Post by gjoellee on 2008-07-28
do this: go to synaptic, and pretty much down in the left corner there is a button called status, click on it. The list above should change an there should be mentioned something about broken package. Go there and take a complete removal of the package. Or you can locate the broken package with synaptic (it should be marked [COLOR=Red]red[COLOR=Black], and then take a complete removal, is nothing of this works follow the steps below....[/COLOR][/COLOR]




Go to synaptic and install > ubuntu-desktop if this doesn't help you install firefox from synaptic. if this doesn't work download firefox from [www.mozilla.com]("http://www.mozilla.com") and use these install instructions:

extract the downloaded tarball and put it to your home folder

cd firefox

./firefox




Or are you trying to compile from source?

If so you usually have to:

-Install all build dependencies for the program. (Can usually be found by googling)

cd /path/to/sourcetarball

tar -xzvf source.tar.gz

./configure --prefix=/usr

make

sudo make install



Then to uninstall:

cd /path/to/source

sudo make uninstall              open terminal:

cd Desktop

tar -xzvf firefox-2.0.0.14.tar.gz

cd firefox

./firefox

Or are you trying to compile from source?

If so you usually have to:

-Install all build dependencies for the program. (Can usually be found by googling)

cd /path/to/sourcetarball

tar -xzvf source.tar.gz

./configure --prefix=/usr

make

sudo make install



Then to uninstall:

cd /path/to/source

sudo make uninstall

---

