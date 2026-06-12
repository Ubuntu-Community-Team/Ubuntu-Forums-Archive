---
title: "Updating software in Ubuntu"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by Noble Bell on 2012-02-20
Being new to Ubuntu and Linux in general I have a question..

I am using Ubuntu 10.04. My question is this.. 

What is the easiest method to update my installed software in Ubuntu?

Example: BlueFish editor that is hosted in the Ubuntu repositories is several versions behind the latest available from BlueFish website. The website listed a method to update the repositories for Ubuntu by adding a line to the software sources.

Is this the best way?

---

### Post by Tony Flury on 2012-02-20
basically - yes.

Ocassionally you might need to download direct from a suppliers web site, but ideally to make sure your dependecies etc are managed fully - add a repository to the Software Manager - and get automatic updates offered to you etc.

Bear in mind if you take a version later than the one in the official version in the repository you may experience bugs etc.

---

### Post by Noble Bell on 2012-02-20
Thank you. That is what I was thinking.

---

### Post by ajgreeny on 2012-02-20
Whilst I mainly agree with the last post, you could always look into the possibility of using a ppa repository.  For bluefish you can get version 2.2.1 if you follow the instructions at [https://launchpad.net/~klaus-vormweg/+archive/ppa](https://launchpad.net/~klaus-vormweg/+archive/ppa)

If it is unsuccessful you can disable the ppa then completely remove the bluefish package and reinstall from the normal repos, but watch out for dependencies that may also have been updated and need removing and replacing with correct versions.

It is often worth looking for a ppa for any package that you want, but you feel is too out of date in the Lucid installation's normal repos. I have the stable thunderbird repos which gives me TB v10, a webupd8 repository for gthumb and gimp, and another to get tesseract v3 for much improved OCR.  Search in [www.googlubuntu.com](www.googlubuntu.com) for **ppa <packagename>** and you may be surprised at what is available.

PS [www.googlubuntu.com](www.googlubuntu.com) is a terrific search engine for all things ubuntu.

---

### Post by Noble Bell on 2012-02-20
Thanks. I will give that a try too.

---

### Post by mastablasta on 2012-02-20
also this is software upgrade not update. updates come via update manager and are usually bug fixes and security patches. But sometimes they can also be software upgrades.

In this case though you need a PPA for a newer verison of the software. There are other methods (.deb files, source etc) but PPA is probably prefered.

---

### Post by snowpine on 2012-02-20
Upgrade to 12.04 in April and you will have 2-year-newer versions of everything. :)

---

### Post by Noble Bell on 2012-02-20
@snowpine - Doesn't 12.04 contain Unity? I am really not interested in that yet. Also, I have heard that the LTS versions are the more stable of the versions available. 

In my line of work and for learning sake I need stability over newer code. So, I might stick to the versions in the repositories until I get a little smarter with Linux. I have many years of Windows experience and programming experience but Linux is new and so far I am enjoying it.

---

### Post by snowpine on 2012-02-20
> **Noble Bell said:**
> @snowpine - Doesn't 12.04 contain Unity? I am really not interested in that yet. 

12.04 will offer Unity as one of dozens of choices; you can also use Ubuntu 12.04 with Gnome, KDE, Xfce, LXDE, fluxbox, openbox, icewm, ratpoison... the list goes on! ;)

> **Noble Bell said:**
> Also, I have heard that the LTS versions are the more stable of the versions available. 

In my line of work and for learning sake I need stability over newer code. So, I might stick to the versions in the repositories until I get a little smarter with Linux. I have many years of Windows experience and programming experience but Linux is new and so far I am enjoying it.

The LTS releases (currently 10.04, soon to be 12.04) are *supposed* to be more stable, but because Ubuntu is so flaky with various hardware configurations etc., some users find that a non-LTS release is more stable *for them and their hardware*.

---

### Post by Cheesemill on 2012-02-20
> **Noble Bell said:**
> @snowpine - Doesn't 12.04 contain Unity? I am really not interested in that yet. Also, I have heard that the LTS versions are the more stable of the versions available.

12.04 is the next LTS.

---

### Post by Noble Bell on 2012-02-20
I might have to take a look at 12.04 then when I get a chance to. Thanks guys.

---

### Post by snowpine on 2012-02-20
You can take a look right now if you like (the Alpha 2 came out last week) although it will probably be a few months before it is stable enough that I can recommend it for serious work.

---

