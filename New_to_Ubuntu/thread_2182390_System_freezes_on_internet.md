---
title: "System freezes on internet"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by Philippe_Blouin on 2013-10-21
Hello.
I have been using a new A with the latest version of Ubuntu installed, and already I am experiencing quite annoying problems. The system freezes completely (mouse included) after a few minutes browsing the internet (firefox and chromium), letting me the sole option of switching the power button off and starting again. No particular website seems to be in cause (it also happens on ubuntu forums), and it never happened on any other application than internet browsers.
The first freeze occured the very first time I opened the computer, while updating : when half the packages were installed, the system froze and when I came back the rest could not be found. Could a ubuntu reinstall help?
I doubt it would be a RAM problem since the computer is new, but I still have some days left for return, if it appears to be the problem.
I'm a ubuntu newbie, so if the answers can be simply said, I'd appreciate it!
thanks,
Phil

---

### Post by varunendra on 2013-10-23
Hello Phil, Welcome to the forums !

It may help us understanding the problem better if you share with us some facts about your system, like system specs, version of Ubuntu etc. Apart from GUI tools, the output of following commands may tell us a lot about it -

Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
free -m
sudo lshw -short -numeric
uname -mr
lsb_release -d
df -h
```

And while connected to internet, please try -
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get autoremove
```
Do these operations finish successfully? Any error messages? Post them back if there are any.

---

