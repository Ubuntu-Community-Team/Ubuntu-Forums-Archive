---
title: "Java 1.5.0"
date: 2006-10-06
forum: Programming Talk
---

### Post by FangPT on 2006-10-06
Hi all.

I'm having a problem with my gij version. 
Currently i have 1.4.2 but i need to updgrade it to 1.5 because it's necessary in order to compile certain programs.

The thing is, i updgraded everything, i used "search" , i used Add/remove and there is no upgrade at all to a 1.5 version.

Oh, and I'm using Eclipse.

I appreciate any help because i googled it so many times and search forums but i just can't get this to work.

thanks ;) 

```
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)
 
```

---

### Post by JoshHendo on 2006-10-06
[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

I reccomend downloading the RPM and converting it with alien.

- Josh

---

### Post by welshboy on 2006-10-06
Personally, I think the best version of Java to have is the sun version.  After all, they wrote it.  

And if you want to use the java that the majority of people are using, then go for it.

to install it you need to ensure that your repositories are set to multiverse and universe, and look for sun-java (can't remember what the rest of it is called.)  

This will then set up java on your machine,

Once all that's done, type in sudo update-alternatives --config java
and select the Sun version.

Voila, one java system, or if you do prefer gij, then do what Fang suggested.

welshboy

---

### Post by hod139 on 2006-10-15
See this howto:[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by bieber on 2006-10-15
Eek.  He comes along asking how to upgrade a free Java implementation, and immediately three responses pushing Sun's Java.  Why, unless it's absolutely neccesary, would you urge a fellow GNU/Linux user to install proprietary software?

Anywho, I'm afraid the only way to get the latest version is going to be to download the latest source and compile.

---

### Post by Hendrin on 2006-10-15
Unfortunately, although GCJ is moving along quite rapidly, it still can't run  or compile many of the java programs around hence the reason quite a few programmers will recommend JAVA's version.

If a GCJ version catches up to Sun's version or Sun completely open sources there version I will definitely start using my Java knowledge again. :)

---

### Post by hod139 on 2006-10-16
> **bieber said:**
> Eek.  He comes along asking how to upgrade a free Java implementation, and immediately three responses pushing Sun's Java.  Why, unless it's absolutely neccesary, would you urge a fellow GNU/Linux user to install proprietary software?

Why?  Sun's java may not be open (they keep claiming they will open it), but it is **free**, an **officilly supported** package, and **superior** to GNU's version (gnu SWING support is still lacking, some of the math functions I used on an older version of GNU's java were producing incorrect results, etc).  Unless you philosophically want to run open source software, why not use Sun's java?

---

