---
title: "Why is Ubuntu going so slow"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by thechad90000 on 2012-01-23
Hello, I'm new to Ubuntu and I've just installed 11.10 on my Samsung 700Z laptop. It's going super slow though. I've got 8 GB of RAM and an i7 processor but for some reason it takes forever to watch videos or load any programs. Any help as to why this is happening?

---

### Post by mastablasta on 2012-01-23
what kind of graphics card? do you have proprietary drivers installed?
 
also what does "slow" mean? CPU occupied 100%? or what?
 
see: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by thechad90000 on 2012-01-23
Apologies. I have an ATI graphics card and I guess my version of slow is rather subjective. I've got a quick internet connection, the fastest I could buy from Comcast, and since I've installed Ubuntu my webpages have been loading extremely slow and some programs take longer than usual to load up.

---

### Post by mastablasta on 2012-01-23
ok... i know some pages load slow because they are filled with Flash (and Java) and Flash doesn't have as good support in Linux (thank Adobe for tha). so that is one reason. Another thing you could try is install a different browser. Perhaps Chromium?
A page i found consistently loads slower in Linux (compared to WinXP) is Yahoo.
 
programs take longer than usual to load up - what programmes? Compared to what? longer than when? what is usual?
 
ok things you can do - install and use Unity 2D - perhaps the GPU drivers are not developed fully yet and since unity uses hardware acceleration it could be the culprint.
 
another thing - open terminal and type 
 
top
 
then copy and paste the output here. this command will show what resources are occupied (specifically RAM&CPU). run a browser with terminal open to see the changes. another option is to look in the system monitor. if you think the default one is not showing much, you can try some other monitors such as Conky (a bit difficult to install) or gkrelm (light and nice GUI monitor)
 
you could post them here then someone that knows a bit more about these issues can help. 
 
but just by giving speed based on your perception won't get you far as it is difficult to tell what is causing the slowdwon and then help you based on that knowledge.
 
For example i am running Kubuntu with most effects on chepaest Celeron i could find last year, with 1.3GB DDR RAM, old ATI AGP card with opensource drivers and slow disk yet it all works much faster than with a better maschine running winXP. well except some web pages load slower. but programmes open really fast and general feel of the os is really snappy.

---

### Post by Nick_Kats on 2012-01-23
> **thechad90000 said:**
> Apologies. I have an ATI graphics card and I guess my version of slow is rather subjective. I've got a quick internet connection, the fastest I could buy from Comcast, and since I've installed Ubuntu my webpages have been loading extremely slow and some programs take longer than usual to load up.

Good Morning.
I had the same issue with the Internet speed. It is not a matter of your connection or your pc. The drivers are just not operating well with Ubuntu 11.10. Follow the instructions in the following link and let me know if the internet performs better now.

[http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

P.S.: Be sure that you have a similar network card with the ones described on the thread above.

---

