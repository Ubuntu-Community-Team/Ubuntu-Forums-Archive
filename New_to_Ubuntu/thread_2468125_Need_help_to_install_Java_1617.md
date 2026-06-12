---
title: "Need help to install Java 16/17"
date: 2021-10-19
forum: New to Ubuntu
---

### Post by lucbrasnel on 2021-10-19
I setup Lubuntu on an old pc that was lying around to use as a server. I am very new to linux and ubuntu, so i basically just follow online tutorials to install software.

I need to install java 16 or 17 to run a 1.17 minecraft server, but every attempt I have made to install it has failed.
I was wondering if lubuntu just doesn't support it / the ppa repository used to install it.

I appreciate any help you can provide

---

### Post by Tadaen_Sylvermane on 2021-10-19
[https://launchpad.net/~openjdk-r/+archive/ubuntu/ppa](https://launchpad.net/~openjdk-r/+archive/ubuntu/ppa)

I use the openjdk-17-jre-headless for my minecraft server docker container.

---

### Post by ActionParsnip on 2021-10-19
Which Java do you want? Oracle Java? OpenJRE?

---

### Post by guiverc on 2021-10-19
You'll need to provide release details.

Lubuntu is a *flavor* of Ubuntu, so will run any software any other Ubuntu family member will run.

---

### Post by QIII on 2021-10-19
OpenJDK does not support all the features of Minecraft -- or shall I say the developers of Minecraft don't understand the relationship between OpenJDK and Oracle Java and are too lazy to take the time to learn.

Anyway, Oracle Java is the best for Minecraft, but Oracle will no longer allow anyone to have Oracle Java in their repos or PPAs.  Best to install Oracle Java from Oracle's site and set it as the alternative.

And yes, you need to let us know your *release*, not just the flavor.

Further, it would be best to have the Minecraft on a *server*, not on a flavor with a DE.  Ubuntu Server version is what you want.  You don't need or want the overhead of a DE on a server.

---

### Post by sw-mariusz on 2021-10-20
1 ) Download java 17 (x64 Compressed Archive) from [www.oracle.com]("https://www.oracle.com/java/technologies/downloads/") and unpack to /usr/bin/java
2)  sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-17/bin/java 1
3)  sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-17/bin/javac 1
4)  Change OpenJDK java to java 17 : sudo update-alternatives --config java
5) Change OpenJDK javac to java 17: sudo update-alternatives --config javac
6) Check java/javac version: java -varsion and javac -version

---

### Post by Tadaen_Sylvermane on 2021-10-20
> **QIII said:**
> OpenJDK does not support all the features of Minecraft -- or shall I say the developers of Minecraft don't understand the relationship between OpenJDK and Oracle Java and are too lazy to take the time to learn.

Anyway, Oracle Java is the best for Minecraft, but Oracle will no longer allow anyone to have Oracle Java in their repos or PPAs.  Best to install Oracle Java from Oracle's site and set it as the alternative.

And yes, you need to let us know your *release*, not just the flavor.

Further, it would be best to have the Minecraft on a *server*, not on a flavor with a DE.  Ubuntu Server version is what you want.  You don't need or want the overhead of a DE on a server.


Not sure this is accurate anymore. I just now did a bit of searching because I was curious. Couldn't find much other than the current desktop launcher (for Windows) is using the OpenJDK (Just installed and loaded Minecraft on my own desktop for personal confirmation. It asked for the OpenJDK to be allowed through the firewall). Either it's only on the desktop launcher, or they gave Oracle the middle finger. I personally hope the latter. Regardless in my own personal experience I haven't had any discernable issue with the OpenJDK to date. Admittedly I don't play Minecraft as much as I used to.

Before I ran the OpenJDK just because I dislike Oracle and was willing to deal with a few minor inconveniences. Now it appears to be even more solid on the OpenJDK side.

*EDIT* Apparently Oracle changed the required licensing for Java in the last couple years. I don't know about client's but I read something about 25 bucks a month per cpu and "world" for server operators. Much less in bulk but still a lot of money when they can get the OpenJDK effectively for free and maybe even help improve it. This licensing change is aimed at people profiting off of Java directly.

---

### Post by QIII on 2021-10-20
Within the last year, when I had a server set up for the teenagers living with us, flight as default was still not possible with OpenJDK.  In fact, I'm not sure if any of the components of Creative Mode were available.  Nor were text commands.

The OpenJDK source code is the basis for Oracle's commercial Java products.  In fact, Oracle has engineers assigned to the open source OpenJDK effort.  "Oracle-centric" developers may be unaware of this, and when an Oracle branded module is not found, they don't bother to use the OpenJDK equivalent.  My guess, at any rate.

---

### Post by Tadaen_Sylvermane on 2021-10-20
Unfortunately without any documentation on it direct from Mojang / Microsoft (we know how that will go, if ever) it's speculation on both sides. I don't know. You got me curious now. I never did see a default flight on anything other than spectator mode. But as I said I wasn't exactly a big player. It was mainly for the wife and I. 

To late overall but wouldn't it be nice if any closed source software that used open source parts regardless of how small had to... not open the source for the whole thing but disclose the exact open source bits they are using. I'm sure there are multiple sides to that of course. Is a thought.

---

