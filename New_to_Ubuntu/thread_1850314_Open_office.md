---
title: "Open office"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by mdt90 on 2011-09-26
hello friends,

i have installed lubuntu linux 10.04 on my old laptop.below is its configuration-
sony electronics inc.
UCG114XEUM
intel(R) Pentium(R) 3
Mobile CPU 1133MHz
1.13 GHz ,256 mb of RAM

I want to use it for word processing and presentation.
which software should i prefer to fulfill above needs?
should i go for open office?if yes, what version will work fine without slowing that laptop?
can somebody post the reference of the site that provides it?

any help would be appreciable.

---

### Post by Paqman on 2011-09-26
Open Office is probably a bit fat for you. Try Abiword for word processing, it's nice and light. I'm not too sure about lightweight presentation apps so I'll leave that to someone else.

---

### Post by technosysind on 2011-09-26
Open Office 3.3.0 is good. U can download the 32-bit version :)

---

### Post by mdt90 on 2011-09-26
> **Paqman said:**
> Open Office is probably a bit fat for you. Try Abiword for word processing, it's nice and light. I'm not too sure about lightweight presentation apps so I'll leave that to someone else.

abiword is bydefault available  with the lubuntu 10.04 version.can anyone suggest a lightweight application for presentation?

---

### Post by mörgæs on 2011-09-26
> **technosysind said:**
> Open Office 3.3.0 is good. U can download the 32-bit version :)

No, if you want OO, you should not download. It should be installed from a PPA.

This goes for (almost) all software in Ubuntu.

---

### Post by mdt90 on 2011-09-26
> **mörgæs said:**
> No, if you want OO, you should not download. It should be installed from a PPA.

This goes for (almost) all software in Ubuntu.

so what are the steps that i should take in order to install it from ppa?

---

### Post by RussianSoup on 2011-09-26
You meet the system requirements for LibreOffice, just like OO.o but without the corporate overbearing which defeats half the purpose of Linux. Might not be the best performance but it's easy to use and has a fully functional presentation program. As for installation, it should be available in the Ubuntu Software Center.

If you have to install it from the command line:

sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice

should do the trick.

---

