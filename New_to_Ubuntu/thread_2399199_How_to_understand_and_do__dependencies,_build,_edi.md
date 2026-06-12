---
title: "How to understand and do:  dependencies, build, edit, pro, qmake, etc"
date: 2018-08-22
forum: New to Ubuntu
---

### Post by mysticmuse2 on 2018-08-22
New Ubuntu user trying to do install the program here:

  	 	 	 	   [URL="https://github.com/OneMoreGres/ScreenTranslator"]https://github.com/OneMoreGres/ScreenTranslator
[/URL]

 
 
 [B]Instruction says:
Linux[/B]: install dependencies and build from source (edit .pro, qmake && make). Also download [data files]("https://github.com/tesseract-ocr/tessdata/tree/3.04.00") for tesseract.



[LIST]
[*]How do I install  dependencies?
[*]How do I build from a source?
[*]How do I do " (edit .pro, qmake && make)"
[/LIST]

---

### Post by TheFu on 2018-08-22
Scroll to the bottom of that page ...
> Dependencies

    see Qt 5
    see Tesseract
    see Leptonica
    several online translation services

There are links trying to explain.

But installing something this complex using C/C++ and make is a huge effort for non-programmers.

---

### Post by Yellow Pasque on 2018-08-25
Start by getting the dependencies. Note that this may be an incomplete list as my system may have already had some dependencies:
```
sudo apt-get install git build-essential qt5-qmake libtesseract-dev libleptonica-dev libxcb-util-dev libqt5x11extras5-dev libqt5webkit5-dev fakeroot debhelper
```

You will also need the tesseract packages for the specific languages you wish to use. For example, this will install the English package:
```
sudo apt-get install tesseract-ocr-eng
```
There is a nice list here: [https://packages.ubuntu.com/bionic/tesseract-ocr-all](https://packages.ubuntu.com/bionic/tesseract-ocr-all)

Then it's time to build. This worked for me:
```
cd ~/
mkdir source
cd source/
git clone https://github.com/OneMoreGres/ScreenTranslator.git
cd ScreenTranslator/scripts/
./make_all.sh
cd ~/source/build/linux/
sudo dpkg -i screen-translator-2.0.2-15.04.deb
```

---

