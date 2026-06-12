---
title: "echo $JAVA_HOME"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by mohsen.noor on 2014-01-10
I installed Java (JRE+JDK) but when I write in terminal :echo $JAVA_HOME  it doesn't show anything to me
My Java programs are working correctly.

---

### Post by Dave_L on 2014-01-10
Are you sure you need the environment variable JAVA_HOME?

If the Java programs are working correctly, then I wouldn't worry about it.

---

### Post by mohsen.noor on 2014-01-10
@yes I need that because I'm following some course and instruction

---

### Post by nilla78ro on 2014-01-10
export JAVA_HOME=/usr/lib/jvm/java-7-oracle 
(or what java version you have).
you can add it to ~/.bashrc

---

### Post by mohsen.noor on 2014-01-11
@[[COLOR=#000000]nilla78ro[/COLOR]]("http://ubuntuforums.org/member.php?u=1897113")[COLOR=#000000]  thanks[/COLOR]

---

