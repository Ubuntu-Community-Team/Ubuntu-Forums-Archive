---
title: "Eclipse is running excruciatingly slow"
date: 2007-07-23
forum: Programming Talk
---

### Post by Amablue on 2007-07-23
I'm using Sun's Java 6, and it's a fresh install, but it slows to a crawl constantly. For example, when I start a comment with /* it takes a few seconds to comment out the entire source code below it before I can continue to type. The autocomplete can lock up the program for 10 or 20 seconds at a time and the little memory manager applet in my panel shows the processor jumping up to 100%

---

### Post by hod139 on 2007-07-23
Are you sure that you are using Sun's java.  What's the output of
```

java -version

```

If you installed java and eclipse from the repositories I have a howto written that should fix your problem: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by Amablue on 2007-07-23
```
alex@Shigeru:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```

I found it. Turns out I had fixed everything except the /etc/eclipse/java_home file. Now that I put sun's java at the top it works fine

---

### Post by destructchaos on 2007-07-23
i know this question gets asked a lot (i asked it once), but i have a few followup question that go a bit beyond:

1) what is this gcj hunk that is horribly slow and is it used for anything other than slowing down eclipse?

2) why aren't the eclipse config files set properly to use sun's java first since it was clearly intended to be that way? (conclusion derived from speed difference)

3) would it be such a horrible thing to have sun's java be a recommended package to be installed when someone apt-get installs eclipse?

---

### Post by hod139 on 2007-07-23
> **destructchaos said:**
> i know this question gets asked a lot (i asked it once), but i have a few followup question that go a bit beyond:

1) what is this gcj hunk that is horribly slow and is it used for anything other than slowing down eclipse?

gcj is the GNU java compiler.

> 
2) why aren't the eclipse config files set properly to use sun's java first since it was clearly intended to be that way? (conclusion derived from speed difference)

Known bug: [https://launchpad.net/ubuntu/+source/eclipse/+bug/45347](https://launchpad.net/ubuntu/+source/eclipse/+bug/45347)

> 
3) would it be such a horrible thing to have sun's java be a recommended package to be installed when someone apt-get installs eclipse?
Now that Sun's java is open source, this is probably a doable idea.  You should request it on launchpad.  The whole java-common stuff is a mess.

---

### Post by destructchaos on 2007-07-23
> **hod139 said:**
> Known bug: [https://launchpad.net/ubuntu/+source/eclipse/+bug/45347](https://launchpad.net/ubuntu/+source/eclipse/+bug/45347)

after reading the page, it sounds like a solution is in the works.  good stuff.

> **hod139 said:**
> Now that Sun's java is open source, this is probably a doable idea.  You should request it on launchpad.  The whole java-common stuff is a mess.

how would i go about doing that?  i've done the auto-bug submit thing, but i didn't know stuff could be specifically requested.

---

