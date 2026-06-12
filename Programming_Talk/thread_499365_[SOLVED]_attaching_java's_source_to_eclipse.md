---
title: "[SOLVED] attaching java's source to eclipse"
date: 2007-07-12
forum: Programming Talk
---

### Post by destructchaos on 2007-07-12
ok, so i have java and ecilpse working but wanted to look at some of the java source so i went into the repos and installed sun-java6-source.  everything worked except it didn't get "attached" in eclipse, so when i hold control and click on a java library function, i get a page saying that the source isn't attached and provides a button to attach it, but i have no idea where to look.

long story short, how do i en mass attach the java source to eclipse so i can look at whatever i want?

thanks.

---

### Post by Ramses de Norre on 2007-07-13
Go to your JRE settings (window>preferences>java>installed JREs), select your current, then edit it and set the source attachment for rt.jar, I just downloaded the src.zip from sun's site and put that in there.

---

### Post by destructchaos on 2007-07-13
worked perfectly, thanks.  you rock!

---

### Post by live4fun on 2010-11-08
I just stumble over this thread and it help solve my problem. Thx.

Just wanted to note it src.zip is already on your machine if you have jdk installed.

For me it was here

/usr/lib/jvm/java-6-sun/src.zip

Just follow where 
>which java

guids you to.

---

