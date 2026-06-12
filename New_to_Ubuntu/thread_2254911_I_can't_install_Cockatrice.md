---
title: "I can't install Cockatrice"
date: 2014-11-30
forum: New to Ubuntu
---

### Post by derek28 on 2014-11-30
I'm using 14.04 (64 bit) on an Acer laptop. 

Cockatrice is an open source card-game program, widely used to test Magic: The Gathering cards before buying them. You can find the download links/servers/forums at [www.woogerworks.com](www.woogerworks.com). 

I know I ran the apt-get but I don't know where to go next. 

Help would be appreciated! I don't know much about computers in general but I'm a fan of anything open source and Ubuntu is great, I'm just bad at using it.

---

### Post by Bucky Ball on 2014-11-30
This is the advice it gives on the website re. installing the client on Ubuntu:

> 
You can compile cockatrice manually following the instructions in the README after installing the dependencies.

Install dependencies for the Qt4 version with [U]sudo apt-get install build-essential g++ qtmobility-dev libprotobuf-dev protobuf-compiler libqt4-dev
[/U]
On Ubuntu precise you will need a PPA for the Qt5 and cmake packages, _sudo add-apt-repository ppa:ubuntu-sdk-team/ppa && apt-get update_.

The dependencies for Qt5 on ubuntu are libprotobuf-dev protobuf-compiler qtbase5-dev qtdeclarative5-dev libqt5webkit5-dev libsqlite3-dev qt5-default qttools5-dev-tools qttools5-dev qtmultimedia5-dev libqt5svg5-dev cmake You need cmake >= 2.8.9 in order to compile with Qt5.

You give very little detail, so which part of the process exactly are you having problems with?

---

### Post by derek28 on 2014-12-01
I can't find the README or the 'trice files at all; I don't know what  dependencies are; I'm not completely sure what compiling means. Can you  let me know where the README can be found? I appologize for my  ignorance, I'm trying to learn :/

---

### Post by derek28 on 2014-12-02
"the source directory does not appear to contain cmakelists.txt" is what I get when I enter "cmake .."

---

