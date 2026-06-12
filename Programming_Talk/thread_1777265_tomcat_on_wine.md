---
title: "tomcat on wine"
date: 2011-06-07
forum: Programming Talk
---

### Post by bigdidz on 2011-06-07
Hello there,

At my job, we are developing a program in Java that connect to Excel to web page.  Indeed, we are only working on Windows but I cannot live with that any more.  Windows just suck!

Hence, I'm trying the impossible here: develop a program that depend heavily on Windows and Excel under Linux.

My goal is to "Wine" my entire project.  I have a "wined" jdk and  I already "Wined" netbeans and it works like a charm.

My last problem is tomcat.  I need to start tomcat from wine and it does not work.  I run the command catalina.bat jpda start (to debug tomcat) and here is the log that I have.

> 
Using CATALINA_BASE:   C:\_easa\trunk\server\tomcat
Using CATALINA_HOME:   C:\_easa\trunk\server\tomcat
Using CATALINA_TMPDIR: C:\_easa\trunk\server\tomcat\temp
Using JAVA_HOME:       C:\Program Files\Java\jdk1.6.0_25
File not found

File not found

File not found

File not found

Usage:  catalina ( commands ... )
commands:
  debug             Start Catalina in a debugger
  debug -security   Debug Catalina with a security manager
File not found

  jpda start        Start Catalina under JPDA debugger
  run               Start Catalina in the current window
  run -security     Start in the current window with security manager
  start             Start Catalina in a separate window
  start -security   Start in a separate window with security manager
  stop              Stop Catalina
  version           What version of tomcat are you running?


I know the problem comes from catalina.bat around those lines
```

if ""%1"" == ""debug"" goto doDebug

if ""%1"" == ""run"" goto doRun

if ""%1"" == ""start"" goto doStart

if ""%1"" == ""stop"" goto doStop

if ""%1"" == ""version"" goto doVersion

```

My question is:  what's missing there?  How can I know what files are missing?

Thanks a lot!

Didier Amyot

---

