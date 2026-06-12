---
title: "Java classpath problem, i think?"
date: 2010-10-22
forum: Programming Talk
---

### Post by Auden on 2010-10-22
Hey, i tried running a java program using terminal, and this is the results:

```
durimkelmendi@ubuntu:~/srcAllDummysRemoved/bin$ java -classpath -Xmx512m client
Exception in thread "main" java.lang.NoClassDefFoundError: client
Caused by: java.lang.ClassNotFoundException: client
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: client.  Program will exit.

```Yes there is a file named client in there, and it's the class file.

This is my /etc/environment:
```
JAVA_HOME="/usr/local/Java/jdk1.6.0_22"
CLASSPATH="/usr/local/Java/jdk1.6.0_22/lib:."
```

---

### Post by mainerror on 2010-10-22
Do you have a package statement in your Java file?

---

### Post by Auden on 2010-10-22
> **mainerror said:**
> Do you have a package statement in your Java file?
I don't know, i'm new to Ubuntu.

---

### Post by Some Penguin on 2010-10-23
If you don't know what a Java package is, and that it has nothing whatsoever to do with Ubuntu, you should probably first bother opening up a basic book on Java.  Online forums are not an excuse to avoid work.

---

### Post by Auden on 2010-10-23
> **Some Penguin said:**
> If you don't know what a Java package is, and that it has nothing whatsoever to do with Ubuntu, you should probably first bother opening up a basic book on Java.  Online forums are not an excuse to avoid work.
I know what a package is, it's a way to organize all the files to different directories. And yeah no they are not packaged, the files are in the same directory as the sh file. I just misunderstood his concept :P

---

### Post by mainerror on 2010-10-23
> **Auden said:**
> I know what a package is, it's a way to organize all the files to different directories. And yeah no they are not packaged, the files are in the same directory as the sh file. I just misunderstood his concept :P

No, I'm talking about a package statement in your .java file.

---

### Post by wkhasintha on 2010-10-23
'client' must also be the Class name , not only the File name . make sure

---

### Post by mainerror on 2010-10-23
> **wkhasintha said:**
> 'client' must also be the Class name , not only the File name . make sure

Indeed. You should also start you class name uppercase by convention.

Like this. File name: **T**est.java

```

// your important imports

public class Test {
    // some useful methods
}

```

---

### Post by wkhasintha on 2010-10-23
> **mainerror said:**
> Indeed. You should also start you class name uppercase by convention.

Like this. File name: **T**est.java

```

// your important imports

public class Test {
    // some useful methods
}

```

Exactly bro...

---

### Post by Auden on 2010-10-25
> **wkhasintha said:**
> Exactly bro...
Everything is correct, i've double checked, there are no problems running that java program through windows 7, i'm only experiencing this problem with ubuntu.

---

### Post by spjackson on 2010-10-25
> **Auden said:**
> 
```

durimkelmendi@ubuntu:~/srcAllDummysRemoved/bin$ java -classpath -Xmx512m client


```Everything is correct, i've double checked, there are no problems running that java program through windows 7, i'm only experiencing this problem with ubuntu.
Why are you specifying an empty classpath?

Note that the -classpath option overrides CLASSPATH in the environment. It also inhibits the default classpath of the current directory which would be used if neither CLASSPATH nor -classpath is used.

---

### Post by Auden on 2010-10-25
> **spjackson said:**
> Why are you specifying an empty classpath?

Note that the -classpath option overrides CLASSPATH in the environment. It also inhibits the default classpath of the current directory which would be used if neither CLASSPATH nor -classpath is used.
Is there any way to add it or run a java file without it? because if i run without it, i get this:
```
durimkelmendi@ubuntu:~/srcAllDummysRemoved/bin$ java -xmx512m client
Unrecognized option: -xmx512m
Could not create the Java virtual machine.

```

---

### Post by spjackson on 2010-10-25
> **Auden said:**
> Is there any way to add it or run a java file without it? because if i run without it, i get this:
```
durimkelmendi@ubuntu:~/srcAllDummysRemoved/bin$ java -xmx512m client
Unrecognized option: -xmx512m
Could not create the Java virtual machine.

```
That's because there is no such option that begins with a lowercase x. What you probably mean is:
```

$ java -Xmx512m client

```which begins with an uppercase X.

---

### Post by Zymus on 2010-10-25
1. That RuneScape client is very inefficient. I'm assuming you're wanting to add new Items, Objects, or NPCs. In that case, [http://www.moparscape/org/smf](http://www.moparscape/org/smf)
2. If you specify the "-classpath" or "-cp" VM argument, you have to specify a classpath. By default, Java looks in the './' directory. And in this case, you don't need to specify the classpath. I'm also assuming it's a 317 client. In that case i believe you must also run the client like so:
> 
java client 0 0 lowmem members 32
java client <world-id> <port-offset> <lowmem|highmem> <free|members> <signlink(ie. .file_store_<signlink>)>
3. -Xmx512m. The first 'X' is capitalized. 
4. Java is a platform independent language. There for the problems have nothing to do with the operating system.
5. Also, if you're running Java on an x64(64-bit) system, then you will run into a problem when running the client. You will be able to click the "Game area"(not game frame) twice before java segfaults and crashes. You can click the inventory, equipment, quest, etc tab, and the chat box without crashing. But when you click like, the mini map, or the rendered game region, it will crash. The exact reason isn't known but some theories are a bug in the JVM hotspot, or a bug in the client's walking algorithm.

---

