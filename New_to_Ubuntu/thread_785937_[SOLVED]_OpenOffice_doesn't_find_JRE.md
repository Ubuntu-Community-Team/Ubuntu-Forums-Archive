---
title: "[SOLVED] OpenOffice doesn't find JRE"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by noorez on 2008-05-07
Hi, I have just installed the sun-java6-jre package. I then went to openoffice tools->options->Java. It didn't find the new JRE so I searched for it but it kept telling me the given path didn't contain a JRE. How do I get OpenOffice to recognize the new JRE.

Also, I though OpenOffice was written in Java....which java version is it using then if I didn't have java installed before?

---

### Post by quelx on 2008-05-07
Your answer is likely in this thread

[http://ubuntuforums.org/showthread.php?t=780958](http://ubuntuforums.org/showthread.php?t=780958)

You need to install Java and the OOo java bindings

---

### Post by noorez on 2008-05-07
Ok, I've installed the openoffice.og-java-common as it suggested and the sun jre that i installed showed up. However, during the installation, I noticed that some gcj pakages were being installed. As I understand it, gcj is GNU's version of java. So, is openoffice using sun's java or gcj java?

---

### Post by quelx on 2008-05-08
you can probably remove the gcj packages without too much fuss (I have sun-java installed and just checked and -none- of the GNU java compiler packages are installed)

Check the Tools>Options>Java pane again and it should tell you which it is using.

If you want Sun's JRE you need to install it

```
sudo apt-get install sun-java6-jre
```

and tell OOo where the new jre is located (actually it will probably find it automagicly)

/usr/lib/jvm/java-6-sun/jre

---

### Post by jamesstansell on 2008-05-08
> **noorez said:**
> Ok, I've installed the openoffice.og-java-common as it suggested and the sun jre that i installed showed up. However, during the installation, I noticed that some gcj pakages were being installed. As I understand it, gcj is GNU's version of java. So, is openoffice using sun's java or gcj java?

OpenOffice.org can use either one. (And others, but let's ignore them for now.)  It just depends on exactly which packages and their versions you have installed, as well as how they are configured.  You found the java setting in the OO.o options, but there are other settings that can be made as well.

Looking at the Ubuntu 8.04 LTS packages, I can't figure out why gcj might have been installed for openoffice.org-java-common when you already had sun-java6-jre.

To answer your one question, only relatively small parts of OO.o are written in Java, and they're generally not considered essential. (But of course if the function that you want to use is, then you might disagree!)

Is OpenOffice.org working for you now?  Feel free to post again with any issues or questions you have.

-james.

---

