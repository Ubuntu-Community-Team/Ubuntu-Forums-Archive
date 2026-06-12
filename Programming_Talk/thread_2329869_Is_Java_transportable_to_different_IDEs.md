---
title: "Is Java transportable to different IDEs"
date: 2016-07-05
forum: Programming Talk
---

### Post by PopsTheSailor on 2016-07-05
Hi, I want to learn Java, JDBC, and mySQL. So that I don't spend a ton of time deciding which IDE is best, I'm just going to install Netbeans. I curious how much an IDE impacts the code you write. If I end up deciding that Netbeans isn't what I want / need, is it easy to install a different IDE and move on or will I spend a bunch of time updating libraries, drivers, or ??? I'm new to programming in an IDE so curious how much I will lock myself into any particular IDE.

I want to write my own desktop cookbook program to learn Java and JDBC with the additional benefit of learning JAVA since it's the most common language for mobile apps. I've definitely decided to learn Java so not looking to debate the language I choose, just the inner-workings of IDEs.

---

### Post by Rocket2DMn on 2016-07-06
The IDE has no impact on things like libraries and drivers.  It is a tool for actually writing and managing the code, compiling, debugging, and sometimes more advanced capabilities like deploying the application.  The only overhead of moving to a different IDE is getting the project configured in the new IDE so that it knows where the source code is, where dependent libraries are, and where to place compiled code (e.g. bin/ or target/).

Although I haven't switched Java IDEs for a very long time, if you're using a standard project structure (like those imposed by [Maven]("http://maven.apache.org/")), moving between IDEs should be fairly seamless so long as your app isn't horribly complex.

Different IDEs have plugins for mobile app development as well, particularly Android.  Android even provides its own IDE called Android Studio.

---

### Post by DaviesX on 2016-07-06
Netbeans is good. BTW, I can't imagine writing Java without an IDE. This languge loses much of its value if not pairing up with a powerful IDE. If you figure later on netbeans isn't good for you, you can always switch to any other IDE that has support for ANT build (ANT is the default tool underlies netbeans' build process). Or, if you are very concern about switching IDE, well, you can create a maven project in Netbeans. Maven is more common than ANT. Moreover, it handles dependencies amazingly. So, yeah, there is no barrier prevents you from making such choice. And I think Netbeans is pretty good for what you are trying do.

---

### Post by PopsTheSailor on 2016-07-06
Great info, very helpful. Thanks and I will mark this as solved.

---

