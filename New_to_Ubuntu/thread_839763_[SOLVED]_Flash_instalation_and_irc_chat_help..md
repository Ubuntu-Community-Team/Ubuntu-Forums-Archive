---
title: "[SOLVED] Flash instalation and irc chat help."
date: 2008-06-24
forum: New to Ubuntu
---

### Post by ElTesorillo on 2008-06-24
Hi, a am a beginner and dont know much about ubuntu but am very eager to use it. My installation very smoothly and I was very exicited. However, I seem to have hit a wall while trying to install Macromedia flash player and I also cant figure out how to connect to IRC chat. Thank you for all of your help.

---

### Post by spiderbatdad on 2008-06-24
```
sudo apt-get install xchat
```
It installs under the internet menu. Is fairly self explanatory after that: pick the sever you to sign in to and /join #channel. An IRC tutorial is here for irc commands:[http://www.irchelp.org/irchelp/irctutorial.html](http://www.irchelp.org/irchelp/irctutorial.html)

---

### Post by wormser on 2008-06-24
For Flash you need to install flashplugin-nonfree.  You can install it via Synamtic or the command line.  Applications> Accessories> Terminal.

```
sudo apt-get install flashplugin-nonfree
```

There are a bunch of different IRC clients for Ubuntu.  You can search in Synaptic for IRC.  System> Administration> Synaptic Package Manager.  Xchat is a popular one.

---

### Post by RomeReactor on 2008-06-24
Hi. What version of Ubuntu do you have? How did you install Flash?

Regarding IRC, open Pidgin (Applications->Internet->Pidgin), there go to 'Accounts->Manage', and press the 'Add' button. In the 'Basic' tab, change the protocol to IRC, for 'Screen name' choose your nick, in 'Server' you can leave 'irc.ubuntu.com' or use 'irc.freenode.net'. The 'Password' entry is only meant if you have your nick registered, so if you haven't you can leave it blank. You should leave the settings in the 'Advanced' tab as they are.

---

### Post by ElTesorillo on 2008-06-24
Thank you all so much. I have flash and IRC succescfully working. This type of support is the reason I joined ubuntu. Thanks again.

---

