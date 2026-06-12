---
title: "How to ... run xyscan on ubuntu karmic"
date: 2009-11-25
forum: Outdated Tutorials &amp; Tips
---

### Post by crazy ivan on 2009-11-25
This useful scientific tool that extracts data points from plots found in publications is found at:

[http://star.physics.yale.edu/~ullrich/xyscanDistributionPage/](http://star.physics.yale.edu/~ullrich/xyscanDistributionPage/)

And since there is no .deb package yet we have to download the source an compile it.. Now you want to follow the standard procedure. Extract the source and change to the containing directory, there you type

```
 qmake -o Makefile xyscan.pro 
```

If this does not work, you need to

```
 sudo apt-get install qt4-qmake 
```

now all you have to do is type

```
 make 
```.

Now either you're done or you get something like:

```
 main.cpp:13:24: error: QApplication: No such file or directory 
```

This means your Qt is not yet complete (ly configured).. Getting these packages resolved the dependencies for me (most likely you don't need them all). 

```
 sudo apt-get install libqt4-core libqt4-dev libqt4-gui libqt4-qt3support libqt4-sql lsb-qt4 qt4-designer qt4-dev-tools qt4-doc qt4-qtconfig gcc libapt-pkg-perl resolvconf 
```

Usually you will have some qt-3 leftovers which will interfere, so you have to upgrade dependencies by hand:

```

sudo update-alternatives --config qmake
sudo update-alternatives --config uic
sudo update-alternatives --config designer
sudo update-alternatives --config assistant
sudo update-alternatives --config qtconfig
sudo update-alternatives --config moc
sudo update-alternatives --config lupdate
sudo update-alternatives --config lrelease
sudo update-alternatives --config linguist

``` 

Here you select the "qt4" version every time the program selects a conflict and confronts you with a dialogue. (Cf. [ https://help.ubuntu.com/community/BuildingQuantumGisPoint8FromSource]("https://help.ubuntu.com/community/BuildingQuantumGisPoint8FromSource")). You don't need the package 'uim-qt' which leads to heavier conflicts!!

Now the 'make' should work and you just run "./xyscan" to start working.. :-({|=

---

