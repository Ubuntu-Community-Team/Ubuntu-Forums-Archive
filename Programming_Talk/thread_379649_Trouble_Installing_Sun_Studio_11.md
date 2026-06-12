---
title: "Trouble Installing Sun Studio 11"
date: 2007-03-08
forum: Programming Talk
---

### Post by opticyclic on 2007-03-08
I downloaded Sun Studio 11 from the Sun website
[http://developers.sun.com/sunstudio/downloads/](http://developers.sun.com/sunstudio/downloads/)

I had to install rpm for the installer to work
[http://forum.java.sun.com/thread.jspa?forumID=855&threadID=5102562](http://forum.java.sun.com/thread.jspa?forumID=855&threadID=5102562)
```
apt-get install rpm
ln -s /usr/bin/rpm /bin/rpm
```

However, I still have a problem with the Java SDK
```
error: Failed dependencies:
        glibc >= 2.1.2-11 is needed by j2sdk-1.4.2_08-fcs.i586
        sh-utils >= 2.0-1 is needed by j2sdk-1.4.2_08-fcs.i586
        fileutils >= 4.0-8 is needed by j2sdk-1.4.2_08-fcs.i586
        gawk >= 3.0.4-1 is needed by j2sdk-1.4.2_08-fcs.i586
        textutils >= 2.0-2 is needed by j2sdk-1.4.2_08-fcs.i586
        /bin/sh is needed by j2sdk-1.4.2_08-fcs.i586
```

Anyone got Sun Studio working properly on Ubuntu?
Any idea how I could resolve these dependencies?

---

### Post by hod139 on 2007-03-09
Have you installed Java?

---

### Post by opticyclic on 2007-03-10
I installed Java with Automatix.
I don't think that it is the correct version though. (hence the failed dependencies)

---

### Post by opticyclic on 2007-03-13
Anyone at all got Sun Studio to work with Ubuntu?

---

### Post by derby007 on 2007-03-14
I didnt try to setup SunStudio in Ubuntu, but i did get Netbeans to work. I use SunStudio in M$ but its different to Netbeans as Netbeans comes with FREE DESIGN as default.

---

### Post by opticyclic on 2007-03-15
When I go to the Sun site, SunStudio is only available for Solaris and Linux.
Are you sure that you use in Windows?
Do you have a download link?

---

### Post by Ragazzo on 2007-03-15
If it's a RPM package, did you try installing with **alien** command? Or linking /bin/rpm to /usr/bin/alien

---

### Post by howlingmadhowie on 2007-04-21
i'm still having problems here. i managed to install  sunstudio by going to the .kits/ide/packages directory and running alien on everything there and then dpkg -i *.deb (if you search for sunstudio, you'll find these instructions elsewhere too).

the trouble is, i've installed the newest java version (java6) and sunstudio specifically doesn't look for it when working out which jdk to use, and instead ends up trying to use gcj. hopefully with the open-sourcing of java, these small inconveniences will soon be a thing of the past.

i'll have a go at rewriting the script sunstudio uses to find the jdk and, if it works, i'll post the result

(of course i could always just install the jdk1.4.2 and let it use that)

---

### Post by amo-ej1 on 2007-04-22
I managed to get the (more recent) express edition to work. Perhaps that one brings you more luck ?

---

