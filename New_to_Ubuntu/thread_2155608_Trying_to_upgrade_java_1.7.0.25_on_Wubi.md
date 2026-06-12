---
title: "Trying to upgrade java 1.7.0.25 on Wubi"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by kcs636 on 2013-06-18
I have a Windows desktop running a current Wubi, 12.04.  I put java on it for someone's games
following this tutorial.

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

java -version show 1.7.0.21 64bit.

Yahoo is now calling for 1.7.0.25.   What is my best route to upgrade?

I actually followed the mentioned webpage a bit, it's almost as if the update isn't aware of 1.7.0.25 and
think I have the most current?


thanks

---

### Post by claracc on 2013-06-19
I have an ubuntu 12.04 (gnome fallback desktop) fully updated, and I also have the webup8 repository added in order to have the last oracle java version.

However, my java is ```
clara@clara1:~$ java -version
java version "1.7.0_21"
Java(TM) SE Runtime Environment (build 1.7.0_21-b11)
Java HotSpot(TM) Server VM (build 23.21-b01, mixed mode)

```

So I understand that java 1.7.0_25 is not yet in the repository, you will have to wait a little in order it be included. I suppose it will be included in short time.

---

