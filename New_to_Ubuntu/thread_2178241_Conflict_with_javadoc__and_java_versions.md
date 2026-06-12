---
title: "Conflict with javadoc  and java versions"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by PedestrianMan on 2013-10-02
Hi everybody, 

[TABLE]
[TR]
[TD="class: votecell"]

[/TD]
[TD="class: postcell"]                When generating javadoc I get an error when javadoc is parsing the diamond operator es:
  ```
List<String> list = new ArrayList<>()
// javadoc 6 blocks here
```  I am using ubuntu 12.04 and the command javadoc -J-version says I am using:

  java version "1.6.0_27"  However I have compiled and developed the project in Java 7. Of course if I type 

java -version   I have the following result: java version "1.7.0_21"

  How can I change/upgrade the jdk used by the javadoc command?

Furthermore, this is what I get with update-java alternatives:
 ```
sudo update-java-alternatives -l
java-1.6.0-openjdk-i386 1061 /usr/lib/jvm/java-1.6.0-openjdk-i386
```  I do not even get java 1.7.0 which is the one I am using. Again java -version returns java 1.7.0.
      
[/TD]
[/TR]
[/TABLE]

Anybody can help me out to solve these java versions conflict?
Thanks in advance.

---

