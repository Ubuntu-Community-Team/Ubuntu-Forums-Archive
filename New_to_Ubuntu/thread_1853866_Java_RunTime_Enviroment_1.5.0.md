---
title: "Java RunTime Enviroment 1.5.0"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by Silent Messy Death on 2011-10-03
Some of my windows programs keeps telling me that i need Java RunTime Enviroment 1.5.0 and when ever i close the windows send me to suns website with Java 6 and what i've looked at in Ubuntu software Center i've already got Java 6 please help =/

Thanks
SMD

---

### Post by cavh on 2011-10-03
It may be that your Windows programs require a specific Java version (i.e. 1.5) to run, and that a newer Java version won't work. You can have more than one version of Java installed - see this link for a how-to: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

If you install 1.5, make it your default and the Windows program(s) still complain, you'll need to see whether you can set WINE to use the 1.5 version. That's beyond my experience, sorry I can't help there.

You should also review the WINE database to see whether your program(s) are listed and if so, what level of compatibility you can expect:
[http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by Silent Messy Death on 2011-10-03
Alright told the terminal to scan for latest and newest updates for java and says tht i got the latest versions of java how would i go about setting them to default?

---

### Post by Silent Messy Death on 2011-10-03
lol oh oops srry tierd didnt relize didnt kno how xD hope some one else could help me with tht mean time look on the internet

---

### Post by Ken UK on 2011-10-03
I don't think have 6 instead of 5 is going to cause a problem and if it does then it will most likely be a fault or error message within the programme itself.

If you are using WINE then surely you need Java installed in WINE? I'm not an expert on WINE but the Java installation in Ubuntu (found in the software centre) is something completely different. try installing the latest version of Java for Windows within WINE.

---

