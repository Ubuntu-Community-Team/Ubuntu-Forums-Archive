---
title: "set environment variables ibm java 7"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by 007casper on 2012-08-26
when I load the application, I get ```

/usr/lib/jvm/java-7-ibm/jre/bin/java/bin/java not found
```

????

How come it is not working?

I followed the instructions here
[http://www.wikihow.com/Install-IBM-Java-on-Ubuntu-Linux](http://www.wikihow.com/Install-IBM-Java-on-Ubuntu-Linux)

however I only loaded sdk since it has jre.  
> 
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/java-7-ibm/jre/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/java-7-ibm/bin/javac" 1

sudo update-alternatives --set java /usr/lib/jvm/java-7-ibm/bin/java
update-alternatives: error: alternative /usr/lib/jvm/java-7-ibm/bin/java for java not registered, not setting.

sudo update-alternatives --set javac /usr/lib/jvm/java-7-ibm/bin/javac
> 
java -version
java version "1.7.0"
Java(TM) SE Runtime Environment (build pxa6470sr1-20120330_01(SR1))
IBM J9 VM (build 2.6, JRE 1.7.0 Linux amd64-64 20120322_106209 (JIT enabled, AOT enabled)
J9VM - R26_Java726_SR1_20120322_1720_B106209
JIT  - r11_20120322_22976
GC   - R26_Java726_SR1_20120322_1720_B106209
J9CL - 20120322_106209)
JCL - 20120322_01 based on Oracle 7u3-b05
> 
which java
/usr/bin/java
> 
echo $JAVA_HOME
/usr/lib/jvm/java-7-ibm/jre/bin/java

---

### Post by androssofer on 2012-08-26
> **007casper said:**
> when I load the application, I get ```

/usr/lib/jvm/java-7-ibm/jre/bin/java/bin/java not found
```



there seems to be addititonal

```

/bin/java

```

on the end of where the application is looking vs what you have set as your $JAVA_HOME

can you change where the application looks for java? it seems as if it needs to be aimed at:

```

/usr/lib/jvm/java-7-ibm/jre
```

and then it goes into /bin/java itself.. where as you may have done all the work for it, aimed it all the way to /bin/java and its getting confused..

---

### Post by 007casper on 2012-09-02
thank you so much

---

