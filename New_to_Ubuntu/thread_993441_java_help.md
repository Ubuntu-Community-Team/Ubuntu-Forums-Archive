---
title: "java help?"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by thehereaway on 2008-11-25
Hey, i was reading some threads on here and took what i thought were the right steps to installing java but i don't think it has worked correctly.

When i check what version i have in the terminal it says...

> darren@Darren:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
darren@Darren:~$ 


but then java tests on the internet tell me im using 1.4.2, which would explain why java applications are still not working.

any ideas?

---

### Post by taurus on 2008-11-25
Did you remember to install the plugin as well?

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

---

### Post by thehereaway on 2008-11-25
yeah i typed in this...

> sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version

---

### Post by taurus on 2008-11-25
Try running this to make sure everything is pointing to the latest version of java.

```
sudo update-alternatives --config java
```

---

