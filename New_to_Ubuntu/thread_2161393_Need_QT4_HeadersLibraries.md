---
title: "Need QT4 Headers/Libraries"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by finalarrow3 on 2013-07-10
Hi everyone,

I'm super new to these forums so I hope I've gotten the section right. Right now, I'm trying to install GEANT4 simulation software. However, before I can do that, I need a few programs first. What I need to install right now are the qt4 headers and libraries. I simply can't figure out the installation instructions on their website so I haven't made any progress there. But there seems to be a command (forgive me, still quite a beginner with Ubuntu) like sudo apt-get install qt... I'm just wondering which particular commands do I have to run to get the headers and libraries?

Thanks for the help.

---

### Post by oldos2er on 2013-07-10
Moved to Absolute Beginners.

---

### Post by steeldriver on 2013-07-10
I have no experience with that particular piece of software, but you probably want libqt4-dev

```
sudo apt-get install libqt4-dev
```

If the build process still complains about qt4 dependencies, you can see the other likely candidates using apt-cache e.g.

```
apt-cache search qt4-*-dev
```

or

```
apt-cache search qt4 | grep -i development
```

You may also find the apt-file program useful for this kind of thing

---

### Post by finalarrow3 on 2013-07-11
Thanks! I already have the libqt4-dev, but I tried the apt-cache search and installed the programs that seemed relevant. Now, I am an absolute beginner with Linux, would you mind explaining exactly what's happening when I used apt-cache and what the qt4 | grep -i development does when I run it? I'd like to understand a bit more about what's going on and I've never actually been educated with Linux before.

---

### Post by steeldriver on 2013-07-11
It's just searching the available packages for ones mentioning qt4 in their descriptions (*apt-cache search qt4*) then further restricting the results to those containing the string 'development', case insensitively (*grep -i development*) - the thing in between is a pipe symbol | which just sends the output of the first command (apt-cache) to the input of the second command (grep)

Are you able to configure and build GEANT4 now?

---

