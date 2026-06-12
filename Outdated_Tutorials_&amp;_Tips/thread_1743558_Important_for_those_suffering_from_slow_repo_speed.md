---
title: "Important: for those suffering from slow repo speeds"
date: 2011-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by sandyd on 2011-04-29
If your suffering slow repo speeds, or have extra bandwidth to share, please consider using apt-p2p. The servers are WAY too overloaded right now, and downloads are trickling in at extremely low speeds.

Apt-p2p allows for users running apt-p2p to share bandwidth between each other, sort of like torrents, to prevent the repo from being overloaded (like it is right now).

**Setting up Apt-p2p**
```

sudo apt-get install apt-p2p
sudo /etc/init.d/apt-p2p start

```Will start the apt-p2p client. This will allow you to share your bandwidth with others, so that they can download packages that you have on your computer.

**Setting up APT to use apt-p2p** **(not required if you only want to share your bandwidth, only required if you want to download packages using apt-p2p)**
```

sudo nano /etc/apt/sources.list
```right after each
```

http://
```add
```
[FONT=monospace]
[/FONT]localhost:9977/
``` Theirs no spaces in between.
and yes, there is a slash right after the 7.

Press control + X to save the file.

You will now need to update your sources
```

sudo apt-get update
```

---

### Post by andymorton on 2011-04-29
Hi, thanks for posting this. I'll install it now. :D

andy

---

### Post by juancarlospaco on 2011-04-29
Im using FTP instead, and its super fast!

well apt-get update is a little slower than http, but download is faster than http

on */etc/apt/sources.list *replace *http://* with *ftp://*, 
but dont do it on the security repo because it dont have the FTP service,
also comment out all the lines starting with *deb-src* unless you compile/develop

---

