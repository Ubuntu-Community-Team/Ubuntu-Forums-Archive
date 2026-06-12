---
title: "I don't know what to do with a non-executable jar archive file (did research)"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by andreygaganov0 on 2013-11-17
I have a dropbox-core-sdk-1.7.5.jar archive file. I tried to install it as a package in my Home directory with: 


  java -jar dropbox-core-sdk-1.7.5.jar


  but the terminal spits out: "no main manifest attribute, in dropbox-core-sdk-1.7.5.jar". The thread [Can't execute jar- file: "no main manifest attribute"]("http://stackoverflow.com/questions/9689793/cant-execute-jar-file-no-main-manifest-attribute")  suggests that I need to add a line similar to "Main-Class:  com.mypackage.MyClass" META-INF/MANIFEST.MF file. But I don't know what  class I'm supposed to type in.


  I've found instructions on [http://www.wikihow.com/Run-a-.Jar-Java-File](http://www.wikihow.com/Run-a-.Jar-Java-File), but they are just as confusing.


  Can someone explain to me what I should do about this non-executable  jar file so that I could let the machine know that this package exists?

---

### Post by andreygaganov0 on 2013-11-17
Update: `javac -classpath dropbox-core-sdk-1.7.5.jar Main.java` worked. `java -classpath dropbox-core-sdk-1.7.5.jar Main`, however, didn't.

---

### Post by andreygaganov0 on 2013-11-18
OK, the chat conversation with a member of StackOverflow *really* helped out. [http://stackoverflow.com/questions/20037741/cannot-install-a-jar-package-without-an-ide](http://stackoverflow.com/questions/20037741/cannot-install-a-jar-package-without-an-ide)

---

