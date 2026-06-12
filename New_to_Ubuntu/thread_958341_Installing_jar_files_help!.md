---
title: "Installing jar files help!"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by jlbr on 2008-10-25
OK, I want to install a file called UltrMixer-2.3.4-linux.jar

And this is what I got:

juanluis@juanluis-laptop:~$ java -jar /home/juanluis/tmp/UltraMixer-2.3.4-linux.jar
Failed to load Main-Class manifest attribute from /home/juanluis/tmp/UltraMixer-2.3.4-linux.jar

I installed javacommon and javawrapper from Synaptic, what am I doing wrong?

---

### Post by Duck2006 on 2008-10-25
This may be of help.

[http://ubuntuforums.org/showthread.php?t=370757](http://ubuntuforums.org/showthread.php?t=370757)
[http://ubuntuforums.org/archive/index.php/t-504905.html](http://ubuntuforums.org/archive/index.php/t-504905.html)

---

### Post by drtre on 2008-10-25
> **jlbr said:**
> Failed to load Main-Class manifest attribute from /home/juanluis/tmp/UltraMixer-2.3.4-linux.jar

that means jvm cannot load the class that contains the main method which is written in your manifest in the JAR file. wud u please provide the input of this : 

> jar -tf /home/juanluis/tmp/UltraMixer-2.3.4-linux.jar

---

### Post by jlbr on 2008-10-25
thanks, it worked like a charm this time.

---

