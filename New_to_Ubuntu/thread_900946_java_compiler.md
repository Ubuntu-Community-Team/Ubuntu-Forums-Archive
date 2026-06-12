---
title: "java compiler"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by patchido on 2008-08-25
well.. i have a proggraming class and i will want to know which java compiler best suits to be like JCreator, i really want some kind of auto indent and the compiler puting its own brackets as in JCreator... any suggestions?

---

### Post by yabbadabbadont on 2008-08-25
Eclipse

---

### Post by patchido on 2008-08-25
i know about eclipse... but is there any other alternative???
just to have from where to pick

---

### Post by aloshbennett on 2008-08-25
I would suggest Netbeans too, but after Eclipse.

---

### Post by Sinkingships7 on 2008-08-25
Well, first off, compiler != IDE. What you're looking for is an Integrated Development Environment. The best out there for Java is definitely NetBeans in my opinion. [This link]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u7-nb-6.1-oth-JPR@CDS-CDS_Developer") will take you to the Java SE and NetBeans bundle package download page from Sun. Just select Linux as your platform, check the box, and press download. If you need help installing it, just give a shout in this thread and I'd be happy to help you out.

---

### Post by kpkeerthi on 2008-08-26
Install Sun Java from the repositories. See [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by patchido on 2008-08-26
well... for some reason eclipse isnt working..... i cant run anything... or well i dont know how... it is different than in JCreator... in JCreator i only clicked run and it did.... in here i dont know what to do

---

### Post by ggaaron on 2008-08-27
If I remember correctly if you open the main class, you should be able to click the arrow near the run button in toolbar and then choose run this class, etc. If you happen to use older eclipse then you should add a runner (also in the menu near the run button) to be able to run anything. I'm probably not very helpful, but I've switched to netbeans for java after only a brief usage of eclipse.

---

### Post by patchido on 2008-08-27
> **Sinkingships7 said:**
> Well, first off, compiler != IDE. What you're looking for is an Integrated Development Environment. The best out there for Java is definitely NetBeans in my opinion. [This link]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u7-nb-6.1-oth-JPR@CDS-CDS_Developer") will take you to the Java SE and NetBeans bundle package download page from Sun. Just select Linux as your platform, check the box, and press download. If you need help installing it, just give a shout in this thread and I'd be happy to help you out.

i followed that link and ended with "/home/pato/Desktop/jdk-6u7-nb-6_1-linux-ml.sh" i double click and nothing happens... installer isnt working?

---

### Post by ggaaron on 2008-08-27
Any reason not to use netbeans from repositories?

---

### Post by Sinkingships7 on 2008-08-27
> **patchido said:**
> i followed that link and ended with "/home/pato/Desktop/jdk-6u7-nb-6_1-linux-ml.sh" i double click and nothing happens... installer isnt working?

First, move the file to where you want it to be installed. I suggest a system-wide location for installing 'outside' software. Then change it's file permissions to execute. Then execute it. The following commands will do everything for you:
```

cd Desktop
sudo mv jdk-6u7-nb-6_1-linux-ml.sh /opt/
cd /opt/
sudo chmod +x jdk-6u7-nb-6_1-linux-ml.sh
sudo ./jdk-6u7-nb-6_1-linux-ml.sh

```
Executing those commands one by one will get it installed for you. After running the last command, you should get a GUI installer pop-up with simple instructions on how to finish. Again, come back here and ask for help if you need it. I'm more than willing.

After it's done installing, you can open NetBeans by going to Applications -> Programming -> NetBeans IDE
[quote=ggarron]Any reason not to use netbeans from repositories?[/quote]
It's outdated, and this way will get the OP the latest version of NetBeans and the latest version of JDK, which is also outdated in the repositories.

---

### Post by ggaaron on 2008-08-27
Most distributions don't use 6.1, probably for a reason=) 6.0 isn't outdated, 6.1 has more Ruby features, but java ones stay more or less the same I believe. Also Ubuntu uses OpenJDK, not Sun-java as default, so outdated Sun-java shouldn't be a problem.

---

### Post by patchido on 2008-08-28
how can i know if i have java installed correctly so i can use eclipse?

---

### Post by ggaaron on 2008-08-28
Run 'java -version' in terminal to see if java is installed and if yes what implementation is being used. To run eclipse you need a java vm, to compile anything in eclipse you don't have anything special as it has it's own compiler.

---

### Post by patchido on 2008-08-28
well.... then atleast could someone tell me from scratch how am i suposed to install it and also run a program.... hello world would be enough... i can manage the rest.... i just need for it tpo be able to import java.io.*

---

### Post by ggaaron on 2008-08-29
So which java do you finally use? Sun java from repositories, Sun java installed manually, or OpenJDK from repositories? What do you mean by 'it'? Eclipse, JDK?

---

### Post by patchido on 2008-08-29
that is the problem.... i dont even know what i have but i know i need for my clas.... i atach a screen form what i am suposed to download for windows...

---

### Post by ggaaron on 2008-08-29
If you haven't messed up your system already installing from somewhere else than synaptic you'd better install OpenJDK from synaptic, eclipse/netbeans also from synaptic and just use it - no magic steps required to make it work=)

---

