---
title: "How to remove all things Java and start over"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-05-10
I can go to some Java-based sites and my Java works fine. But for others it either takes forever to load, or it just doesn't work at all.

It is imperative that one particular site, that worked until just the other day, starts working again.

Yesterday and today I deleted everything that I could on my system that was Java related using the Software Center. That included Icedtea plugin, Icedtea Java Web Start, Iced Tea Java Control Panel, and OpenJDK Java Runtime6. 

Then, using the instructions from [this web site]("https://launchpad.net/%7Ewebupd8team/+archive/java"), I installed the PPA for the Java Installer, verified that it was in my Software Sources, did an update, and ended up with the most recent Java version on my system. But this did not solve my problems so I have since deleted the PPA and re-installed Icedtea plugin, which also re-installed OpenJDK Java Runtime6. 

None of the above has helped in solving this issue so what I would like to do is completely purge my system of all things Java and start over, but when I use sudo apt-get remove java, my system says it can't find it. Oh, and I have tried apt-get remove OpenJDK Java Runtime6 as well, but still get the same errors. 

Advice? 

Thanks.

---

### Post by QIII on 2012-05-10
You may be typing the wrong package name in the terminal if you are being told it can't be found.

In your image, you show what you feel you need to remove.  Click on them and click remove or uninstall if you want to uninstall them.  You really only need uninstall the IcedTea plugin, since you can have any number of Java JREs and JDKs as you want and can switch between them.  It's the plugin that matters when you are browsing.

Failing that, use Synaptic (install it if needed) and find all of those packages and select them for removal.

You have two choices:  Use OpenJDK 7 or Oracle Java 7.  Those are the only options.

If the website that you are having difficulty with does not work with either OpenJDK 7 or Oracle Java 7, you have little recourse.  The issue is with the developers/maintainers of the website.  It may even be that they now require Java 7 and will not work with Java 6 for security reasons or because Java 6 is nearing its end of life.  They may not even be aware that there is an issue, so it might be worth mentioning to them.

The webupd8 package gets you the most recent version of Oracle Java and  installs the Oracle Java browser plugin. It will keep it up to date as  Oracle releases new updates.

See here:

[http://ubuntuforums.org/showthread.php?t=1977358](http://ubuntuforums.org/showthread.php?t=1977358)

As I have time, I am going to endeavor to update the Ubuntu Java wiki.

---

### Post by Curtis6767 on 2012-05-10
> **QIII said:**
> 

You have two choices:  Use OpenJDK 7 or Oracle Java 7.  Those are the only options.

If the website that you are having difficulty with does not work with either OpenJDK 7 or Oracle Java 7, you have little recourse.  The issue is with the developers/maintainers of the website.  It may even be that they now require Java 7 and will not work with Java 6 for security reasons or because Java 6 is nearing its end of life.

As I have time, I am going to endeavor to update the Ubuntu Java wiki.

You may have hit the nail on the head. I uninstalled all those Java-related apps from the software center. Not being able to find Java on my system, I went to the Java site to check to see if I still had Java installed. As the check was in progress, Firefox offered up a plugin, which turned out to be Icedtea. I decided to go ahead and accept the plugin. When I checked again to see if I had Java installed, the site said I did, though it was an older version.

I then went to two Java sites, one that had worked today, which still worked, and the other more important site which did not work and has worked sporadically in the last few days. For whatever reason, the second site worked. I don't know why except that it may have more to do with the site itself than with Java. Hopefully it will work from now on.

Thanks for your help.

---

### Post by QIII on 2012-05-10
OpenJDK (well, the IcedTea plugin) works on the "Do I have Java" test because Oracle understands what OpenJDK is.

If other sites present problems, you may need to go the webupd8 route.  As I said in my post that I cited, OpenJDK should be your first try because it is open source.

Glad you got it to work!

---

