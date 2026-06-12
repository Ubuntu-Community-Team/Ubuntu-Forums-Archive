---
title: "how specific class into jar"
date: 2011-09-15
forum: Programming Talk
---

### Post by newelfik on 2011-09-15
Hello,

I'm losing a lot of time to success a little and basic problem.
The context:

I am developing an application using a specific .jar into path/jdk/lib

So the classpath is not fixed.. 
I've seen that -classpath option is incompatible with -jar option (i.e. MANIFEST..)

So I get an solution but not be abble to success it..

I want to access to my main.class and add path/jdk/lib in -classpath , so do not use -jar option.

In practice, I get something like that :
java -cp ./lib:/path/to/jdk/lib/tools.jar my.main.class 

I suppose I am in good directory with .jar and lib directory.

But I get always : java.lang.NoClassDefFoundError: my.main.class

What I miss ?

---

### Post by dethorpe on 2011-09-15
Can you be more specific and give the exact filenames and pathnames you are using and working in anf the actual comman line.
 
One thing that may be effecting you is that you don't put the .class extension of the main class in the java line.
 
```
 
  java -cp ./lib:/path/to/jdk/lib/tools.jar my.main

```
 
Also the directory of the class file must match the class path, so given the ./lib in the classpath, the main class file should be ./lib/my/main.class

---

### Post by ofnuts on 2011-09-15
> **newelfik said:**
> I've seen that -classpath option is incompatible with -jar option (i.e. MANIFEST..)Seen where?

---

