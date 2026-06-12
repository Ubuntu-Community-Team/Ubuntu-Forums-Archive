---
title: "[SOLVED] Ubuntu and eclipse"
date: 2008-09-02
forum: Programming Talk
---

### Post by tojas on 2008-09-02
Hello guys!

My question is related with eclipse as you can see in the title. So I created a little project in eclipse... I am creating a JFrame and putting in some other JPanels... So the problem occurs when I push the run button... the JFrame appears but it freezes and don't want to do anything else... Btw this only occurs when I am running it under Ubuntu... Sadly it is working with winxp..

---

### Post by tinny on 2008-09-02
> **tojas said:**
> Hello guys!

My question is related with eclipse as you can see in the title. So I created a little project in eclipse... I am creating a JFrame and putting in some other JPanels... So the problem occurs when I push the run button... the JFrame appears but it freezes and don't want to do anything else... Btw this only occurs when I am running it under Ubuntu... Sadly it is working with winxp..

Can you post some code?

Also whats the output of:
```

java -version
javac -version

```

For Java development on Ubuntu you REALLY want to install Sun Java 6 JDK. (The Default "OpenJDK" is rubbish)

```

sudo apt-get update
sudo apt-get install sun-java6*

```

After installing Sun Java 6 JDK you will need to configure Eclipse to use it.

“Window” > “Preferences” > “Installed JREs” you need to “Add” the Sun JDK and set it as the default.

The JDK should be in the "/usr/lib/jvm/" folder.

---

### Post by tojas on 2008-09-02
tojas@tojas:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
tojas@tojas:~$ javac -version
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.

Btw I also wanted to install java 1.6 but I didn't know how... I don't have enough experience in linux... so thank you very much for help to install java 1.6... I am trying with this java too:)
Let's see what happens... :D

---

### Post by tinny on 2008-09-02
Make sure you set Eclipse up to use the Sun Java 6 JDK. You have to do this manually. (This is a really common problem people have)

“Window” > “Preferences” > “Installed JREs” you need to “Add” the Sun JDK and set it as the default.

---

