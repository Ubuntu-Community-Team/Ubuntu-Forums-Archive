---
title: "Updating Ubuntu"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by SirenKing on 2012-09-19
I'm looking up How To's for this, but I'm starting out pretty clueless.

What is the quickest tool for backing up my Ubuntu Laptop and what is the best update to go for after version 8.10?

---

### Post by SirenKing on 2012-09-19
I was trying to use Clonezilla to back up my Laptop per the instructions here:
[https://help.ubuntu.com/community/EOLUpgrades/Intrepid](https://help.ubuntu.com/community/EOLUpgrades/Intrepid)

I'm not sure if my system meets the requirements. How do I find out?

---

### Post by RedRat on 2012-09-19
Others may have a different view, but I am a believer in a clean install. Basically, copy all your data/documents that you want to preserve (even your saved emails) than take the big bite and do a clean install from the CD. 

I have followed various "updaters" here from Ubuntu 8 to 12 doing it incrementally and they seemed plagued with problems. I think you are better off just reformatting your hard drive (which you can do during the install) and cleanly install Ubuntu 12.04--I recommend the LTS version. You can try doing it incrementally, and you might be the lucky one who has no problems. Give yourself a couple of stars.

---

### Post by jerrrys on 2012-09-19
Quote

"I'm not sure if my system meets the requirements. How do I find out?"

Tell us what you got to work with.  CPU, video, ram, model.

---

### Post by ty74 on 2012-09-19
I would not bother with backing up the system. Ubuntu is free, if something goes wrong just install a fresh installation. I suggest just wipe it and put ubuntu on it again. I think you would have less problems. If u still want 2 upgrade here is a site that tells you how [http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-ubuntu-10-04-via-the-terminal/](http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-ubuntu-10-04-via-the-terminal/). I do recommend getting a live cd so you can make fresh installations of ubuntu.

---

### Post by SirenKing on 2012-09-19
In the end I went with what RedRat suggested. I didn't have a lot of files on my comp and I discovered later the the only significant reason for doing incrimental installs was if you wanted to to keep system preferences. I'm not a big "let's get down to the details" guy, so I don't have any special alterations or packages on my comp. That, and Iw as worried about being plagued by probs, like RedRat said.

Only problem now is that Ubuntu 12.04 is laoging reeeeaaaalllyyy ssslllooowwwlllyyy........... It's probably a slow server. I should have gone with a different mirror, but se la vi... (probably spelled that wrong)

I let you know how it turns out.

Thanks people!!! XD

---

### Post by SirenKing on 2012-09-20
Wow. I went to all that trouble just to find out that my PC is non-PAE, so it won't run the Linux PAE-dependant Kernal required by the latest version of Ubuntu. Now I have to go with a different version. I hope that Ubuntu fixes that in their next version. I'm not the only one who got upset about it, it seems...

---

### Post by black veils on 2012-09-20
you can install lubuntu, and then install the desktop you want, or the desktop your computer has the power for, within it. i dont know what the specs are, ram etc, so i dont know which would be best for you.

Edit:

you can download the ubuntu **[mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD")**, its a small file. a command-line like installer, it downloads everything, but only what you need. its easy but if you get confused, look at **[this]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html")** for an overview of the process. doing it the mini way means you dont have to wait as long to download the .iso, and you can choose you desktop environment in the process, and it supports non-pae. make sure to pick the correct desktop for you computer specs.

---

### Post by MoebusNet on 2012-09-21
Something else to pay attention to is your video card; the newer versions of Ubuntu do not seem to support some of the older video cards as well. Some of that is the fault of the video card manufacturers who are dropping support for some of the previously-supported video cards (i.e., nvidia-96); some of it is that open-source drivers (nouveau & nv among others) have not kept up. You may find that if your system is non-PAE, the video card isn't supported any more.

Lubuntu or Xubuntu are the non-PAE versions; Xubuntu is an LTS version.

I suggest you try a live-CD or Live-USB trial first (always a good idea) before you reformat and do a clean install. It could well save you a few hours frustration.

---

