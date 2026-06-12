---
title: "How to execute .jar files"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by X D face me on 2012-06-20
Hello everyone

I've downloaded an executable .jar file from the internet and i would like to run it, but when i select open with other application, the java 7 runtime environment isn't in the list of programs. When i head to [http://java.com/en/download/installed.jsp?](http://java.com/en/download/installed.jsp?) (to detect wich version of java i have) it says: You have the recommended Java installed (Version 7 Update 5). Also when i type in my terminal: java -version, it says: 

java version "1.7.0_05"
Java(TM) SE Runtime Environment (build 1.7.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 23.1-b03, mixed mode)

When i try to run it through google chrome, it downloads the file again. Does anyone know how to solve this problem?

X D face me

---

### Post by pissedoffdude on 2012-06-20
I think you should be able to run it with custom command 'java' or 'java -jar'

If not, simply run```
java -jar file.jar
```

---

### Post by z3nhakr on 2012-06-20
do you have JRE (java runtime edition) installed? it is different from java web start. if not download it from software center

---

### Post by X D face me on 2012-06-20
> **z3nhakr said:**
> do you have JRE (java runtime edition) installed? it is different from java web start. if not download it from software center

there's only an openjdk 7 in the software center, which represents java 6. where can i download jre and how can i install it.

---

### Post by jldoll on 2012-06-20
I use Lubuntu so I'm not sure what software center calls the package.  Lubuntu software  center calls it openjdk java 7 runtime which is openjdk-7-jre is you read the details. If you use synaptic package manager which I believe is installed by default with all distros it's listed as openjdk-7-jre.

---

### Post by X D face me on 2012-06-20
the openjdk 7 on the software center of ubuntu i similar to jre 6

---

### Post by pissedoffdude on 2012-06-20
You should be fine with that version.  Have you tried running the jar in the terminal with the command mentioned above?

Run the above-mentioned command and let us know if you're still getting an error.  Also, you can drag and drop the file into the terminal after typing 'java -jar' if you're not sure how to input its location into the terminal

---

### Post by X D face me on 2012-06-20
> Originally Posted by pissedoffdude  
You should be fine with that version. Have you tried running the jar in the terminal with the command mentioned above?

Run the above-mentioned command and let us know if you're still getting an error. Also, you can drag and drop the file into the terminal after typing 'java -jar' if you're not sure how to input its location into the terminal
thank you, it works. topic can now be closed

---

### Post by X D face me on 2012-06-20
> **pissedoffdude said:**
> You should be fine with that version.  Have you tried running the jar in the terminal with the command mentioned above?

Run the above-mentioned command and let us know if you're still getting an error.  Also, you can drag and drop the file into the terminal after typing 'java -jar' if you're not sure how to input its location into the terminal

thank you, it works. topic can now be closed

---

