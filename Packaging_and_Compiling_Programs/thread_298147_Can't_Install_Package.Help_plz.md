---
title: "Can't Install Package.Help plz"
date: 2006-11-12
forum: Packaging and Compiling Programs
---

### Post by petros-nu2lnx on 2006-11-12
i'm a new ubuntu user.i wanted to install build-essential in order to compile programs in C.i don't have a dsl connection and i've installed ubuntu in my laptop and there are no drivers for it's modem.So,i have to download the packages (.deb) manually through Windows and not by using the Synaptic Package Manager.
i downloaded build-essential but it asked for g++.
i downloaded g++ and it asked for g++-4.1.
i downloaded g++-4.1 and it asked for libstdc++6-4.1-dev.
i downloaded libstdc++6-4.1-dev and it asked for g++-4.1!!!

How am I supposed to install it when the one depends the other???
Help plz guys.I'm a new user ](*,)

---

### Post by catlett on 2006-11-12
build essential is on the installation cd. put the installation cd. It shgould prompt to add it as a repository source or something like that. It should be an automatic situation but you may be prompted to agree.
After it is added, enter this in the terminal
```
sudo apt-get install build-essential
```

---

### Post by dannyboy79 on 2006-11-12
well, something doesn't sound right since you say that you downloaded g++-4.1 and the it asks you for it again?? are you installing it after you download it?? plus I am pretty sure that build-essentail has all that stuff in it so after you download it, you tried to install it correct? if you put them on a cd, then just add the cd as a repo, then do sudo aptitude install blah  blah and it'll install them from the cd. you can a cd as a repo through the preferences within synaptic, try that.

---

### Post by petros-nu2lnx on 2006-11-12
when i'm tryin' to install every package it shows me it's dependencies.
g++-4.1 depends on libstdc++6-4.1-dev [http://packages.ubuntulinux.org/edgy/devel/g++-4.1](http://packages.ubuntulinux.org/edgy/devel/g++-4.1) 
and libstdc++6-4.1-dev depends on g++-4.1 [http://packages.ubuntulinux.org/edgy/libdevel/libstdc++6-4.1-dev](http://packages.ubuntulinux.org/edgy/libdevel/libstdc++6-4.1-dev)

---

### Post by catlett on 2006-11-12
You only need build-essential. You don't need to add anything else. Are you getting a dependency error after putting the cd in and entering sudo apt-get install build-essential?

---

### Post by petros-nu2lnx on 2006-11-12
Thanx catlett.u were right.it's on the installation cd

---

### Post by catlett on 2006-11-12
> **petros-nu2lnx said:**
> Thanx catlett.u were right.it's on the installation cd

I only know this because it is the matter of ongoing debate. The ubuntu devs stand by their 'one cd installation'. This means certain applications need to be kept off. Believe it or not they chose build-essential (personally I think it is crazy to ship a linux distro without compilers but I am just a lowly end-user)
Anyways the forum use to get mutliple 'I can't compile' 'make: command not found' etc. posts for help.  This started a bit of a debate/dialogue about including build-esential. In the end, they chose to not include it on the base install but they would add it to the cd as an extra package to be installed through apt.
This doesn't solve the initial problem but at least people can get build-essential without needing internet access.

---

