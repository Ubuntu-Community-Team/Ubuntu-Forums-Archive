---
title: "Please make Sun java the default java installed not gcj"
date: 2009-05-07
forum: Programming Talk
---

### Post by gmatt on 2009-05-07
I've spent about an hour trying to figure out whats wrong with my program. It ended up being just that GCJ java's fault, but there is no way to quickly identify that GCJ is causing this, until I tried sun-java by the off chance and everything worked 100%. Here is a list of things the GCJ will screw up on:

-any less mainstream libraries like JMF, or JAI (both of which I am using for development)
-Eclipse debugging does not work at all with GCJ, all breakpoints set in eclipse will simply be ignored with no warning no nothing
-Eclipse works alright for the most part, but programs launched through Eclipse under GCJ run about 1000% slower than if run under sun-java.

In conclusion GCJ might be alright for the occasional Java user, but for the serious Java-dev GCJ is a pain in the butt. I would like some warning to be added to Ubunutu users that the current version of java installed is GCJ and will most likely not run properly with any Java development tools.

---

### Post by slavik on 2009-05-07
as we are not in charge of deciding, please file a bug in launchpad regarding this.

My guess is that you will be told no, due to possible licensing issues.

---

### Post by DocForbin on 2009-05-07
imo it would be preferable to not bundle anything than to bundle openjdk. Not sure but I think this is the way the desktop in 9.04 is (no java out of the box). But I know the 8.10 server edition comes with openjdk.

---

### Post by jespdj on 2009-05-08
Since 8.10, OpenJDK Java is the default Java on Ubuntu, not GCJ.

