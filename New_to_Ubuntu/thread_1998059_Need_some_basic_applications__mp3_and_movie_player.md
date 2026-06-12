---
title: "Need some basic applications : mp3 and movie player."
date: 2012-06-06
forum: New to Ubuntu
---

### Post by vinodm on 2012-06-06
Hello members , I am new to this forum and ubuntu , I installed ubuntu 12.4 LTS and liked it. But I want to play music and movies but it says no plugin . Please suggest some good mp3 and movie player for ubuntu. I also need a good pdf reader and a movie maker. 

:guitar:
Thank you
Vinod M

---

### Post by Megaptera on 2012-06-06
Have you installed Ubuntu-restricted-extras?

Full explanation here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
"Follow these steps to play and record most common multimedia formats, including MP3, DVD, Flash, Quicktime, WMA and WMV, including both standalone files and content embedded in web pages."

---

### Post by z3nhakr on 2012-06-06
which version of Ubuntu are you using?
Ubuntu should have out of the box support for PDF files. In 11.10 it is a repackaged version of evince called Document Viewer. I think it's the same in 12.04. As far as mp3s and media files go, the restricted extras package should add support for these files to almost any media applications because it is a shared library, therefor you can use totem, vlc, banshee, or whatever suites you best.

---

### Post by oklokl on 2012-06-06
[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")
sudo add-apt-repository ppa:nilarimogard/webupd8    ## player  audacious    [https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

audacious
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4C9D234C ## webupd8
sudo sh -c 'echo "deb  http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main"  >> \/etc/apt/sources.list.d/webupd.list'
sudo apt-get update && sudo apt-get install audacious
```

my favorite player
I do not know the PDF.

---

### Post by z3nhakr on 2012-06-06
> **oklokl said:**
> [https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")
sudo add-apt-repository ppa:nilarimogard/webupd8    ## player  audacious    [https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

audacious
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4C9D234C ## webupd8
sudo sh -c 'echo "deb  http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main"  >> \/etc/apt/sources.list.d/webupd.list'
sudo apt-get update && sudo apt-get install audacious
```

my favorite player
I do not know the PDF.
the applications in this repo are available in software center. it is a LOT easier to use and also eliminates the need to add a repository.

---

### Post by oklokl on 2012-06-06
Can be run at once, a variety of ...
[http://cafe.daum.net/candan/HgwY/76](http://cafe.daum.net/candan/HgwY/76)
my home.. n,.n..

---

### Post by vinodm on 2012-06-06
Thank you all  :) :KS

---

### Post by mastablasta on 2012-06-06
> **vinodm said:**
>  I also need a good pdf reader and a movie maker. 

 
Plenty of PDF readers in Linux including Adobe Acrobat Reader. [http://www.adobe.com/support/downloads/product.jsp?product=10&platform=Unix](http://www.adobe.com/support/downloads/product.jsp?product=10&platform=Unix)
 
Evince, Okular and Epdfview to name only a few.
 
Libre office Draw can import PDF, so you can edit it. But you need to install the PDF importer plugin from software center.
 
Movie maker - a good one is Kdenlive
 
Movie player - VLC is one of the best, but you also have some others available (such as for example Totem, Xine, Mplayer and similar).
 
MP3 player - uff these come in many forms, shapes and sizes. Default one is Rythmbox, then there is Banshee, Amarok, Clementine and if your collections is really big then maybe Guayadeque ... Audacious was already mentioned. And i am sure there are plenty others out there. just browse the software center a bit.

---

### Post by d4m1r on 2012-06-06
I am worried about your 12.04 Ubuntu install....The default installer (if you downloaded the official ISO's) installs a mp3 player, a movie player, AND a pdf view all by default...

You shouldn't have had to install anything extra...

---

### Post by philinux on 2012-06-06
> **d4m1r said:**
> I am worried about your 12.04 Ubuntu install....The default installer (if you downloaded the official ISO's) installs a mp3 player, a movie player, AND a pdf view all by default...



But not the codecs unless you tick the extras box.

---

