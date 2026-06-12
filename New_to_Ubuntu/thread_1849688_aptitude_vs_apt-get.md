---
title: "aptitude vs apt-get"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-09-25
I've seen discussion and items on the same page about aptitude and apt-get.   Yet I don't seem to have the command aptitude available, which I gather is the newer way to do things.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

?

thanks.

= = = = = 
Just found this, maybe there is a clue here (sounds like aptitude is not a terminal command):
aptitude is a curses (terminal-based) front-end for apt. It allows you to interactively pick packages in an interactive interface rather than specifying it in a command on the command line (like with apt-get). If you want a similar front-end but with GUI, you can use synaptic.

synaptic - looks like lots more to look at.  Am I on the right track to figure out how to install Kazam and Kontact?  Kontact seems to be listed, but not installed.  Kazam is not listed.   This must not be the same list as the installed and not installed listed in the ubuntu software center.  Many more packages listed here (but not Kazam - wonder if I can add it??)

---

### Post by LowSky on 2011-09-25
aptitude is not a newer way, just different in how it handles some things. 

aptitude is better at uninstalling unneeded packages without additional commands.

see this for better explanation
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Paqman on 2011-09-25
> **Denver Dave said:**
> I've seen discussion and items on the same page about aptitude and apt-get.   Yet I don't seem to have the command aptitude available, which I gather is the newer way to do things.


Aptitude and apt-get are very similar, they're both just systems for controlling the package manager (in the case of Ubuntu, that's dpkg). Apt-get is preinstalled on all Ubuntu systems, aptitude is (IIRC) now only included on the server. You can install aptitude on your machine though, just open up Ubuntu Software Centre or Synaptic and search for it, or use:
```
sudo apt-get install aptitude
```
Aptitude has a nicer command line interface than apt-get, but otherwise works pretty much exactly the same.

> 
synaptic - looks like lots more to look at.  Am I on the right track to figure out how to install Kazam and Kontact?  Kontact seems to be listed, but not installed.  Kazam is not listed.   This must not be the same list as the installed and not installed listed in the ubuntu software center.  Many more packages listed here (but not Kazam - wonder if I can add it??)

Synaptic is like a more techy version of USC. USC deliberately hides a lot of the packages, and only shows you the actual apps. Synaptic will show everything, which is why it takes a bit more knowledge to be comfortable with.

Both synaptic and USC both get their packages from the same place, which incidentally is the same place apt-get, aptitude, Update Manager and Additional Drivers get theirs.

Kazam seems to be a dead project. It never made it into the Ubuntu repositories, although there is an old PPA [here]("https://launchpad.net/~and471/+archive/kazam-daily-stable"). That page has instructions for how to add the PPA if you're still keen. That would allow you to get Kazam through USC, synaptic, etc.

---

