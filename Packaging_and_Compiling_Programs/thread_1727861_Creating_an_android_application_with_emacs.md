---
title: "Creating an android application with emacs"
date: 2011-04-13
forum: Packaging and Compiling Programs
---

### Post by yotama9 on 2011-04-13
Hi guys.

After getting used to emacs, it's hard to write code using eclipse...

I want to create an application for android phones but when I try to package it I get an error:

```
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk/lib/tools.jar
Buildfile: build.xml does not exist!
Build failed

```

I have followed this page:
[http://developer.android.com/guide/tutorials/hello-world.html](http://developer.android.com/guide/tutorials/hello-world.html)

Thanks

---

### Post by SevenMachines on 2011-04-13
Might be a silly question but does tools.jar exist?
```
$ ls /usr/lib/jvm/java-6-openjdk/lib/tools.jar
/usr/lib/jvm/java-6-openjdk/lib/tools.jar
```if not, install openjdk-6-jdk
```
$ apt-get install openjdk-6-jdk
```

---

### Post by yotama9 on 2011-04-13
you are right about the tools.jar but the build file is still needed


```
Buildfile: build.xml does not exist!
Build failed

```

---

### Post by SevenMachines on 2011-04-13
Shame you dont use eclipse because the integration with the sdk is by far the best, but it can be done easily enough other ways.
The build.xml for ant should be created when you use android to create your project. eg
```
$ android create project     --package com.android.helloandroid     --activity HelloAndroid --target 2  --path ~/Desktop/HelloAndroid 
Created project directory: /home/seven/Desktop/HelloAndroid
....
Added file /home/seven/Desktop/HelloAndroid/AndroidManifest.xml
Added file /home/seven/Desktop/HelloAndroid/build.xml
...
```Running ant from emacs with ~/HelloAndroid as the working directory should then work. Sorry i dont know exactly how thats done, its been a few years (over a decade :)) since i've used emacs

---

### Post by SevenMachines on 2011-04-13
Theres a guide at the bottom of the link you posted for command line android projects, that should allow you to set up emacs hopefully

---

### Post by yotama9 on 2011-04-17
Thanks. 

I gave up on command line developing :( but I have emacs+ plugin for eclipse.

---

