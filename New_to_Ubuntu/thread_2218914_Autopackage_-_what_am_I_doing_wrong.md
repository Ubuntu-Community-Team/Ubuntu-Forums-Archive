---
title: "Autopackage - what am I doing wrong?"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by yan4 on 2014-04-22
Hi,

One of the things that more puzzle me with Linux is the package install. Till now I have used commands from terminal that I just copy-and-paste from somewhere and it has worked. However I confess that I don't feel too comfortable just pasting a crazy long command into my terminal. Anyway...

Today I downloaded for the first time an 'autopackage' (Xara LX 0.7). Not knowing exactly what was an 'autopackage' (but able to suppose what it does) I made some research and confirmed that it was what I thought: a package installer (such as Windows MSI?).

I have read that Autopackage should be part of my Ubuntu 12.10 distro, but it is not there. Anywhere.

The autopackage from Xara just show up as a generic file (script shell type) at my downloads folder and if I click twice over that will only open in a text editor. Definitively it is not right. I tried to find Autopackage app to download and install on my Ubuntu but couldn't find it anywhere.

What is the trick here?

Thanks!

---

### Post by sandyd on 2014-04-22
Xara is already in the repos

You should be able to find it in the software center - or if it cant be found, run
```

sudo apt-get install xaralx
``` (side note: password entry will not be visible)

---

