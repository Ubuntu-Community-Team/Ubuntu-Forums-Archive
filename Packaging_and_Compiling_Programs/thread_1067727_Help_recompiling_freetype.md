---
title: "Help recompiling freetype"
date: 2009-02-12
forum: Packaging and Compiling Programs
---

### Post by JuanChanKane on 2009-02-12
Hi there, 

I am trying to recompile freetype2 from source, with a small change.

I downloaded the file from [here]("https://launchpad.net/ubuntu/intrepid/+source/freetype/2.3.7-2ubuntu1"), and inserted the desired change: edited file /freetype-2.3.7/include/freetype/config/ftoption.h
and uncommented the line which I want to change:

/* #define TT_CONFIG_OPTION_BYTECODE_INTERPRETER */

So I got the source package extracted and edited...I installed the “build-essentials” one. So how should I proceed now in order to recompile and get this installed?

I was about to try this, but not sure if it will work under ubuntu 8.10

./configure
make
sudo make install
clean install

---

