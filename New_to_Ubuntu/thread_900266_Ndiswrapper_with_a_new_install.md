---
title: "Ndiswrapper with a new install ?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by dquigley13 on 2008-08-25
Hi,

I downloaded..

Ubuntu 8.04 LTS Desktop Edition 

for an old IBM A31 laptop. It works great, however I am trying to get the PCMIA Belkin Wireless G Notebook card with it working. I have read a few threads here about ndiswrapper and tried to install the latest version to no avail. Lots of errors.

Other threads seem to indicate that there is a version on the disk, which there appears to be, using that I was able to get a Wireless configuration option on my admin menu, which when I pointed to the XP driver for my card did indeed pick up that there was hardware present. But did nothing else, didn't show me a list of wireless networks or anything like that. Despite this, ndiswrapper -l shows me no ndiswrapper installed. Trying to manually install, fails half way through at some line to do with gcc.

Anyway, I have re-installed the O/S from scratch. How do I from a plain vanilla version of Ubuntu 8.04 LTS ensure that ndiswrapper is installed and working. I am not concerned with getting the card working yet, just want to get ndiswrapper up and running first.

Thanks

---

### Post by caljohnsmith on 2008-08-25
First make sure you have your Ubuntu CD in your CD-ROM drive; then go to System > Admin > Software Sources, click the "third-party software" tab, and hit the "add CD-ROM" button to add your Ubuntu CD. 

Next in a command line run:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
That should get you ndiswrapper. :)

---

