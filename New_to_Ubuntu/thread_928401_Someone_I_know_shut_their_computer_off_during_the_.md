---
title: "Someone I know shut their computer off during the middle of a distro upgrade"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by diablo75 on 2008-09-23
A friend of mine has an older PC he's put off upgrading from 7.10 to 8.04 for a while and decided to do it recently.  After the downloading of the new packages started, he decided to use the computer (which I've advised him to NEVER do again while upgrading).  Elements of the desktop started to disappear, and perceiving a serious problem, he felt the next course of action would best be shutting the computer down.

His xserver was broken as a result and we've gotten him back up and running with a GUI after reconfiguring it, but what about the upgrade?  Will it be able to continue where it left off or is the damage permanent?

---

### Post by DougieFresh4U on 2008-09-23
could try 
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by wolfen69 on 2008-09-23
let's start with: ```
sudo apt-get install -f
```

---

### Post by jemate18 on 2008-09-23
> **diablo75 said:**
> A friend of mine has an older PC he's put off upgrading from 7.10 to 8.04 for a while and decided to do it recently.  After the downloading of the new packages started, he decided to use the computer (which I've advised him to NEVER do again while upgrading).  Elements of the desktop started to disappear, and perceiving a serious problem, he felt the next course of action would best be shutting the computer down.

His xserver was broken as a result and we've gotten him back up and running with a GUI after reconfiguring it, but what about the upgrade?  Will it be able to continue where it left off or is the damage permanent?

Oh... that will be damaged.  When you are upgrading, the packages in your computer are being upgraded, suppose one package is upgraded, but its dependencies were not upgraded due to interruption, that package will therefore not be able to run as expected and will produce error. More so, it might be corrupted......

better follow the post above

---

### Post by xeth_delta on 2008-09-23
Given that the some parts have already been updated, I assume that all the packages have been downloaded and installation began.

Whatever you do, do not run "apt-get clean" before finishing the upgrade (it will delete the packages from the cache).

Also, I suppose that the sources.list file has been updated too, to contain the new repositories.

You should wait a little bit longer for another suggestion or to see if somebody recommends against my suggestion, which would be to go to the command line and issue a
```
sudo apt-get update
sudo apt-get upgrade
```
and let it finish installing...

---

### Post by sam_delta on 2008-09-23
there are probably more solutions but if i were him, id backup everything and do a fresh install. (probably with simple backup or something)

sam

---

### Post by sam_delta on 2008-09-23
there are probably more solutions but if i were him, id backup everything and do a fresh install. (probably with simple backup or something)


sam

---

