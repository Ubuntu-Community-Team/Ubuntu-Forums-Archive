---
title: "Problem, BlueJ Java environment"
date: 2008-02-04
forum: Programming Talk
---

### Post by Sugz on 2008-02-04
So i was compiling a method tosay in Java when i was faced with the following error.

**cannot resolve scanner - class scanner**

i had a look around and saw that i perhaps had outdated. JDK or Java runtime environment.

I think i may have got the most recent version. but how do i make BlueJ point to this new JRE or how do i sort anything else out?

I am so confused but i would prefer to get this problem sorted asap.

-Many thanks 

-Sugz

---

### Post by jken146 on 2008-02-04
What version of java are you using?  To find out, open a terminal and type ```
java -version
```

---

### Post by Shin_Gouki2501 on 2008-02-04
bluJ ... don't know who thinks this is good for java learning.. me not.
well give us details on ur source code and java version and we may be able to help u!

---

### Post by The Cog on 2008-02-04
> **Shin_Gouki2501 said:**
> bluJ ... don't know who thinks this is good for java learning.. me not.
I do.

Did you write a class scanner? If so, check it's not Scanner (capital S) instead.
If not, you probably need to import the package that contains the class, and again, it's probably a capital S.

---

### Post by Sugz on 2008-02-04
Fixed it, i simply downloaded JDK 6, deleted (uninstalled) all remanents of Bluej and then re-installed Blue J pointing to the new version.
Im now running java 1.5.0_13 (if thats the latest one)

Again thanks for the help

---

### Post by JamesUser on 2008-02-05
wait a minute.. you downloaded JDK6, and re-installed BlueJ to point to it. And it shows 1.5? Maybe BlueJ brings with it a JDK too..

Anyways latest JDK is 1.6 while J2EE SDK is 1.5.

---

### Post by jken146 on 2008-02-05
BlueJ doesn't bring a JDK with it; the installer asks you to point it to a JDK.  On having installed Sun's JDK version 6 from the Ubuntu repositories, you can point the BlueJ installer to /usr/lib/jvm/java-6-sun-1.6.0.03

---

### Post by hfinger on 2009-04-23
> **Shin_Gouki2501 said:**
> bluJ ... don't know who thinks this is good for java learning.. me not.u!

Well, I do.  It's used by Monash University and I got a High Distinction and had never programmed before.  You can download a version of Netbeans that incorporates BlueJ. You can access the same files from both IDEs simultaneously and each IDE automatically updates its view.  A great way to ditch the training wheels gradually.

Regards,
Hedley :cool:

---

