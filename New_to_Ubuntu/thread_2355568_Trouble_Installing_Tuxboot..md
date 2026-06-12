---
title: "Trouble Installing Tuxboot."
date: 2017-03-14
forum: New to Ubuntu
---

### Post by joachimj on 2017-03-14
Hello there,I'm new to Ubuntu and I'm having a difficult time trying to install [Tuxboot]("http://tuxboot.org/download/").I have downloaded a .tar.gz file which I managed to extract using ```
tar -xzf [filename]
```and now I'm looking at a folder called tuxboot-0.6 sitting on my desktop but I can't figure out how to actually install it. I'd really appreciate any help.Many thanks,Julian

---

### Post by Perfect Storm on 2017-03-14
It says you can do this if you're ubuntu users:
```
sudo apt-add-repository ppa:thomas.tsai/ubuntu-tuxboot
sudo apt-get update
sudo apt-get install tuxboot
sudo tuxboot
```

---

### Post by joachimj on 2017-03-14
Yes, I tried that but when I ran sudo tuxboot it fails to load properly. I just got a small white box appearing. I forgot to mention I'm running Ubuntu 14.04 LTS with Unity

---

### Post by Perfect Storm on 2017-03-14
So you want to compile it from the source, why not taking version 0.8?
This shown with version 0.6 but can modify it to version 0.8 also it haven't been updated since 2014 so it may not work:
You need to install qmake for this and properly some more we can take it when it comes.

```

sudo apt install qt4-qmake libqt4-dev
cd ~/Downloads
tar xf tuxboot-0.6.src.tar.gz
cd tuxboot-0.6
./INSTALL
make
sudo make install
```

---

### Post by joachimj on 2017-03-14
Thanks for this. I think an error occurred when using ./install. This is the output I get in terminal.


 Generated 85 translation(s) (82 finished and 3 unfinished)
    Ignored 21 untranslated source text(s)
g++ -c -m64 -pipe -O2 -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -D_REENTRANT -DNOSTATIC -DCLONEZILLA -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o main.o main.cpp
make: g++: Command not found
make: *** [main.o] Error 127

---

### Post by Perfect Storm on 2017-03-14
You properly need some basic compiling tool install.
```
sudo apt install build-essential
```

then try again.

---

### Post by joachimj on 2017-03-14
Thanks very much. The installation looked much more promising but at make and then sudo make install nothing happens I get this: make: Nothing to be done for `first'.(trusty)julian@localhost:~/Downloads/tuxboot-0.6$ sudo make install
make: Nothing to be done for `install'.

---

### Post by Perfect Storm on 2017-03-15
Then look in folder, there must be a file/bin to start the program with.

---

