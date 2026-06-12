---
title: "Power and management"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by Locke X on 2011-12-13
I have a usb powered and run device that seems to be receiving no power (the port is fine in win7 so it is functioning)...it has a light on it that flashes but doesn't light up in ubuntu.

There is no device manager for ubuntu as far as I know so how can I inspect the configuration for problems (from what I know of linux this question is actually much more complicated than it seems)

Linux is profoundly newbie-unfriendly and I am super-bloody frustrated by spending all day trying to get something as simple as an external wireless modem to work.

If you have an answer please make it a command line solution as my interface is a little strange. Thank you

---

### Post by Mark Phelps on 2011-12-13
Don't have an answer ... but do have a question.

Win7 comes with USB drivers preloaded (at least, for USB 1.1 and 2.0) -- and these are typically the default drivers that Linux installs along the same lines.

When you first connected this device in Win7, did it install its own drivers?  Or, did you have to run an app -- to install some software and (possibly) drivers as well?

If the answer to either of these questions is yes -- then most likely, this device is NOT going to work properly in Linux as it needs either special software or special drivers, neither of which is available by default.

---

### Post by Locke X on 2011-12-14
Yes and no... once I plugged the xwifi modem into usb in win7 all I had to do was disable my wifi mini for the xwifi modem to work along the lines of my mini BUT to get full functionality (including the extras provided by software) I did have to do an install with the provided cd.

Certainly I may need the extra functionality later but right now I just need the damn thing to work like any other xwifi modem.

After many dead ends I tried to install the package provided by alfa for linux 2.6 using sudo apt-get but I think that the fact the package is zip is a problem.

Yes I am a linux noob to the extreme and if I didn't HAVE to learn this I would have written off linux as a lost cause to new unsupported users because there are NO reliable resources for familiarizing a person with linux as far as I have seen.

---

