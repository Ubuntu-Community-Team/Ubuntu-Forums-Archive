---
title: "How can i execute a jar file?"
date: 2014-12-11
forum: New to Ubuntu
---

### Post by samira3 on 2014-12-11
[FONT=arial][SIZE=2]to execute a jar file, at the first i installed openjdk pakeges and then next command:
```
java -jar ccnChat.jar
```
I got this
```
error: Failed to load Main-Class manifest attribute from ccnChat.jar
```
then i tried another way: i right clicked on the jar file, and i marked allow executing file as program from permissions tab and i chose openjdk as its default program. then i double clicked on jar file but it didn't open. And there is not any message or error. Could u please help me that how can i execute this jar file?[/SIZE][/FONT]

---

### Post by slickymaster on 2014-12-11
The _-jar_ option only works if the JAR file is an executable JAR file, which means it must have a manifest file with a **Main-Class** attribute in it. See [Packaging Programs in JAR Files]("http://docs.oracle.com/javase/tutorial/deployment/jar/index.html") to learn how to create an executable JAR.

If it's not an executable JAR, then you'll need to run the program with something like:```
java -cp ccnChat.jar somepackage.SomeClass
```
where **somepackage.SomeClass** is the class that contains the main method to run the program.

---

