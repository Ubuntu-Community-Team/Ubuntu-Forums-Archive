---
title: "How do I install JRockit?"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by Tetamusha on 2012-08-01
Hi guys. I installed Ubuntu here on my Dell Inspiron 14R and I need to develop stuff in Java for college, so I need a JDK. My teacher told me to use JRockit but, unlike OpenJDK and Oracle JDK, it is being a pain to install...

I downloaded a .bin file from the link below (my system is 64 bits) and used chmod +x and ./ to run it.
[http://www.oracle.com/technetwork/middleware/jrockit/downloads/index.html](http://www.oracle.com/technetwork/middleware/jrockit/downloads/index.html)

I chose to install it inside /usr/share, but when i typed 'java -version', it wasn't found and Eclipse didn't run either. Then I installed it in my user folder, but it wasn't found too. I used 'sudo rm -r' to remove both directories, but now I have no JDK.

Can anyone help me? Do I have to set those JAVA_HOME, JAVA_PATH, PATH, CLASSPATH etc. system variables for Ubuntu to find JRockit? If so, can anyone help me?

Thanks

---

### Post by levlaz on 2012-08-01
I think you need to install java, there are a lot of great options. 

openJDK/JRE are available in the software center.  

JRocket is a JDK(Java development Kit) you still need JRE (Java Runtime Environment) in order to use it. 

If you want "real" java [this is a great guide. ]("http://www.duinsoft.nl/packages.php?t=en")

---

### Post by Tetamusha on 2012-08-02
I thought the JDK installed the JRE with it. It is a full JVM, after all. Besides, I just uninstalled every JRE and JDK from my Windows, installed only JRockit and Eclipse (which depends on Java to run) worked after that.
When I needed Oracle JDK, I used the following:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by levlaz on 2012-08-02
Hm.. not sure if this is important but the link you showed said that JRockit is for Java6... perhaps the issues is that you are installing Java7?

---

### Post by Tetamusha on 2012-08-02
That's the newest JRockit version available.

---

