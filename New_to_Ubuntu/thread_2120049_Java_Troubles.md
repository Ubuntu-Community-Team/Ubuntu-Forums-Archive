---
title: "Java Troubles"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by LagerDrinker on 2013-02-25
Hi Everyone,

I'm new to the forum, new to Ubuntu and basically new to the whole Linux world.

I have installed Ubuntu today after a few days of frustration with Mint and was hoping a move to Ubuntu would solve my problem, but no joy.

I am trying to access [www.jmeeting.com]("http://www.jmeeting.com") but the java applet is failing to load.

I started off with openjdk and the icedt plugin.

I then tried the JRE from java.com but not totally sure I followed the instruction properly, and I got more confused trying to do the symlink thing, as I say, i'm new to the whole Linux way of doing things but am going to persevere.

As I was getting in a total muddle I followed a tutorial to totally remove all Java from my pc which I think I successfully did.

I then installed open jdk 6 and the icedt plucin in again from the software centre but I still have the same problem,

After I log in there is a pause for a few seconds then a log viewer window pops up, the final line of which says Exception starting applet. ( I was going to try and post the log but cannot find out if or where it is stored)

I'm so far really pleased with my whole Ubuntu experience it's just this one thing that is giving me grief.

If anyone can help me with this before I pull out what little hair I have remaining ;-) I would be most grateful.

Thanks very much,

James

ps I am using the 64 bit version of ubuntu.

---

### Post by KnownSyntax on 2013-02-26
What browser are you using and did you have it open when you install icedtea and openjdk-6-jre? If it was open the whole time then try closing it and reopening it.

I believe if you use Firefox you have to allow for Firefox to use Java in it's settings, although I haven't used Firefox in a while. For Chromium it should just work after you restart the browser or boot it up after openjdk-6-jre and the icedtea plugin install.

---

### Post by LagerDrinker on 2013-02-26
I have tried with both firefox and chrome.
Not sure if I had them open or not but they have both been closed and reopened a few times since, pc has also been shut down and restarted.
I have enabled java in both browsers and checked the plug in using about: plugins in firefox which is listing icedt.
Unfortunately still no joy.

---

### Post by Sandertje on 2013-02-26
Could you type the following in a terminal:

```
java -version
```

and post the output of that here?

---

### Post by LagerDrinker on 2013-02-26
Thanks for the reply,

Unfortunately I am away from home and therefore my pc :cry: until Friday but will post the output then.

---

### Post by LagerDrinker on 2013-03-01
Hi Guys, finally back home.

The result of java -version is......

james@james-desktop:~$ java -version
java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.3) (6b27-1.12.3-0ubuntu1~12.04)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)


Thanks

James

---

### Post by QIII on 2013-03-01
Welcome to the world of Linux and Ubuntu!

There are a few issues here.

1.  OpenJDK 6 and Oracle Java 6 were to reach EOL in November, 2012, but I believe that was extended until April, 2013.  In any case, support is going to end soon.  OpenJDK 7 or Oracle Java 7 are the ones to use.

2.  Given the severe security issues that have cropped up in the browser plugin, I would disable it most of the time and enable it only when you must.  Mozilla has helped out by making he browser plugin "click to play" to limit unintended execution.

3.  OpenJDK 7 is the reference implementation for all implementations of Java, including Oracle Java 7.  Oracle, which is a prime mover in OpenJDK development, has decided it will be that way.  Despite this, some developers either do not design their products to recognize OpenJDK or do not follow the implementation.

As an experiment, I would at least try installing Oracle Java 7 (you can remove it later) by following the method in the wiki in my signature.  Fine "Oracle Java 7", "Command line methods" and "Using webupd8.org's strikingly simple method."  It is a safe PPA that installs an installer that downloads from Oracle and does all the installation for you, sets up the browser plugin and updates Oracle Java 7 when Oracle releases updates.

Let us know how that goes.

Best wishes!

---

### Post by LagerDrinker on 2013-03-01
So do I need to remove all other versions of Java before starting with this. If so, is this a good way of doing it.....


[http://askubuntu.com/questions/84483/how-to-completely-uninstall-java](http://askubuntu.com/questions/84483/how-to-completely-uninstall-java)

or can I just install the new version?

thanks,

James

---

### Post by QIII on 2013-03-01
No need to unistall.  Multiple versions of Java can live happily together on your machine.  You can even choose which one to use if you want to change.

The method I pointed you to will set Oracle Java 7 as your choice, but you can change it later.

---

### Post by LagerDrinker on 2013-03-02
Yay you're a star QIII.

Followed the [Using webupd8.org's strikingly simple method.]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") from the link in your sig,

Working perfectly now. :) :)

BIG THANKS!!!!


James

---

