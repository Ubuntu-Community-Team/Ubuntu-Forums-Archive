---
title: "sun-java6-jdk vs. openjdk-6-jdk"
date: 2009-05-01
forum: Programming Talk
---

### Post by sefs on 2009-05-01
Is the openjdk now the way forward.  I currently have sun-java6-jdk.  I just wanted clarification that the openjdk is now the offical install from here on out for the java programming language.

Thanks.

---

### Post by jespdj on 2009-05-02
The best version of Java to use at the moment is Sun Java 6.

[OpenJDK](http://openjdk.java.net/) is Sun's project to make their Java implementation fully open source. The next version of Sun Java (Sun Java 7, expected no sooner than March 2010) is going to be based on OpenJDK.

The version of OpenJDK that's in the Ubuntu repository is a Sun Java 6-compatible version of OpenJDK; it's basically the same as Sun Java 6, but with some proprietary parts (that Sun didn't write themselves) replaced by open source software (parts of the font rendering, graphics and sound stuff).

For the most part, OpenJDK works well with most Java applications, but unfortunately it is not 100% compatible with Sun Java 6, which causes problems with some Java programs, especially some online banking Java applets.

For Java software development, it really doesn't matter if you take the Sun JDK or the OpenJDK JDK, because the APIs are exactly the same. Just the implementation is different.

---

### Post by drubin on 2009-05-02
> **jespdj said:**
> For Java software development, it really doesn't matter if you take the Sun JDK or the OpenJDK JDK, because the APIs are exactly the same. Just the implementation is different.

Generally that is ok even more so with cli applications. For Gui I would recommend not using the openjdk thee have been quite a few threads on this forum about users having issues with openjdk and swing. (mostly with alignment and look).

But generally if you code for openjdk and run your app on only openjdk it should be ok.

---

### Post by sefs on 2009-05-02
Thanks, I just tested it and realise that a swing app I have here displays a bit differently in truth, not as neat as the sun distribution.

---

### Post by eye208 on 2009-05-02
> **sefs said:**
> Thanks, I just tested it and realise that a swing app I have here displays a bit differently in truth, not as neat as the sun distribution.
Make sure to install the Lucida TrueType font. This has been the default font in Swing applications until OpenJDK. It is missing in the OpenJDK package but available separately.

---

### Post by krazyd on 2009-05-02
Some apps don't work at all with openjdk. Eg. BlueJ.

---

### Post by jespdj on 2009-05-02
> **eye208 said:**
> Make sure to install the Lucida TrueType font.
There's a package named **sun-java6-fonts** which will install fonts for Sun Java 6.

---

### Post by eye208 on 2009-05-02
> **jespdj said:**
> There's a package named **sun-java6-fonts** which will install fonts for Sun Java 6.
Yes, but if you install that, **sun-java6-jre** will be installed, too. That doesn't make much sense if you want to use OpenJDK anyway.

---

### Post by motapa on 2010-11-07
Thanks a lot guys, you have answered all the question I had on choosing a java platform. I am a student of java and was really worried which path to choose, especially since i am running ubuntu, and its default java environment is open jdk. But your comments cleared everything out for me.

For learning purposes, i think the default jdk will fit just fine for me.

---

