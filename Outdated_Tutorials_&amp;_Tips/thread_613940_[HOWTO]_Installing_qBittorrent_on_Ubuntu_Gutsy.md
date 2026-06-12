---
title: "[HOWTO] Installing qBittorrent on Ubuntu Gutsy"
date: 2007-11-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Rippie on 2007-11-15
Just a quick guide how i got qBittorrent installed without any problems on my Ubuntu Gutsy.. follow the link below to see some screenshots

Screenshots: [http://sourceforge.net/project/screenshots.php?group_id=163414](http://sourceforge.net/project/screenshots.php?group_id=163414)

> First of all, close all software managers you might have open.

Let's start with the easy steps shall we ?

1. We need to edit sources.list
```
sudo gedit /etc/apt/sources.list
```

2. Add these to lines in the bottom of this file.
```
deb http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
```

Now save and close sources.list

3. Update your sources list and install the qBittorrent.
```
sudo apt-get update && sudo apt-get install qbittorrent
```

After the installation, the program can be found at **Applications > Internet > qBittorrent**

Good Luck !!

---

### Post by pante on 2007-11-18
Hi

I folowed your guide but it didn't worked.

I get a "Broken packages" message and "libzzip-0-13" is not installable. 

(Message may differ because I have a spanish language version).

---

### Post by Rippie on 2007-11-19
Where did you get error ? during installation or trying to start the program.

What Ubuntu version are you running ?

---

### Post by pante on 2007-11-26
Hi

The problem appeared during installation. I am running Xubuntu 7.04, may be that's the problem.

Anyway I installed Deluge and seems to work fine. That's why I forgot my post here :oops: . If I try qBittorrent again (got no time now), I'll tell.

Thank you for your answer!

---

### Post by asaz989 on 2007-12-02
Hey, I'm running vanilla 7.10, and after I add the lines to sources.list, I try this, and I get the error message "Couldn't find package qbittorrent".

---

### Post by Rippie on 2007-12-02
> **asaz989 said:**
> Hey, I'm running vanilla 7.10, and after I add the lines to sources.list, I try this, and I get the error message "Couldn't find package qbittorrent".

Could you please paste the lines you included in your sources.list file ?

---

### Post by asaz989 on 2007-12-02
```
deb http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
```

There it is.

I ended up going through and installing the package and dependencies manually, only now I get a problem that when I try to run qbittorrent it complains that it can't find a libmagick++.so.9, even when I've seen it in my browser in /usr/libs.:confused:

---

### Post by Rippie on 2007-12-03
hmm to be honest im not really sure, as i wrote in my post i got i to work straight away.

Im afraid you will have to open a new thread and get some help from more experienced people. :(

---

### Post by asaz989 on 2007-12-04
Well, starting a new thread, thanks for the help.

---

