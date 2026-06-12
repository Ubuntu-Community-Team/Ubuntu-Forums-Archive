---
title: "software install."
date: 2011-11-25
forum: New to Ubuntu
---

### Post by vrpatilisl on 2011-11-25
hi 
I want to keep all impiortant software on my harddisk. for eg. VLC and want to install offline mode. how to install software offline. which is relible site to get .deb files.
thanxs

---

### Post by sudodus on 2011-11-25
Why do you want to install it off-line? Is it difficult for you to have a stable or fast internet connection? Or do you think 'the Windows way'?

Normally in Ubuntu, software is installed from repositories with a command line from a terminal window for example
```
sudo apt-get install vlc
``` or from ***synaptic*** or ***software-center*** which are graphical user interfaces to apt-get. When you install this way, you will also receive offers to update the software in the same way as all system updates.

So if you have an internet connection, I strongly recommend that you use this normal method to install programs. Use the manual download and install (and if necessary compile) method only for programs that are not included in the repositories or if you have no internet connection to your computer.

---

### Post by mastablasta on 2011-11-25
if you wish you can make a backup selection of which programmes you installed or as some people do it make a script that you then run and it iwll install all the porgrammes you like.

---

### Post by mlentink on 2011-11-25
> **vrpatilisl said:**
> hi 
I want to keep all impiortant software on my harddisk. for eg. VLC and want to install offline mode. how to install software offline. which is relible site to get .deb files.
thanxs

Any particular reason why you want this? You'd be certain of one thing: outdated software. Most software that is available in the repositiories is, just as ubuntu itself, constantly being developed, and therefore new versions will become available at regular intervals. Obviously, if you were to store a particular version of the package on you local disk, you would not take advantage of that.

Should you want to download individual packages, take a look at packages.ubuntu.com

---

