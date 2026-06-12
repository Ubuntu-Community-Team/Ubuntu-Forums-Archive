---
title: "Is java (and thus Eclipse) REALLY slow on intrepid?"
date: 2008-10-02
forum: Programming Talk
---

### Post by Luke has no name on 2008-10-02
Every time Eclipse closed a comment or loaded a lib (by closing the carat >) the program froze for about 10 seconds. It got really annoying really quickly.

---

### Post by dwhitney67 on 2008-10-02
I have never known Eclipse to run "slow"; I've known it to be difficult to configure/use, but never slow.  Of course, I have not used it in over 3 years, so the application could have degraded (with updates) during that period.

---

### Post by Reiger on 2008-10-02
Yes, I've found Eclipse to run much better (and Java (apps) in general) under Windows.

---

### Post by jespdj on 2008-10-02
> **Reiger said:**
> Yes, I've found Eclipse to run much better (and Java (apps) in general) under Windows.
It depends on what Java version you are using. Don't use the old GNU Java (gcj) stuff, it's outdated, incomplete and slow.

Use OpenJDK or Sun Java - they run just as fast and smooth as on Windows.

> **Luke has no name said:**
> Every time Eclipse closed a comment or loaded a lib (by closing the carat >) the program froze for about 10 seconds. It got really annoying really quickly.
I've noticed this in the latest version of Eclipse (3.4), especially when editing JavaScript files. But it's not an Ubuntu problem, because it happens also on Windows. I have the feeling that especially the WTP (Web Tools Platform) stuff in Eclipse 3.4 is buggy and unstable.

---

### Post by xlinuks on 2008-10-02
> **Reiger said:**
> Yes, I've found Eclipse to run much better (and Java (apps) in general) under Windows.

The graphics in Java and Flash run faster on Windows like twice or more because their companies care a lot more about windows, which is understandable.

---

### Post by xlinuks on 2008-10-02
> **jespdj said:**
> It depends on what Java version you are using. Don't use the old GNU Java (gcj) stuff, it's outdated, incomplete and slow.

Use OpenJDK or Sun Java - they run just as fast and smooth as on Windows.


I've noticed this in the latest version of Eclipse (3.4), especially when editing JavaScript files. But it's not an Ubuntu problem, because it happens also on Windows. I have the feeling that especially the WTP (Web Tools Platform) stuff in Eclipse 3.4 is buggy and unstable.

Once again, the Java graphics on windows runs faster than on Linux. There's more bitter news, the Java 6 update 10 will feature swing fully 3D accelerated, but _only_ on window$, thus window$ will get another Java graphics speed/usability boost, Linux has been overseen allegedly because the video drivers are too unstable or change over time too much (can't remember the exact answer), that's what I've been told on a sun forum.
I tested myself the 2D graphics performance of Java 6 update 10 (RC) on windows and Linux, and I can tell you on windows its waaay faster.

---

### Post by Asham on 2008-10-18
> **xlinuks said:**
> Once again, the Java graphics on windows runs faster than on Linux. There's more bitter news, the Java 6 update 10 will feature swing fully 3D accelerated, but _only_ on window$, thus window$ will get another Java graphics speed/usability boost, Linux has been overseen allegedly because the video drivers are too unstable or change over time too much (can't remember the exact answer), that's what I've been told on a sun forum.
I tested myself the 2D graphics performance of Java 6 update 10 (RC) on windows and Linux, and I can tell you on windows its waaay faster.

I was hoping for a Java performance boost in Linux when Java joined the OSS world. Aw, this sucks. :(

---

### Post by Shin_Gouki2501 on 2008-10-18
Its jsut incredebile how much pain , frusttration and misinformation is constructed by the whole "gjc" is created.


It't hard enough to fight these outdated opinions like : java is slow.
(which coems from over 10 years old java...)

Eclipse runs fine here , as java does, on my mac and my gf's ubuntu box.

---

### Post by cl333r on 2008-10-18
> **Shin_Gouki2501 said:**
> Its jsut incredebile how much pain , frusttration and misinformation is constructed by the whole "gjc" is created.


It't hard enough to fight these outdated opinions like : java is slow.
(which coems from over 10 years old java...)

Eclipse runs fine here , as java does, on my mac and my gf's ubuntu box.

"gcj" has indeed messed things up and added to the impression that java is slow, but make no mistake, Sun's Java runtime for Linux is (sometimes considerably) slower than Sun's Window$ implementation. Java 6 update 10 has just been released and now on window$ on nvidia and ati cards (intel not supported) all Java 2D/Swing is hardware accelerated, I tested it, feels cool. Linux, Solaris, whatever, are unfortunately left out so far. As we reach some 5-10% market share I bet Sun will try and (help) implement the same features for Linux despite having bad video drivers.

---

### Post by Reiger on 2008-10-18
Well Java in and of itself is not slow (on Ubuntu), however it is not quite as fast as Java on Windows is. You'll notice with large scale projects & apps such as Eclipse; and funny thing is that it doesn't hang on the GUI but it lags hard on the autocompletion & suggestions bits.

And don't mention the gcj: I've ditched that soon as I had my wireless up and running. ;)

---

### Post by nvteighen on 2008-10-18
btw, if Solaris is Sun's OS... why is Solaris' Java slower than Windows'? :p

---

### Post by kavon89 on 2008-10-18
I seem to have experienced the exact opposite. 

