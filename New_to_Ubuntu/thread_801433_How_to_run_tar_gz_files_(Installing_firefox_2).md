---
title: "How to run tar gz files? (Installing firefox 2)"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by pimpsahoy15 on 2008-05-20
Well, I just got ubuntu, and Im loving it...glad to get away from that vista garbage.

Now, I am aware that firefox 3 beta 5 comes with ubuntu, but I dont want to use that...I want to use firefox 2, because all of my add-ons are incompatible with the beta.  So I go to download the Linux version of 2.0, and I found that it was in tar gz, an archive file, not an executable file.  So, I'm having trouble figuring out what commands to use and what to do...I ahve never used linux before, so being precise and exact in all responses would be appreciated.

---

### Post by perlluver on 2008-05-20
> **pimpsahoy15 said:**
> Well, I just got ubuntu, and Im loving it...glad to get away from that vista garbage.

Now, I am aware that firefox 3 beta 5 comes with ubuntu, but I dont want to use that...I want to use firefox 2, because all of my add-ons are incompatible with the beta.  So I go to download the Linux version of 2.0, and I found that it was in tar gz, an archive file, not an executable file.  So, I'm having trouble figuring out what commands to sue and what to do...I ahve never used linux before, so being precise and exact in all responses would be appreciated.

You can install firefox 2 from the repos, go to add/remove and look for Firefox 2 package.

---

### Post by pimpsahoy15 on 2008-05-20
> **perlluver said:**
> You can install firefox 2 from the repos, go to add/remove and look for Firefox 2 package.
I go to add or remove programs, but only firefox 3 is in there...and i have no idea what the repos are.

---

### Post by perlluver on 2008-05-20
> **pimpsahoy15 said:**
> I go to add or remove programs, but only firefox 3 is in there...and i have no idea what the repos are.

At the top it should say supported applications, make sure All Available Applications is checked and then Firefox 2 will be available under Internet.

---

### Post by PinkFloyd102489 on 2008-05-20
Open Synaptic Package Manager and search for 'firefox-2'. Then mark it for installation.

---

### Post by metasolaris on 2008-05-20
> **pimpsahoy15 said:**
> I go to add or remove programs, but only firefox 3 is in there...and i have no idea what the repos are.

SYSTEM > PREFERENCES > SYNAPTIC PACKAGE MANAGER

just use 'Search' to find the software you want

tick the box

install!

BW
meta

---

### Post by avtolle on 2008-05-20
Firefox2 web browser is the name that shows up when I checked "Add or Remove Programs", above Firefox. I've "all available applications" (or whatever) selected, so you might want to do that before looking (will require a reload). "Repos" is short for repositories, which contain applications, etc., for Ubuntu.

---

### Post by pimpsahoy15 on 2008-05-20
I found it thanks :)

---

### Post by Exsecrabilus on 2008-05-20
You must also install **firefox-2-gnome-support**, **flashplugin-nonfree** and (optionally) **mozilla-firefox-locale-en-gb** for better Firefox functioning.

To get these packages, just go **Applications** >> **Accessories** >> **Terminal** and type in:

```
sudo apt-get install firefox-2-gnome-support flashplugin-nonfree mozilla-firefox-locale-en-gb
```

---

