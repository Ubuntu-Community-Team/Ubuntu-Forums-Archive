---
title: "how can i set class path in ubuntu?"
date: 2009-01-21
forum: Programming Talk
---

### Post by void_void on 2009-01-21
when i  fire following command i get the following result

<JAVA_HOME>/bin/javah -o HelloWorldNative.h -jni -classpath home/jjoshi/NetBeansProjects/HelloWorld/build/classes helloworld.Main
bash: JAVA_HOME: No such file or directory

how can i set class path ?

---

### Post by jespdj on 2009-01-21
Just type "javah", and not "<JAVA_HOME>/bin/javah". Also, use "-classpath /home/..." - note the slash / before "home".

Try this:
```
javah -o HelloWorldNative.h -jni -classpath /home/jjoshi/NetBeansProjects/HelloWorld/build/classes helloworld.Main
```

JAVA_HOME is not the same as CLASSPATH. You do not normally have to set either JAVA_HOME or CLASSPATH, but if you really want to, you can add lines like this to your ~/.profile:
```
export JAVA_HOME=/usr/lib/jvm/java-6-sun
```
(assuming you're using Sun Java 6). Note, after editing your ~/.profile you have to log out and in.

---

