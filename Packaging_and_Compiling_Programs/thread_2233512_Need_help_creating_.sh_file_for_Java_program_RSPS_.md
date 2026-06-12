---
title: "Need help creating .sh file for Java program RSPS r474 (Runescape Private Server)"
date: 2014-07-09
forum: Packaging and Compiling Programs
---

### Post by hexer2 on 2014-07-09
Hi,

Sorry if I posted in wrong place, wasn't quite sure of where to post this.

I have been been creating a Runescape Private Server as a learning project, I have been using Windows Vista to do this. But I think my time would be best spent developing it on linux. I have been using Ubuntu for a number of years now but have never learnt how to write a .sh file for a java program.

The .bat file that I was using in windows reads:

@echo off
title Acquittal
java -Xmx1500m -cp bin;deps/poi.jar;deps/mysql.jar;deps/RuneTopListV2.jar;deps/GTLVote.jar;deps/mina.jar;deps/slf4j.jar;deps/slf4j-nop.jar;deps/jython.jar;log4j-1.2.15.jar; server.Server
pause

My "java -version" out put in the terminal is:

unknown@unknown-access-point:~$ java -version
java version "1.7.0_60"
Java(TM) SE Runtime Environment (build 1.7.0_60-b19)
Java HotSpot(TM) Server VM (build 24.60-b09, mixed mode)

And for the RSPS client .bat file

@echo off
title Client
java -cp . -Xmx300m client 10 0 highmem members 32
pause

I am wanting to know how to write a .sh file so that I can run this java program in ubuntu

Any help would be much appreciated,

Thanks

---

### Post by hexer2 on 2014-07-10
Posted in bad place, don't know how to delete post sorry. But my problem was solved

[http://ubuntuforums.org/showthread.php?t=2233529](http://ubuntuforums.org/showthread.php?t=2233529)

---

