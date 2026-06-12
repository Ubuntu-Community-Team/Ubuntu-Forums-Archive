---
title: "netbeans is so slow"
date: 2007-07-05
forum: Programming Talk
---

### Post by mesocool on 2007-07-05
I am using netbeans 6.0 and it becomes so slow after a few compiles with tomcat. My whole ubuntu is frozen and nothing can be clicked on. I am using sun's jdk. Is there anybody having the same problem or do I need some special configurations to solve this problem?

Thanks..

---

### Post by AlexThomson_NZ on 2007-07-05
Sounds like Java is hogging all your RAM or CPU.  

Does "top -i" or "free -mol" give you any clues?

I found a similar problem with an Eclipse plugin when parsing XML files, but for me NB has been fine with Tomcat

---

### Post by {spitFire} on 2007-07-05
> **mesocool said:**
> I am using netbeans 6.0 and it becomes so slow after a few compiles with tomcat. My whole ubuntu is frozen and nothing can be clicked on. I am using sun's jdk. Is there anybody having the same problem or do I need some special configurations to solve this problem?

Thanks..

The problem is with the permissions set on the JDK folder and contained files, I guess. You can look at the following link for help
* [http://ubuntuforums.org/showthread.php?t=281080](http://ubuntuforums.org/showthread.php?t=281080)

---

### Post by mesocool on 2007-07-07
thanks everybody.

I just found that even I load a large pdf file with evince. My system froze until the current page was loaded. Ubuntu works fine on my desktop. But it becomes slow sometimes (not all the time) after I use it for a while.

Strange.

---

### Post by syn4k on 2010-07-24
Thanks for all your messages first off. 
I'm a PHP developer and have absolutely no experience configuring java or its packages or anything even remotely related...

Still, I have ran the top command whenever I type into my editor and Java skyrockets my CPU up to like 146%! What's worse is that it takes a very LONG time before the few characters I typed to actually show up in the editor. 

I would appreciate any understandable help resolving this issue...lol

---

### Post by syn4k on 2010-07-31
bump

---

### Post by immeëmosol on 2010-12-28
[http://art.ubuntuforums.org/showthread.php?t=1566333](http://art.ubuntuforums.org/showthread.php?t=1566333)
[http://ubuntuforums.org/showthread.php?t=281080](http://ubuntuforums.org/showthread.php?t=281080) ( related -- eclipse)

[http://wiki.netbeans.org/FaqSlowNetBeans](http://wiki.netbeans.org/FaqSlowNetBeans)
[http://wiki.netbeans.org/Performance](http://wiki.netbeans.org/Performance)

---

