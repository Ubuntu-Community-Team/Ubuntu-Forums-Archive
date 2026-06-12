---
title: "No NetBeans IDE?"
date: 2012-01-14
forum: Programming Talk
---

### Post by jorpoveda on 2012-01-14
I do not know if this is the correct forum for this thread, but I have a  doubt about NetBeans. Why I cant download it from the Ubuntu Software  Center?

And if it is not recommended, then which would be the most suitable alternative? I will thank your suggestions.

---

### Post by bluexrider on 2012-01-14
> **jorpoveda said:**
> I do not know if this is the correct forum for this thread, but I have a  doubt about NetBeans. Why I cant download it from the Ubuntu Software  Center?


[http://ubuntuforums.org/showthread.php?t=1859677](http://ubuntuforums.org/showthread.php?t=1859677)

---

### Post by ofnuts on 2012-01-14
> **jorpoveda said:**
> I do not know if this is the correct forum for this thread, but I have a  doubt about NetBeans. Why I cant download it from the Ubuntu Software  Center?

And if it is not recommended, then which would be the most suitable alternative? I will thank your suggestions.I have it in my software manager so it must be in an Ubunt repository (like Multiverse...). Check your list of software sources.

This said, tomorrow"s software is better written with today's tools, and since Ubuntu doesn't keep that lind of software very up-to-date unless you upgrade Ubuntu itself, you have better grab the current version from Sun/Oracle anyway.

---

### Post by t1497f35 on 2012-01-14
NetBeans could/should be in the partner repository.
But you  better [download the latest NetBeans 7.1]("http://netbeans.org/").

PS: Saying "I have a doubt about NetBeans" is generally wrong, usually Indians say so when they mean "I have an issue/problem with NetBeans" because for whatever reason they think that "doubt" and "problem" are synonyms in English, they're not.

---

### Post by jorpoveda on 2012-01-14
> **t1497f35 said:**
>  PS: Saying "I have a doubt about NetBeans" is generally wrong, usually Indians say so when they mean "I have an issue/problem with NetBeans" because for whatever reason they think that "doubt" and "problem" are synonyms in English, they're not.

Thanks for this English correction, I am south american so I dont practice my English skills too often. I downloaded NetBeans from the link in your post and I have an issue with the jdk, which I guess is some kind of compiler...???

---

### Post by Telengard C64 on 2012-01-14
> **bluexrider said:**
> [http://ubuntuforums.org/showthread.php?t=1859677](http://ubuntuforums.org/showthread.php?t=1859677)

^ This thread seems to answer all the problems you mentioned, jorvopeda.

Also see [the related bug report](https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/822753).

---

### Post by KdotJ on 2012-01-14
> **jorpoveda said:**
> I have an issue with the jdk, which I guess is some kind of compiler...???

JDK stands for "Java Development Kit".. which does indeed include a compiler as well as a whole bunch of other tools. Wikipedia has a good explanation of what the JDK is and what it contains, [Link HERE]("http://en.wikipedia.org/wiki/Java_Development_Kit")

---

### Post by t1497f35 on 2012-01-14
> **jorpoveda said:**
> Thanks for this English correction, I am south american so I dont practice my English skills too often. I downloaded NetBeans from the link in your post and I have an issue with the jdk, which I guess is some kind of compiler...???

Some folks already responded to this.
In short:
"sudo apt-get install openjdk-7-jdk"
or openjdk-6-jdk to install the older version, JDK6.

Then make sure openjdk-7-jdk is your default jdk:
"sudo update-alternatives --config java"

After that the NetBeans installer will install with the default jdk, which in your case is "openjdk-7-jdk", which is the [open source edition]("http://openjdk.java.net/") of Oracle's [URL="http://www.oracle.com/technetwork/java/javase/downloads/index.html"]JDK 7.
[/URL]

---

### Post by jorpoveda on 2012-01-15
Thanks a lot, I have fixed the problem with the suggested solutions.

---