[OpenJDK Java](http://openjdk.java.net/) is good, it's more than 95% the same as Sun Java 6. OpenJDK is Sun's project to make their Java implemenation fully open source. They couldn't just make it open source like that, because they used some closed-source third party components. In the OpenJDK project, they are replacing those components with open source alternatives.

OpenJDK works well for most Java software, but it is not 100% compatible with Sun Java 6. At least it is far better than GNU Java, which is a slow, outdated and incomplete implementation of Java 1.4.

---

### Post by gmatt on 2009-05-09
> **jespdj said:**
> Since 8.10, OpenJDK Java is the default Java on Ubuntu, not GCJ.

[OpenJDK Java](http://openjdk.java.net/) is good, it's more than 95% the same as Sun Java 6. OpenJDK is Sun's project to make their Java implemenation fully open source. They couldn't just make it open source like that, because they used some closed-source third party components. In the OpenJDK project, they are replacing those components with open source alternatives.

OpenJDK works well for most Java software, but it is not 100% compatible with Sun Java 6. At least it is far better than GNU Java, which is a slow, outdated and incomplete implementation of Java 1.4.

Hey,

Thanks for the heads up. I don't know why I had GCJ installed on my system :S but GCJ really sucks. But you are right, OpenJDK is stellar on linux. I actually had to switch to it over Sun Java because there was a bug with drawing a BUfferedImage to a JFrame with Sun Java but when I switched to OpenJDK it worked fine. 


I think its good that OpenJDK is the default. It seems more stable and faster than Sun-java.

---

### Post by Reiger on 2009-05-09
> **gmatt said:**
> Hey,

Thanks for the heads up. I don't know why I had GCJ installed on my system :S but GCJ really sucks. But you are right, OpenJDK is stellar on linux. I actually had to switch to it over Sun Java because there was a bug with drawing a BUfferedImage to a JFrame with Sun Java but when I switched to OpenJDK it worked fine. 


I think its good that OpenJDK is the default. It seems more stable and faster than Sun-java.


The reason is [EDIT]**probably** that a lot of Java based apps still seem to be packaged/built against the GCJ. For example, the ever outdated eclipse (and various ant components) still, even on Karmic, lists the gcj-jre as its dependency.

Then again, it is still at version 3.2. Seems like the Ubuntu developers prefer Netbeans (which was up to date in Jaunty, albeit that one too depends on the GCJ).

---

### Post by DocForbin on 2009-05-09
> **gmatt said:**
> I think its good that OpenJDK is the default. It seems more stable and faster than Sun-java.
What makes you say this?

---

### Post by jespdj on 2009-05-10
> **Reiger said:**
> ... that a lot of Java based apps still seem to be packaged/built against the GCJ. For example, the ever outdated eclipse (and various ant components) still, even on Karmic, lists the gcj-jre as its dependency.
Eclipse in the Ubuntu repository is just old and does not seem to be maintained anymore. Eclipse doesn't even run properly with GCJ, so why it has gcj-jre as a dependency is a mystery, it's probably just wrong, because the person who made the Eclipse package in the Ubuntu repository didn't really know what (s)he was doing.... :rolleyes: It's better to download Eclipse from the [Eclipse website](http://www.eclipse.org) than to install it from the repos.

OpenJDK Java is not faster or more stable than Sun Java. As I said, it is 95% identical to Sun Java, with some proprietary parts replaced by open source parts. It works well, but is not 100% compatible with Sun Java, and some particularly picky applications don't work well with OpenJDK.

---

### Post by cl333r on 2009-05-10
> **gmatt said:**
> I've spent about an hour trying to figure out whats wrong with my program. It ended up being just that GCJ java's fault....

You are right 100%. That su#s, but ppl fear patents.
A mix of openjdk and icedtea is afaik already the default in 9.04 but it still causes a lot of problems.
OTOH ironically Mono is installed by default and in this case few ppl care that only Novell and "Novell's distribution channel" are safe from litigations.
Once again, it's about patents and stuff, though in some cases the threats are misteriously being discarded and ppl who make decisions vehemently suggest there's no patents problems at all or that "we can't endlessly fear them".
(Under the hood) it's also about stuff not permitted to talk about, so I don't think there's anything gonna change anytime soon, not at least until jdk 7 is released which promises to be what the GPLed Java was supposed to be.

---

### Post by Reiger on 2009-05-10
> **jespdj said:**
> Eclipse in the Ubuntu repository is just old and does not seem to be maintained anymore. Eclipse doesn't even run properly with GCJ, so why it has gcj-jre as a dependency is a mystery, it's probably just wrong, because the person who made the Eclipse package in the Ubuntu repository didn't really know what (s)he was doing.... :rolleyes: It's better to download Eclipse from the [Eclipse website](http://www.eclipse.org) than to install it from the repos.


Yeah, that's what I do. Just used eclipse to illustrate my point about dependencies not being updated to reflect the new Java choice.

---

### Post by directhex on 2009-05-10
1) There's not enough room, as OpenJDK is huge
2) There's no support for many architectures

Those are reasons holding back OpenJDK from being part of the default install, no matter how desirable.

And before anyone says it, Mono+F-Spot+Tomboy combined still only account for half the size of OpenJDK+noapps, so no, that would't help.

---

### Post by Reiger on 2009-05-10
Well yes, but are there actually any Java apps in a core installation of Ubuntu? IIRC Java is simply not shipped by default, only through the repositories. And if there are no apps in the core installation there's no reason to keep the GCJ for dependencies' sake. ...

---

### Post by gmatt on 2009-05-11
> **jespdj said:**
> 
OpenJDK Java is not faster or more stable than Sun Java. As I said, it is 95% identical to Sun Java, with some proprietary parts replaced by open source parts. It works well, but is not 100% compatible with Sun Java, and some particularly picky applications don't work well with OpenJDK.

Yea I can't say that OpenJDK is faster, I've done some very informal benchmarking with just running my program with both Sun and OpenJDK and thought OpenJDK performed better but it could just be the circumstances.


I can say though from experience, that OpenJDK is MORE stable under linux than SunJava in the specific case of drawing a BufferedImage to a JFrame. When I attempt this simple action in SunJava I get a fatal bug that crashes the entire application. When I use OpenJDK it runs fine. It could be my particular setup (I'm running the app through eclipse) or not, I can't say, I can't be bothered to test it more extensively. But you are welcome to.

---

