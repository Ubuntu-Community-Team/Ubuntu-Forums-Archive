---
title: "Java Console GUI"
date: 2007-02-06
forum: Programming Talk
---

### Post by BatteryCell on 2007-02-06
Hey everyone, I recently found the need to program a gui in Java but only for terminal, so like it only uses the terminal to do its gui, no actual screen or anything.  However, I cannot for the life of me find any examples of how to create a gui in the terminal in java.  All it would need to do is show the movement of something.  

Thanks a bunch !
Joe

---

### Post by Tomosaur on 2007-02-06
I don't know of a way to do this using strictly Java code. You may want to read up on ncurses and see if that suits you, but I'm unaware of a Java library for it.

There **is** a way to format standard output so that it is coloured, but this is _terminal specific_ rather than being native to Java. I'm not too familiar with how it's done though.

---

### Post by phossal on 2007-02-06
I checked the web and found a bunch of hits. I've never used it, but check out this site on Mustang's Console API: [http://www.javalobby.org/java/forums/t53213.html](http://www.javalobby.org/java/forums/t53213.html)


> If a console is available, then "System.console" is non-null (it may be null if you launch your application from your IDE or on certain platforms). You can in particular use "Console.printf", "Console.readLine", and "Console.readPassword", so **it's a simple yet very useful API for certain console applications and administration tools.** As stated in the weblog referenced below, **this feature has been one of Java's top 25 RFEs (Requests For Enhancements) for a very long time.**

Another point worth mentioning: I tried this out, and found that the implementation seemed to solve another annoying problem experienced by users in locales where the character set of the console included non-ASCII characters (on Windows at least): unlike "System.out", printing to the console "System.console" automatically gets the character encoding correct.

You could work around the above issue by wrapping "System.out" with an OutputStreamWriter and the correct character set, but this wasn't easy to guess: System.getProperty("file.encoding") is not guaranteed to be provided and may be misleading, especially on Windows where (in France for example), Windows applications use "Cp1252" as the encoding and MSDOS applications use "Cp850"), so "translated" console apps are often difficult to read in non-ASCII locales due to mismatched encodings.

It's not a curses-style library, which would have been nice-to-have, but at least it's provided some solutions to really-very-important-to-have problems. 

---

### Post by tzulberti on 2007-02-06
Comment: the link that phossal passed would only work in java1.6 (it is already included).
Nevertheless, if you wish to use the conio.h functions of C, link gotoxy, clrcls, etc..., you should look for information about JNI... This has the problem, that your program would only run in Windows...

---

### Post by phossal on 2007-02-06
> **tzulberti said:**
> Comment: **the link that phossal passed would only work in java1.6** (it is already included).
Nevertheless, if you wish to use the conio.h functions of C, link gotoxy, clrcls, etc..., you should look for information about JNI... This has the problem, that your program would only run in Windows...

A *console app* doesn't seem like the kind of thing that would be so widely distributed that upgrading your box to JDK 6 would be the deal breaker. I've had it on my Ubuntu machines since the day it was available, and my Windows machines within a week of its release.

Besides, there were other links to private libraries on Google, I just figured I'd pass a link to the one at the top, considering it's a part of (what I already consider) the *default* Java.

---

### Post by BatteryCell on 2007-02-15
Thanks but after spending a good day trying to get jcurses working I just did it in c.  Thank god for curses eh :-)  

Thanks for the help

---

