---
title: "Multiple downloads fail; unable to install from zip"
date: 2018-12-31
forum: New to Ubuntu
---

### Post by metaself on 2018-12-31
We thought Linux was supposed to be easy to install, but so far it is a mess. Three Ubuntu download attempts from this site failed, all after nearly taking 3 hours to complete, wasting about 9 hours of time. The first two were regular downloads. The third was a bit torrent. A fourth attempt with a bit torrent succeeded but put a bunch of zipped files on our computer. We can't find the .exe file among them and have not the foggiest what to do with all these separated zipped files. How in the freak do we install Ubuntu? Can we just buy this thing on disk somewhere and be done with this flailing downloading?

---

### Post by jeremy31 on 2018-12-31
You should be downloading .iso files and they need to be written to USB or DVD as system image, then boot the computer using USB or DVD

---

### Post by howefield on 2018-12-31
> **metaself said:**
> We thought Linux was supposed to be easy to install, but so far it is a mess.

It really is easy, at least as easy as installing any operating system.

> Three Ubuntu download attempts from this site failed,....

You didn't download any version of Ubuntu from this site. Perhaps you could be more specific ?

> A fourth attempt with a bit torrent succeeded but put a bunch of zipped files on our computer. We can't find the .exe file among them and have not the foggiest what to do with all these separated zipped files. How in the freak do we install Ubuntu? 

The downloaded iso needs to be burned to a USB stick or DVD. Instructions can be found [here]("https://tutorials.ubuntu.com/tutorial/tutorial-burn-a-dvd-on-windows#0"). Once you have created the boot media you can begin the installation process, details [here]("https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0").

> Can we just buy this thing on disk somewhere and be done with this flailing downloading?

Yes, a search for something like "purchase ubuntu" with your favourite search engine will give you multiple options.

---

### Post by Holger_Gehrke on 2018-12-31
Where did you download these ? The official Ubuntu downloads are **not** zip-files, they are .iso images (containing mostly compressed files, so further compressing them doesn't work too well) that you either write to a DVD or put on a USB-Stick using Rufus or something similar. You then boot of these to either try Ubuntu or install it. There obviously is no .exe to run since Ubuntu is not a (Windows-) program but an OS.

Holger

---

### Post by Impavidus on 2018-12-31
The thing you download should be an iso file, ubuntu-18.04-desktop-amd64.iso or something like that, depending on the exact version you want. If your internet connection is a bit unreliable, the torrent is the better way to download. You won't get a zip file or an exe file. Use a tool like rufus (there are several tools available) to write the iso to a usb drive to create a bootable usb, or use a dvd if you prefer. Then boot your computer from the usb drive and try the live session. If everything works, plan on installing.

---

