---
title: "Ubuntu Java bug"
date: 2016-10-08
forum: Programming Talk
---

### Post by virgosun on 2016-10-08
Ubuntu Java bug
My JAVA app run fine on Windows and Sierra, Lollipop, either as a naked jar or app bundle with libraries jar and jni
But in Ubuntu java -jar always: main class not found or unload-able?
what is wrong with ubuntu java?

---

### Post by dwhitney67 on 2016-10-08
A "main class not found" implies that you have not set up your CLASSPATH.  Unload-able (is that a word?) is not an error I'm familiar with.  Perhaps you built your app using version of JDK that is newer than the one on your Ubuntu system.

My suggestion, next time, post the exact errors that you are seeing.

---

### Post by virgosun on 2016-10-09
> **dwhitney67 said:**
> A "main class not found" implies that you have not set up your CLASSPATH.  Unload-able (is that a word?) is not an error I'm familiar with.  Perhaps you built your app using version of JDK that is newer than the one on your Ubuntu system.

My suggestion, next time, post the exact errors that you are seeing.
I have checked the class-path and it is correct, the class-path in the jar's manifest list all jar and jni files 
in the current working folder. The jar work well in other os.
I will check the JRE again to see if it was not up to the requirement
Thank you

---

### Post by virgosun on 2016-10-09
> **dwhitney67 said:**
> A "main class not found" implies that you have not set up your CLASSPATH.  Unload-able (is that a word?) is not an error I'm familiar with.  Perhaps you built your app using version of JDK that is newer than the one on your Ubuntu system.

My suggestion, next time, post the exact errors that you are seeing.
The app is written and built targeting Oracle Jre 1.7++
But my system run OpenJDK 1.8, is that a problem?
 ```

$ java -version
openjdk version "1.8.0_91"
OpenJDK Runtime Environment (build 1.8.0_91-8u91-b14-3ubuntu1~16.04.1-b14)
OpenJDK 64-Bit Server VM (build 25.91-b14, mixed mode)

```
and app run
```

 java -jar Send_Agent.jar 
Error: Could not find or load main class application.Main

```

and this is the app manifest

```

Manifest-Version: 1.0 
Class-Path: . Send_Agent.jar Send_Agent_lib/antlr-runtime-3.4.jar Send_Agent_lib/jackson 
 -annotations-2.8.3.jar Send_Agent_lib/jackson-core-2.8.3.jar Send_Age 
 nt_lib/jackson-databind-2.8.3.jar Send_Agent_lib/sequence-library-1.0 
 .3.jar Send_Agent_lib/sqljdbc4.jar Send_Agent_lib/sqljet-1.1.10.jar S 
 end_Agent_lib/svnkit-1.8.12.jar Send_Agent_lib/svnkit-cli-1.8.12.jar  
 Send_Agent_lib/dns_sd.jar 
Main-Class: application.Main

```

---

### Post by virgosun on 2016-10-09
Thank you
I remove OpenJDK and install Oracle Jre 1.8 and app run fine
Now I have to find a way to compile dns-sd.jar file for Ubuntu
Dont know if anyone have any idea

---

