---
title: "How do you change display manager?"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2011-10-15
currently I am  using kdm and I want to make lightdm default. How do I change display manager to lightdm? Thanks in advance

---

### Post by garvinrick4 on 2011-10-15
If in a version that does not use lightdm you would have to use a ppa
Have installed lightdm in Ubuntu 11.04 Natty with ppa in launchpad but
looking at it now it is not up to date last build was 7 weeks ago or so.
I would shy away from this for a while myself. This will bump it up to front incase some
other user has a better idea for you.

---

### Post by mcduck on 2011-10-15
```
sudo dpkg-reconfigure kdm
```
...and then pick the DM you want to use. It doesn't actually make any difference which DM's name you use in the dpkg command, just use one you have installed and you'll always get the same result. :)

Of course you'll have to install lightdm first.

---

### Post by sujitrjadhav on 2011-10-15
> **mcduck said:**
> ```
sudo dpkg-reconfigure kdm
```...and then pick the DM you want to use. It doesn't actually make any difference which DM's name you use in the dpkg command, just use one you have installed and you'll always get the same result. :)

Of course you'll have to install lightdm first.

I found other way of doing it. Changed setting in /etc/X11/default-display-manager file.It worked. Anyway thanks very much for telling me other way of doing same thing.

---

### Post by garvinrick4 on 2011-10-15
> Of course you'll have to install lightdm first.
Is lightdm in Natty's repo's? Is OP using 11.04 or 11.10, if in repo's of 11.04 point is moot.

---

### Post by sujitrjadhav on 2011-10-15
> **garvinrick4 said:**
> Is lightdm in Natty's repo's? Is OP using 11.04 or 11.10, if in repo's of 11.04 point is moot.

I have 11.10 installed on my dell mini

---

### Post by garvinrick4 on 2011-10-15
> I have 11.10 installed on my dell mini
Good then run McDucks line of code and choose one if more than one installed.
Can see if lightdm is installed also or any other package by.
```
sudo apt-get install aptitude
```
```
aptitude show lightdm
```
Will tell the package and if installed, nice to use aptitude.

Anyway McDuck was right on.

---

