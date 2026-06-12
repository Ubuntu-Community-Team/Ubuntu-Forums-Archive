---
title: "Firefox 'Grays Out' a lot"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by Dana_S on 2014-07-14
I use Firefox on Ubuntu 14.04 as my browser (I run Ubuntu from a USB drive), and there are times where the browser 'grays out', and you can't do anything until the color returns.  Some days are worse than others, and I really can't get anything done.  Is it that the browser needs to be updated?  Are there browsers that work better?

---

### Post by ubudog on 2014-07-14
Hi,

What Firefox version are you using?  You can get this from:
```
firefox --version
```

---

### Post by Dana_S on 2014-07-14
Firefox 28.0

---

### Post by ubudog on 2014-07-14
You could try creating a new profile, to see if that's the issue:
```
mv .mozilla .mozillabak
```
This moves your .mozilla directory to .mozillabak, and the next time Firefox starts up it will make a new profile.

Also, the latest Firefox is at version 30, so upgrading to that might help.

---

### Post by Dana_S on 2014-07-14
Do I go through the Ubuntu Software Center to upgrade?

---

### Post by ubudog on 2014-07-14
These commands should upgrade your packages to the latest ones in the Ubuntu repositories:
```
sudo apt-get update && sudo apt-get upgrade
```

Then check your Firefox version.

---

### Post by ubudog on 2014-07-14
Also, how much memory do you have installed on your system?

---

### Post by Dana_S on 2014-07-14
I have 1GB memory installed on my system...  My computer is an Acer Aspire M1100

---

### Post by ubudog on 2014-07-14
I have seen cases where Firefox uses too much memory, and that would be a problem with only 1GB of ram.  Have you tried an alternative, such as Google Chrome/Chromium?

---

### Post by Jerry N on 2014-07-14
FYI Firefox 30 on my machine is using 968 megabytes at this time - so 1gb RAM probably isn't nearly enough.
On my 32 bit Windows 7 machines with 3gb RAM I have trouble with Firefox bogging down after it has been running for a while.

---

### Post by Dana_S on 2014-07-14
After some discussion in another thread, I decided to switch and try Lubuntu for a little while.  Firefox appears to be working ok with it.  Lubuntu is very basic and had definitely thrown me for a little loop, but I researched how to get online...Chromium is a good idea!

---

