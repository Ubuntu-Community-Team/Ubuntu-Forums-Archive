---
title: "Can't install kicker?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-10-30
I'd really like to install kicker in Intrepid Ibex Beta... But I dunno what I'm doing wrong

```

misha@ubuntu:~$ sudo apt-get install kicker
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kicker: Depends: kdebase-data (< 4:3.5.11) but 4:4.1.2-0ubuntu4 is to be installed

```

---

### Post by bodhi.zazen on 2008-10-30
did you update ?

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Then re-try kicker.

---

### Post by seyon on 2008-11-26
Well, the kicker has been replaced by the plasma bar of the KDE 4 release. To install kicker on the current Ubuntu Intrepid 8.10, you have to do the following procedures.

Open a terminal and type:

sudo apt-get install kdelibs4c2a
sudo sed -i 's/intrepid/hardy/' /etc/apt/sources.list
sudo apt-get update
sudo apt-get install kicker
sudo sed -i 's/hardy/intrepid/' /etc/apt/sources.list
sudo apt-get update

And you are done :)

---

