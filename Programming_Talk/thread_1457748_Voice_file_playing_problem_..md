---
title: "Voice file playing problem ."
date: 2010-04-19
forum: Programming Talk
---

### Post by leslie samuel on 2010-04-19
We are doing the  project  called player. 
In this we have tried to play actual call and its related calls ( in and out voice   separately, It means we plan to play 5 calls at a time[related calls])
But we can play 4 stream at a time( 2 calls), but if it reaches more then 4 its throwing below error.

In this we are using JMF and tomcat server.

Error:
=====

        Unable to handle format: LINEAR, 8000.0 Hz, 16-bit, Mono, LittleEndian, Signed, 16000.0 frame rate, FrameSize=16 bits
Failed to prefetch: com.sun.media.PlaybackEngine@1a998c7
  Unable to handle format: LINEAR, 8000.0 Hz, 16-bit, Mono, LittleEndian, Signed, 16000.0 frame rate, FrameSize=16 bits
Failed to prefetch: com.sun.media.PlaybackEngine@484c6b
Error: Unable to prefetch com.sun.media.PlaybackEngine@484c6b

JFM Error event com.sun.media.content.unknown.Handler@913c56
Error: Unable to prefetch com.sun.media.content.unknown.Handler@913c56

JFM Error event com.sun.media.content.unknown.Handler@5db9eb


Environment:
==========

    OS => GNU/Linux
    kernal name => linux
    kernal release => 2.6.31-16-386
    kernal version => #53-Ubuntu SMP Tue Dec 8 06:39:34 UTC 2009

     Jdk version => jdk1.5.0_10
     Jre version => jre1.6.0_18
     JMF version => JMF-2.1.1e
     tomcat server => tomact5.5

firefox => Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.19) Gecko/20081203 Firefox/2.0.0.19

We don't know why this problem is coming. please give some solution.

---

