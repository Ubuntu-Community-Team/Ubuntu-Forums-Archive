---
title: "HOWTO: Install Opera"
date: 2006-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by kebabtomten on 2006-02-04
I will now explain how to install Opera-8,51 on your Ubuntu Breezy Badger computer. 

First we need to get the Opera package:

wget http://www.opera.com/download/get.pl?id=27525&location=14&nothanks=yes&sub=marine

The install the package:

sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb

So now can you open an terminal and type opera and it will start. But you maybe whant an shourtcut so we do that:

Download the Opera icon:

wget http://promote.opera.com/logos/Opera3.jpg

Then:

sudo gedit /usr/share/applications/opera.desktop

And paste this into:

[Desktop Entry]
Name=Opera
Comment=Opera
Exec=/usr/bin/opera
Icon=/home/filip/.opera/Opera3.jpg
Terminal=false
Type=Application
Categories=Application;Network;

Note: Icon=/home/filip/.opera/Opera3.jpg is where i put my Opera3.jpg!

Now can you start Opera from Application-->Network-->Opera.

I did not find any Opera howto but it maybe exist.  And i am not very good at English so if i have spell something wrong tell me that.

---

### Post by zenwhen on 2006-02-04
There is a sufficient howto on this subject already.

---

### Post by zenwhen on 2006-02-04
There is a sufficient howto on this subject already.

[http://ubuntuforums.org/showthread.php?t=78468&highlight=opera](http://ubuntuforums.org/showthread.php?t=78468&highlight=opera)

---

