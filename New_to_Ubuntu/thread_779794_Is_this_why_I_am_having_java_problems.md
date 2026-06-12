---
title: "Is this why I am having java problems"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by dstin1 on 2008-05-03
In the about plugins it says I am using icedtea is this correct?

---

### Post by Michael.Godawski on 2008-05-03
IcedTea is available in Ubuntu 7.10 (Gutsy Gibbon), from the "universe" repository. What version of Ubuntu are you using?

To install the java plugin run this code in terminal

```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-pugin 
```

---

### Post by dstin1 on 2008-05-03
Upgraded to hardy been having problems with ff3 and java ever since.  What I want to do is very simple play pogo but when I try to load a game I get a server error after the ad.  I can kind of make it work with opera but is is slow.  I also installed installed firefox 2 but I can't get java to work at all I don't know how to add the java plugin to the browser.

---

### Post by SunnyRabbiera on 2008-05-03
ah, hardy uses the alternate version of java (openjdk), so thats probably why you have issues.
you can get normal java in the repositories by going up to system, then to administration and then click on synaptic package manager.
after that go up to settings within synaptic and go to "repositories"
and make sure that all the repositories are checked off except the source code repository, and in the second tab make sure that all the third party repositories are checked off.
after that search for jre, REMOVE openjdk and replace it with normal java.

hope that works, I dont use pogo so your guess is as good as mine

---

### Post by Sinkingships7 on 2008-05-03
I was having Java problems. Uninstalling the icedtea and java web starts and then running:

```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

solved my problems. Hope this helps!

---

### Post by alzie on 2008-05-23
By following the directions here: [http://ubuntuforums.org/showthread.php?t=784384](http://ubuntuforums.org/showthread.php?t=784384)

I've been able to get Firefox3.0b5 playing at pogo using the 
sun-java5-plugin

Most of the games now play well for me.

Hope this helps you

---