### Post by tojas on 2008-09-02
I got some error during install java6... :(
Can you help with it please?

tojas@tojas:~$ sudo apt-get install sun-java6*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting sun-java5-bin for regex 'sun-java6*'
Note, selecting sun-java5-doc for regex 'sun-java6*'
Note, selecting ia32-sun-java5-bin for regex 'sun-java6*'
Note, selecting ia32-sun-java5-plugin for regex 'sun-java6*'
Note, selecting sun-javadb-common for regex 'sun-java6*'
Note, selecting sun-java6-plugin for regex 'sun-java6*'
Note, selecting sun-java6-demo for regex 'sun-java6*'
Note, selecting sun-java5-jdk for regex 'sun-java6*'
Note, selecting sun-java5-jre for regex 'sun-java6*'
Note, selecting sun-javadb-doc for regex 'sun-java6*'
Note, selecting sun-java5-src for regex 'sun-java6*'
Note, selecting sun-java6-fonts for regex 'sun-java6*'
Note, selecting sun-java5-source for regex 'sun-java6*'
Note, selecting sun-java6-bin for regex 'sun-java6*'
Note, selecting ia32-sun-java6-plugin for regex 'sun-java6*'
Note, selecting sun-java6-doc for regex 'sun-java6*'
Note, selecting ia32-sun-java6-bin for regex 'sun-java6*'
Note, selecting sun-java6-jdk for regex 'sun-java6*'
Note, selecting sun-javadb-demo for regex 'sun-java6*'
Note, selecting sun-java6-jre for regex 'sun-java6*'
Note, selecting sun-javadb-core for regex 'sun-java6*'
Note, selecting sun-java6-src for regex 'sun-java6*'
Note, selecting sun-java6-source for regex 'sun-java6*'
Note, selecting sun-java5-demo for regex 'sun-java6*'
Note, selecting sun-javadb-javadoc for regex 'sun-java6*'
Note, selecting sun-java5-fonts for regex 'sun-java6*'
Note, selecting sun-java5-plugin for regex 'sun-java6*'
Note, selecting sun-java6-javadb for regex 'sun-java6*'
Note, selecting sun-javadb-client for regex 'sun-java6*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java5-fonts: Conflicts: ttf-lucida
  sun-java6-fonts: Conflicts: ttf-lucida
E: Broken packages

---

### Post by tinny on 2008-09-02
What version of Ubuntu are you running?

You will need to force the package install and then you may need to force the reinstall of ttf-lucida.

```

sudo apt-get update
sudo apt-get install sun-java6* --force-yes

```

Where did you get ttf-lucida from? Thats not a Ubuntu package...

---

### Post by tojas on 2008-09-02
Ubuntu version is 8.04.
Again I got this error what I copied earlier.
And I tried this:
tojas@tojas:~$ sudo apt-get install ttf-lucida --force-yes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ttf-lucida is a virtual package provided by:
  sun-java6-fonts 6-06-0ubuntu1
  sun-java5-fonts 1.5.0-15-0ubuntu1
You should explicitly select one to install.
E: Package ttf-lucida has no installation candidate

I simply installed Ubuntu 8.04 to my laptop, then added the eclipse package. So I didn't added ttf-lucida... Maybe the java added... or don't know..

---

### Post by tinny on 2008-09-02
Did this work?

```

sudo apt-get update
sudo apt-get install sun-java6* --force-yes

```

If it worked, whats the output of this:

```

java -version
javac -version

```

Are using using 64bit Ubuntu?

---

### Post by tojas on 2008-09-02
> sudo apt-get update
sudo apt-get install sun-java6* --force-yes


This was not working... I got the same error and java -version replay with the same message what I pasted here..:(

---

### Post by tinny on 2008-09-02
Can you post your sources.list file.

/etc/apt/sources.list

---

### Post by tojas on 2008-09-02
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


Here it is. And I am using 32 bit ubuntu.

---

### Post by jespdj on 2008-09-03
> **tinny said:**
> For Java development on Ubuntu you REALLY want to install Sun Java 6 JDK. (The Default "OpenJDK" is rubbish)
I disagree; the [OpenJDK](http://openjdk.java.net/) version of Java is definitely not rubbish, and its functionality is very close to Sun Java 6 (in fact, it *is* Sun Java 6 for 96%, and the remaining 4% is open source code to replace the proprietary parts of Sun Java 6). Eclipse works fine on OpenJDK Java.

Tinny, are you mistaking OpenJDK Java for GNU Java? The GNU version of Java is slow, incompatible and incomplete and many Java programs don't run well on it.

There is, however, a known bug with regard to Swing and Compiz. In older versions of Java, Swing windows will display as an empty gray rectangle. This bug was solved in one of the Java 6 update versions.

> **tojas said:**
> tojas@tojas:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
This is an old version of Java that most likely has the bug.

---

### Post by tinny on 2008-09-03
> **jespdj said:**
> 
Tinny, are you mistaking OpenJDK Java for GNU Java?


Perhaps. I see these "I have a problem with Java" questions here all the time. 99% of the time when the user switches to Sun Java the problem goes away.

---

### Post by tojas on 2008-09-04
I don't want to choose who has right... but... after I installed Sun JDK 1.6 my problem is solved. Thanks for help guys.

---

### Post by tinny on 2008-09-04
> **tojas said:**
> I don't want to choose who has right... but... after I installed Sun JDK 1.6 my problem is solved. Thanks for help guys.

How did you get passed the "sun-java6-fonts: Conflicts: ttf-lucida" problem?

---

### Post by karo on 2009-07-24
> **tinny said:**
> How did you get passed the "sun-java6-fonts: Conflicts: ttf-lucida" problem?
Exactly - how?

I've got exactly the same problem: ttf-lucida conflicts sun-java5-fonts and sun-java6-fonts and also frames (which used to work properly) freezeing in Eclipse...

Please, help.

EDIT:
Eclipse seems to start working properly... :| Have no idea why...
But the conflict still exists.

---