In my Computer Science class, we have a bunch of brand new AMD x2 Athlon 64's with 2gb ram, integrated ATI graphics, and a stripped and efficient Windows XP running java 6... and NetBeans is much slower on their systems in comparison to mine. Compiling takes a solid 4-8 seconds with some of the most basic programs, but when I'm working on a large project on my system it's instant compiles and the menus are much snappier on mine.

I use Sun's Java version 1.6.0_06.

---

### Post by Asham on 2008-10-20
I can't say I get a noticeable difference in speed when launching Eclipse under Windows though. Disk IO seems to be what's slowing it down, until it's loaded. It just bugs me that Windows is what's getting the improvements when it should be Linux, or rather the OSS world! I understand why Sun made the decision but it is unfortunate. Sun should take the opportunity and make Java matter in Linux. The outlook of Java knocking .NET off its pedestal in Windows, it is simply not going to happen. Linux and Mac should be Sun's focus, as well as mobiles and PDAs.

---

### Post by achelis on 2008-10-21
> **dwhitney67 said:**
> I have never known Eclipse to run "slow"; I've known it to be difficult to configure/use, but never slow.  Of course, I have not used it in over 3 years, so the application could have degraded (with updates) during that period.

It has become slower and slightly bloated recently (3.4). I believe 3.2 is the fastest version to date. 3.4 still runs smooth for my small projects at home though.

As for really slow on intrepid - have you checked your eclipse.ini file? Increasing ram allowance could help I guess.

---

### Post by jespdj on 2008-10-21
Quoting myself:
> **jespdj said:**
> I've noticed this in the latest version of Eclipse (3.4), especially when editing JavaScript files. But it's not an Ubuntu problem, because it happens also on Windows. I have the feeling that especially the WTP (Web Tools Platform) stuff in Eclipse 3.4 is buggy and unstable.
I'm now using Eclipse 3.4.1 (the lastest version available on eclipse.org) and it's a lot better now, it looks like the WTP developers have fixed the most annoying bugs.

---

### Post by aulio on 2008-11-06
I just installed Kubuntu 8.10, Sun Java 1.6.0.10, and Eclipse 3.4.1. Eclipse is extremly slow on startup and when opening any file with any internal editor. At startup it seems like it hangs, but if I wait long enough (several minutes), it starts. Also, opening a file takes minutes. I've set following in eclipse.ini:

```
-Xmx512m
-XX:MaxPermSize=512m

```

Any ideas what could be the problem?

---

### Post by ifolmedo on 2008-11-07
Same problem here. I have Eclipse 3.4.1, java version "1.5.0_16". I've tested this configuration with Eclipse 8.04 and 8.10.
Eclipse in Ubuntu 8.04 run fast, in 8.10 take five seconds to open every new file.

---

### Post by Maqz447 on 2008-11-07
I had the opposite experience regarding Eclipse startup time. On Gutsy I used Eclipse 3.2 from the repos, and it took a looong time to get it up and running. This was with Sun java 1.6.x. Other than that, it wasn't slow at all. On Intrepid I've installed 3.4.1 from the website and I'm using it with OpenJDK 1.6 from the repos. It only takes about half as long to start up as 3.2 did. 

As for gcj, it has lost its *raison d'être* now that OpenJDK is 100% GPL'd.

---

### Post by exelnet on 2008-12-08
> **ifolmedo said:**
> Same problem here. I have Eclipse 3.4.1, java version "1.5.0_16". I've tested this configuration with Eclipse 8.04 and 8.10.
Eclipse in Ubuntu 8.04 run fast, in 8.10 take five seconds to open every new file.

Im having the exact same problem. Have you fixed it? 

In Eclipse 3.4.1 on Intrepid it takes 5sec to open a java editor.

greetz

---

### Post by jespdj on 2008-12-08
I'm still on Ubuntu 8.04, so I haven't seen the problem on 8.10 myself, but maybe this helps:

Install Sun Java 6 (instead of Java 5):
```
sudo apt-get install sun-java6-jdk
```
Make sure you're using Java 6 instead of Java 5 with this command:
```
sudo update-alternatives --config java
```
Select Sun Java 6 from the menu that this command shows you. Check which version of Java is being used with:
```
java -version
```

---

### Post by tinny on 2008-12-08
One point to note is that regardless of what OS you run Eclipse on you can have performance issues after installing some plugins.

E.g. I noticed a drastic effect on performance after installing the Groovy plugin on both my Windows and Linux installs.

---

### Post by exelnet on 2008-12-08
Nope, its not the plugins. And the sun jdk/jre doesnt make a difference. Its something with intrepid... I have to switch to VM to develop atm... Its quite annoying.

---

### Post by elwell642 on 2009-03-30
I'm seeing this also.  Eclipse 3.4.2 (Ganymede) on amd64 running Intrepid.  

Hardy ran just fine, but Intrepid's tabs take several seconds to open.  It will just say, "Java Editor", "Text Editor", or the like.

Has anyone found a solution other than reverting back to Hardy or using another platform?  Do we know what the problem is?

Thanks for your time!
~Tom

---

### Post by animefan82 on 2009-03-30
For me it depends on what language I'm programming in. Eclipse/Java is extremely slow on intrepid, compared to NetBeans, but Eclipse/C++ runs as fast as in window$, maybe a couple of notches slower. I've just tested it on hardy, and somehow it's on reverse. That is, Java programming goes faster than C++ when it comes to IDE performance (netbeans is still faster). When I program in Java I'm a pure-netbeans fanboy, since it loads faster than it takes me to fill up a glass of tap water, whilst in window$ netbeans takes forever and a day to load.

---

