---
title: "Adding data to linker command line"
date: 2011-06-07
forum: Programming Talk
---

### Post by akshay.sulakhe on 2011-06-07
Hello friends,
              I am doing programming in Ariba,which is a part of spovnet(spontaneous virtual network). My desktop runs fedora 15 X64. I am getting this error at make. Can anyone tell me what it is about. Pastebin link is:- [http://pastebin.com/McrraLps](http://pastebin.com/McrraLps)   .It has stopped all my work,kindly help. Thanks.

---

### Post by dwhitney67 on 2011-06-07
I do not personally waste time with an IDE for C++ (or C) development, but I see the problem you are having with the Makefile.

You need to indicate that you want your application linked with the libboost_system.so library.  Somewhere, somehow, you need to ensure that the Makefile has it's LDFLAGS defined as follows:
```

LDFLAGS += -lboost_system

```


P.S.  Why in pray-tell are you building your application as root?

---

### Post by akshay.sulakhe on 2011-06-07
Yeah..i know i am compiling as root,with normal user,it is denying some permissions to open a thread...so need to use root...where should i add that line,in make file???

---

### Post by dwhitney67 on 2011-06-07
> **akshay.sulakhe said:**
> Yeah..i know i am compiling as root,with normal user,it is denying some permissions to open a thread...so need to use root...where should i add that line,in make file???

Please state which IDE you are using; perhaps someone can help you.  Or you can read the documentation to determine how to add library dependencies.  My previous post indicates that you need to add the following library:  "boost_system".

I've done multi-threaded programming before; I did not need to be root to compile the application, much less be root to run it.

---

### Post by akshay.sulakhe on 2011-06-07
@dwhitney67 :- no IDE..m using KATE.nothing else.i am using ariba,part of spovnet. Can u tell me where exactly i should add the line??

---

### Post by akshay.sulakhe on 2011-06-07
Link for the program.

[http://ariba-underlay.org/wiki/Documentation/Tutorial/PingPong](http://ariba-underlay.org/wiki/Documentation/Tutorial/PingPong)

---

### Post by tjwilli on 2011-06-07
It's been a few years since I've used Makefiles, but yes, I think you need to add the ld argument in the makefile. Did you do a ./configure to generate the Makefile?

---

### Post by dwhitney67 on 2011-06-08
> **akshay.sulakhe said:**
> @dwhitney67 :- no IDE..m using KATE.nothing else.i am using ariba,part of spovnet. Can u tell me where exactly i should add the line??

Edit the Makefile such that you add "-lboost_system" at the appropriate place.  Typically libraries are associated with LDFLAGS.

If you examine the following statement (step 8 from your pastebin post), you will notice that a few of libraries are being included ("-lariba", "-lssl", and "-lgmp"):
```

/bin/sh ../../libtool --tag=CXX   --mode=link g++  -g -O2 -L../../source/ariba -lariba    -o pingpong pingpong-PingPongMessage.o pingpong-PingPong.o pingpong-main.o  -lssl -lgmp

```
Find out in the Makefile where "-lssl" and "-lgmp" are specified, and append "-lboost_system".

P.S.  Did you develop the Makefile, or was it created using a "configure" script?  If the latter, you need to tell the configure script what additional libraries to include into your Makefile.

---

