---
title: "Java Audio Player"
date: 2007-01-24
forum: Programming Talk
---

### Post by igknighted on 2007-01-24
Ok, so for my CSCI class (an intermediate Java class basically) we need to write a fairly substantial GUI program.  Our teacher has recommended cheesy games such as blackjack that I would never touch again after I left the class, so I want to do something that I might actually use (or continue to develop until it is more usable).  I am thinking of creating an Audio Player with a library and as many of the usual features as I can.  My problem is this: the professors in the department know very little about linux (as a general rule) and are not much help with the linux specific stuff.  How hard is it to use the gstreamer or xine backend with java, and am I biting off more than I can manage here?  I have (overall) a fairly light semester, so I can afford to put some serious time into this, but I would like to know before I start that this is realistic.  Thanks!

---

### Post by lnostdal on 2007-01-24
You could interface with a "headless" XMMS from your Java GUI as an option, I think.

---

### Post by rekahsoft on 2007-01-24
You could also write the everything that has to do with audio in C or C++ and use JNI so java cna use it :)

---

### Post by igknighted on 2007-01-24
Thanks for the suggestions.  I don't know C or C++ so I think using XMMS sounds more promising.

---

### Post by laxmanb on 2007-01-25
umm.. you can use java media framework... no programming knowledge in other languages necessary...

[http://java.sun.com/products/java-media/jmf/](http://java.sun.com/products/java-media/jmf/)

---

### Post by lnostdal on 2007-01-25
Nice; seems to support MP3 also. :)

---

### Post by igknighted on 2007-01-25
Thanks! That looks perfect!

---

### Post by Unterseeboot_234 on 2007-01-25
I've been picking at this one whenever I have the time. Linux, right now, you have to load up three packages and retime the kernel to make a soft-synthysizer. Otherwise, most of the answers to MIDI and sound editing pertain to dedicated hardware. I found that strange in light of the fact a java applet can play 5 sound formats using Java 1.2 and Java Media Foundation JMF API can play video and the sound in an app. java does much better playing MIDI than anything else I've tried. Java, also is most excellent at discovering peripherals.

If you write the editor to read/write MIDI please post on this forum. Linux NEEDS a studio suite. Ubuntu sez they'll have one by next April.

Java is supposed to pick the development back up on the Java Sound API. They sollicited input about the idea. Third party stuff out there like [**http://tritonus.org/**]("http://tritonus.org/") and the OpenSource project [**http://www.jsresources.org/**]("http://www.jsresources.org/") do a Google for even more stuff.

Just about everthing I've checked into is demo quality. No one has written an app that ties together some of these demos, like say a player with an equalizer and then edit, then burn a CD.

So, hey, I posted to this thread so I could watch this idea. Keep it going!!!!

---

