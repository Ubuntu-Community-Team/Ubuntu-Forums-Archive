---
title: "I get a Debian login prompt?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by REDace0 on 2008-09-30
Basically, when I boot the computer, it does to a xdm session with a Debian login prompt. For more technical people, here's how I broke it.
First I did this:
```
sudo apt-get install xubuntu-desktop
```
Then I did this:
```
sudo apt-get install fluxbox
```
I got that working, so decided to:
```
sudo apt-get remove xubuntu-desktop
```
And now I have to manually start gdm and put it on CrtlAltF8.

I'd like to fix this, could someone help?

---

### Post by jpkotta on 2008-09-30
xubuntu-desktop is a metapackage that depends on many other packages.  You should probably reinstall it and remove just the ones you don't want.  I'm guessing you just don't want xfce, so remove those.  It's generally a good idea to have at least one of the *buntu-desktop packages installed, unless you know what you're doing.
```
aptitude show xubuntu-desktop
```

---

