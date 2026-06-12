---
title: "i thought i had java 6 installed, help needed."
date: 2009-02-01
forum: Programming Talk
---

### Post by DFord425 on 2009-02-01
i ran the command ```
sudo apt-get install sun-java6-jdk sun-java6-jre
```
and when i run the command java --version, i get this:
```
dford@DMoney:~$ java --version
java version "1.5.0"
gij (GNU libgcj) version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

How do i get java 6 from sun?

---

### Post by jpietari on 2009-02-01
I think you need to change your default version of java.

[http://kulitkulit.wordpress.com/2008/09/15/set-default-java-in-ubuntu/](http://kulitkulit.wordpress.com/2008/09/15/set-default-java-in-ubuntu/)

---

### Post by DFord425 on 2009-02-01
That tutorial is not that clear, i tried running the commands, but they dont work. Is there something else i can do or can someone explain what they are saying in that link a little better?

---

### Post by myrtle1908 on 2009-02-02
> **DFord425 said:**
> That tutorial is not that clear, i tried running the commands, but they dont work. Is there something else i can do or can someone explain what they are saying in that link a little better?

_1. check current default java_
```
java -version
```
*This is to see what Java is configured as the default and which version it is.*

_2. display available java_
```
update-java-alternatives -l
```
*Here you are listing the Java environments you have available/installed.*

_3. select java from list_
```
sudo update-alternatives --config java
```
*If step two yields more than one Java environment, then here you can choose which one to set as the default.  Note: I added 'sudo' and double-minus to '--config'.*

---

### Post by DFord425 on 2009-02-02
Thanks for the help. For some reason the first time i tried it the second step didnt work.

---

