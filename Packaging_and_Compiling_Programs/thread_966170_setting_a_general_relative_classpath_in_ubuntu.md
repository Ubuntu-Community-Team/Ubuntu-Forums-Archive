---
title: "setting a general relative classpath in ubuntu"
date: 2008-11-01
forum: Packaging and Compiling Programs
---

### Post by Oblivion_4 on 2008-11-01
Hi Everyone,
I am trying to compile a simple java program. My program has several dependencies in other folders. In order for my program to compile the compiler is going to have to looks. 

/uponedirectory/currentdirectory #and then
/uponedirectory/dependcydirectory

I am not sure if this action is taken care of the by the compiler or the shell. I have already realized that to do this I am going to need to set a relative classpath. I have already done this in windows. The classpath that I found that works in windows looks like .;..;..\..

How would I do this in Ubuntu? I already tried what was said in this post  [http://ubuntuforums.org/showthread.php?t=945262](http://ubuntuforums.org/showthread.php?t=945262) I have found that most of the classpaths I have seen throughout this forum look nothing like the one that I have post in the previous paragraph.

---

### Post by gmclachl on 2008-11-01
You can specify a classpath at compile time as  well as through an environmental setting. The separator in Linux is a : 

So from your windows example it would be 

export CLASSPATH=.:..:../..

Which looking at it is current directory:up one directory up two directories.

George

---

### Post by Oblivion_4 on 2008-11-01
> **gmclachl said:**
> You can specify a classpath at compile time as  well as through an environmental setting. The separator in Linux is a : 

So from your windows example it would be 

export CLASSPATH=.:..:../..

Which looking at it is current directory:up one directory up two directories.

George

Thank you, it works perfectly.

---

