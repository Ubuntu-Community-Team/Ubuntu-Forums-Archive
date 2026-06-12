---
title: "problem to compile under Angstrom"
date: 2012-03-23
forum: Programming Talk
---

### Post by Jean-Claude Tergal on 2012-03-23
Hi guys !
  I’ve got a mini netbook with a wm8650 processor.
  I’ve install an Angstrom distro on the SD card.
   
  It works fine but I’ve got a problem to install a new program.
  I will use this netbook only to play chess.
   
  So I tried to install Dreamchess.
   
  Angstrom use the opkg package manager and the program librairy seems to be tiny.
   
  So I tried to compile Dreamchess.
   
  When I execute ./configure, I’ve got the message 

```
No acceptable C compiler found in $PATH
```  So I tried ```
opkg install gcc
``` and ```
opkg install cpp
``` but the ./configure script returns the same message…
   
  So I tried ```
$opkg install task-native-sdk
```. It return ```
can’t resolve dependency : INETUTILS
``` INETUTILS don’t exist in Angtrom repository, so I dont know what to do…
   
  Has anybody an idea please ?
  Thank you.

---

