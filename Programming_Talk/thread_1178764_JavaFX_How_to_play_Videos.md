---
title: "JavaFX: How to play Videos?"
date: 2009-06-04
forum: Programming Talk
---

### Post by gantz on 2009-06-04
Hi guys,
JavaFX 1.2 is out now. It supports Linux and is an interesting alternative for Adobe and MS products.
My problem: it supports video through gstreamer, but it does not work on my machine. I am not advanced in linux multimedia, espacially gstreamer.
Does it work on your machine? Do you need to configure JavaFX or gstreamer and what?
regards
gantz

Eye candy: [http://javafx.com/samples/](http://javafx.com/samples/)
PS: I am not sure if this forum is the right place

---

### Post by cl333r on 2009-06-05
Although one can run to a degree JavaFX on Ubuntu, it is officially supported starting with v. 6 update 14 (beta quality). Now, the latest version Ubuntu ships with is v. 6 update 13, so I'd ask, are you sure you updated your Ubuntu Java stack to v. 6 update 14?
Otherwise it mostly doesn't work, especially the video.

---

### Post by froggyswamp on 2009-06-05
Regardless of what Sun says, JavaFX is still buggy and under heavy development: i.e. they broke compatibility in 1.2 with earlier versions.
Besides, JavaFX has serious architectural and dependency problems so I wouldn't use it to create something serious, not until it actually matures. Also, the guys at Sun (not all) still don't get it, i.e. Java/FX still likes asking permission questions even when there's no serious need for it - a good recipe for scaring away and/or boring your customers (see attachment)

Sun, as any other big corporation, is also a big liar, I remember them a year ago "demostrating" at JavaOne how JavaFX  can play "hundreds" of videos "easily", now that I look at the actual JavaFX video performance on windows/Linux - makes me laugh.
No need to give more examples, it's de facto a beta product, be it on windows or Linux.

---

### Post by gantz on 2009-06-05
> **cl333r said:**
> Although one can run to a degree JavaFX on Ubuntu, it is officially supported starting with v. 6 update 14 (beta quality). Now, the latest version Ubuntu ships with is v. 6 update 13, so I'd ask, are you sure you updated your Ubuntu Java stack to v. 6 update 14?
Otherwise it mostly doesn't work, especially the video.
I updated to 6u14 but no video plays (it does not play anything).  I get a  MediaUnsupportedException from the MediaCube Example. Maybe its gstreamer? I added codecs but nothing changed. Any ideas?

@froggyswamp:
I agree, JavaFX is still buggy and will be buggy in near future. I hope Orcale will promote JavaFX to get it fast stable on all OS. The interoperability between Java and JavaFX is the key issue. I would buy JFX Licenes instead of Adobe Flex if JFX is stable. BC I can develop very complex Applications (as pure Java backend) and exchangeble JavaFX UI without having complexity and performance problems eg. BlaseDS (a bridge between Java and Flex which needs Tomcat) by applying common Java Interfaces and a common JVM for Java and JavaFX.

---

### Post by jespdj on 2009-06-06
> **cl333r said:**
> Although one can run to a degree JavaFX on Ubuntu, it is officially supported starting with v. 6 update 14 (beta quality).
The [JavaFX SDK System Requirements page](http://java.sun.com/javafx/1/reference/system-requirements-1-2.html#javafxsdk) says:
> JDK 6 Update 13 minimum (JDK 6 Update 14 recommended)
So that sounds like Java 6 update 13 is also officially supported.

I have not been able to play video with JavaFX 1.2 on Ubuntu 9.04 (64-bit) either. I downloaded and installed the Netbeans 6.5.1 with JavaFX 1.2 SDK and created the MediaBox example, but when I run it, it just says "Sorry, this video can't be played now."

I also bought a book about JavaFX 1.2 at the JavaOne conference which I've visited this week, and there's a table in there that lists the audio and video codecs that are available in JavaFX 1.2 for different operating systems. For many video formats there is no codec for Linux yet.

I guess we'll have to wait until the next version of JavaFX, which should be out in about six months or so.

---

### Post by froggyswamp on 2009-06-06
On my computer I got both Jaunty 32 & 64 bit:
Video works on 32 bit (for me), I could find the plugin.
Video doesn't work on 64 bit (for me), and I couldn't find the plugin either.

Flash is not perfect either, the free version is a cut version, you can't use a lot of (GUI) classes. Flash (ActionScript 3) doesn't (even) support threads, so yes, I would agree that if I had to invest, I'd invest into Java hoping that the folks at Sun/Oracle start doing really good decisions (instead of adding another layer of complexity and inter dependency).
But right now if I had to do something for a site I'd use Flash.

What is also pissing me off is that Sun keeps adding to Java since 1996 without ever dropping any obsolete stuff, i.e. almost the whole java.awt package is long deprecated and forgotten but they still ship all the awt GUI classes with every JRE for the sake of those 2 awt applets left on the web from the 1996-2001 era.

---

### Post by bardu on 2009-06-07
> I have not been able to play video with JavaFX 1.2 on Ubuntu 9.04 (64-bit) either. I downloaded and installed the Netbeans 6.5.1 with JavaFX 1.2 SDK and created the MediaBox example, but when I run it, it just says "Sorry, this video can't be played now."
Same here. I have installed JDK 6 Update 14 as well as JRE 6 Update 14, but that didn't make a difference. The odd thing is that I could run the video examples from javafx.com prior JavaFX 1.2. 

> I also bought a book about JavaFX 1.2 at the JavaOne conference
Would you mind letting us know which book you bought?

---

