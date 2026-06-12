---
title: "Can't Install Tor"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by learn-progra on 2013-10-19
I use Ubuntu 13.10 and i tried to install Tor but it give me an error packages not found when iwant to install it

---

### Post by oldos2er on 2013-10-20
Moved to Absolute Beginners.

You may just need to refresh your sources: ```
sudo apt-get update && sudo apt-get install tor
```

---

### Post by Lars Noodén on 2013-10-20
If you are just getting started, you might want to look at the Tor Browser Bundle.  It is the recommended way for beginners to get started with Tor.  It includes a version of Firefox that has been pre-configured for near-maximum privacy.  (Turning off javascript is the one improvement remaining).  It also has some privacy improving plug-ins.  You can get it for Ubuntu from the Tor Project web site.  Choose 32-bit or 64-bit as appropriate for your system.  

Otherwise, if you are determined to build things up from scratch, there are a lot of settings that need to be set and add-ons that need to be added all so that leaks are plugged.  That's always an option but the Tor Browser Bundle is the easier way.

---

### Post by vanadium on 2013-10-20
You will have a problem with the tor bundle and 13.10: the link and search fields of the tor browser won't accept keyboard input. If you have the problem, "sudo apt-get remove ibus" (and a reboot) will help, but then you will not be able to use ibus, which is a framework for foreign langage input.

---

### Post by Jim_Granite on 2013-10-22
Given this nasty bug in Ubuntu 13.10 which doesn't allow *any* keyboard input (so you can't go to a single URL) in the Tor Browser Bundle from [https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

My workaround, rather than remove the ibus, was to kill the ibus [as explained here]("http://ubuntuforums.org/showthread.php?t=2182627&p=12824210#post12824210"):
$ ibus exit

---

