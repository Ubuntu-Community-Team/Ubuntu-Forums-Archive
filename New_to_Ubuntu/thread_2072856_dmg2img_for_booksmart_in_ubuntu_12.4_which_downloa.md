---
title: "dmg2img for booksmart in ubuntu 12.4 which download?"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-10-18
[https://help.ubuntu.com/community/DMG2IMG](https://help.ubuntu.com/community/DMG2IMG)

I want to install booksmart but don't know which dmg2img download I need to use?-Ubuntu 12.4 Thanks.

---

### Post by dgharmon on 2012-10-18
> **Jackalyn said:**
> I want to install booksmart but don't know which dmg2img download I need to use?-Ubuntu 12.4 Thanks.

Download the latest, compile and install from source ...

---

### Post by Jackalyn on 2012-10-19
> **dgharmon said:**
> Download the latest, compile and install from source ...
Thank you. I downloaded it  but am still having problems. Is this because to compile and install I need to do something else other than open the program? If so, what exactly do I do?

---

### Post by dgharmon on 2012-10-22
> **Jackalyn said:**
> Thank you. I downloaded it  but am still having problems. Is this because to compile and install I need to do something else other than open the program? If so, what exactly do I do?

**Install from source**

 The following assumes the latest version is 1.6.2, so check if a more recent version is available [here]("http://vu1tur.eu.org/tools/") first. To download, compile and install, open an terminal and type: 

wget [http://vu1tur.eu.org/tools/download.pl?dmg2img-1.6.2.tar.gz](http://vu1tur.eu.org/tools/download.pl?dmg2img-1.6.2.tar.gz) -O dmg2img-1.6.2.tar.gz

tar -xvf dmg2img-1.6.2.tar.gz

sudo apt-get install zlib1g-dev libssl-dev libbz2-dev

cd dmg2img-1.6.2

make

sudo make install

You can now remove the installation files if you want to tidy up: 

rm dmg2img-1.6.2.tar.gz rm -R dmg2img-1.6.2 
[B]
Getting Started With DMG2IMG[/B]

 You can now convert .dmg files to .img by typing: 

dmg2img filename.dmgThis will create a file called filename.img

---

