---
title: "Java RXTX installed from repository, how to import?"
date: 2011-05-02
forum: Programming Talk
---

### Post by jondaeh on 2011-05-02
Hi.

I am developing an application in Java, Netbeans, which is using the RXTX library for serial communication. I have got this working before by simply including the rxtx-2.2pre2.jar file in the "libraries" tab in netbeans, however now I get the error

```
java.lang.UnsatisfiedLinkError: no rxtxSerial in java.library.path thrown while loading gnu.io.RXTXCommDriver
```

And as I couldn't resolve the problem, I decided I might as well use the librxtx-java which is installed anyway with the arduino from the repositories. However, I can't get nebeans to understand that I have installed this library, as the gnu.io imports shows up as not existing.

Anyone know is this is possible to do, and if it is, how can I get netbeans to find the librxtx-java?

Thanks!

Jon, Norway

---

### Post by brpylko on 2011-05-02
I know in eclipse you can manually add libraries you want to include, there might be something similar in netbeans.

---

### Post by jondaeh on 2011-05-06
Alright, got some help and figured out how to do this.

Firstly I had to add the Java library (the .jar file) located at
```
/usr/share/java/RXTXcomm.jar
```
by right-clicking Libraries -> add Jar/Folder.

I was able to clean and build the program, but it would fail when executed.

To fix this problem, I added the line
```
-Djava.library.path="/usr/lib/jni/"
```
to the VM Options. (Right click project -> Properties -> Run). 
This is the path to the librxtxSerial.so file.

Sincerely,
Jon

---

### Post by balaqemu on 2011-11-07
Hi,

I have installed the RXTX package ubuntu JVM . 
But I get the import gnu.io * package not found error though I set all the class path of RXTXcomm.jar file and .

Pls provide the proper step to install the RXTX package .



regards

Bala

---

