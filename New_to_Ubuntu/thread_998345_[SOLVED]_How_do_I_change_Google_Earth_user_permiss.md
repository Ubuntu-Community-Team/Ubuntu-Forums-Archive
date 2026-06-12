---
title: "[SOLVED] How do I change Google Earth user permissions?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by bwallum on 2008-11-30
Hi

I'm running googleearth4.3 from Medibuntu install through synaptic. I can only run GE with 'sudo googleearth'

Probably, I have a pile of redundant stuff having tried for days. I have uninstalled all, then found the 'dot' googleearth file and manually deleted it. I have searched and removed all responding to a googleearth search in nautilus as root.

I loath the thought of doing anything over the internet as root particularly when commercial stuff is being thrown at me.

How do I change permissions to make GE run when I am in my user home please? (i.e. run as non root)

---

### Post by spiderbatdad on 2008-11-30
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by bwallum on 2008-11-30
Hole in one! Thank you!

For anybody following:

Google Earth 4.3 works on 64bit machines. Install using synaptic or```
sudo apt-get install googleearth-4.3
```

Run from Applications>Internet>Google Earth

If you get the gui (eventually) but no globe then test the install with```
sudo googleearth
```If that works ok then delete the config files (they get auto regenerated) with (don't miss the dot)```
rm -Rf .config/Google
```and ```
rm -Rf .googleearth
```

If that doesn't do it for you this is where further troubleshooting tips can be found [https://help.ubuntu.com/community/GoogleEarth#Troubleshooting]("https://help.ubuntu.com/community/GoogleEarth#Troubleshooting")

---

### Post by wijit on 2009-11-30
> **bwallum said:**
> Hole in one! Thank you!

For anybody following:

Google Earth 4.3 works on 64bit machines. Install using synaptic or```
sudo apt-get install googleearth-4.3
```

Run from Applications>Internet>Google Earth

If you get the gui (eventually) but no globe then test the install with```
sudo googleearth
```If that works ok then delete the config files (they get auto regenerated) with (don't miss the dot)```
rm -Rf .config/Google
```and ```
rm -Rf .googleearth
```

If that doesn't do it for you this is where further troubleshooting tips can be found [https://help.ubuntu.com/community/GoogleEarth#Troubleshooting]("https://help.ubuntu.com/community/GoogleEarth#Troubleshooting")

Hang on guys!
The difference between running GE as normal user and root occurs because the user has no right to write to the config files - of course, the files that you suggested to delete. Though deleting files will enable GE to run but you will get a message warning you that GE fails to save MyPlace information. That means you will have no chance to set your first screen, distance unit, your place marks, ... Normally these information(s) are recorded on exit and that means every time you run GE you run a newly installed.
I compared GE installation on 2 of my notebooks where GE behaves differently. One can go smoothly while the other can only run with sudo. Only this of 247 threads about GE on UbuntuForum seems very similar to what was happening to me. What I found is the different file permission of .config/Google between them. On the one that can only run with sudo the owner is root while on the other the directory and its contents belong to myself. Thank you for every one here for at least it ensures me that it is about problems of file permission. My advice is not to delete the files but simply change their owner to normal user - you.:D

---

### Post by bwallum on 2009-12-01
Thanks for the update.

As of 17th September 2009, GE ver 5.1.3509.4636 (beta) has been running out of the box on AMD64. 'googleearth' is available in Synaptic Package Manager from medibuntu repos.

---

