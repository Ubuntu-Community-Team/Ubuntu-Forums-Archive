---
title: "Geany java problem!"
date: 2010-12-31
forum: Programming Talk
---

### Post by dj_ee3 on 2010-12-31
Hello, I am a web developer and a programmer and I just learned about this Geany and I think it's really cool to have one place for everything. But whenever I try to compile JAVA project an error comes up. I googled around and the solution to this problem that I saw is reinstalling/installing JDK. I did it and the error still shows up. Can anyone help me out?
Here is a screenshot [http://img143.imageshack.us/img143/8250/screenshotmn.png](http://img143.imageshack.us/img143/8250/screenshotmn.png)

---

### Post by Nytram on 2010-12-31
Hi Dj

I tried your program and it runs without error on mine.

I'm wondering if you just have the JRE installed, instead of the JDK? The former can run Java programs, while the latter is needed to program them. I'm not sure what the JDE is that you mention.

---

### Post by dj_ee3 on 2010-12-31
> **Nytram said:**
> Hi Dj

I tried your program and it runs without error on mine.

I'm wondering if you just have the JRE installed, instead of the JDK? The former can run Java programs, while the latter is needed to program them. I'm not sure what the JDE is that you mention.

Sorry for the typing mistake. I believe I have JDK installed I did it like 30 minutes ago but is there a way to check if it's installed correctly?

---

### Post by Lootbox on 2010-12-31
Try opening up Terminal and typing in 'javac' (command to compile java programs). If the JDK is installed, it should print out various usage options, not unlike the following:
```
$ javac
Usage: javac <options> <source files>
where possible options include:
  -g                         Generate all debugging info
  -g:none                    Generate no debugging info
  -g:{lines,vars,source}     Generate only some debugging info
  -nowarn                    Generate no warnings
  -verbose                   Output messages about what the compiler is doing
  -deprecation               Output source locations where deprecated APIs are used
  -classpath <path>          Specify where to find user class files and annotation processors
  -cp <path>                 Specify where to find user class files and annotation processors
  -sourcepath <path>         Specify where to find input source files
  -bootclasspath <path>      Override location of bootstrap class files
  -extdirs <dirs>            Override location of installed extensions
  -endorseddirs <dirs>       Override location of endorsed standards path
  -proc:{none,only}          Control whether annotation processing and/or compilation is done.
  -processor <class1>[,<class2>,<class3>...]Names of the annotation processors to run; bypasses default discovery process
  -processorpath <path>      Specify where to find annotation processors
  -d <directory>             Specify where to place generated class files
  -s <directory>             Specify where to place generated source files
  -implicit:{none,class}     Specify whether or not to generate class files for implicitly referenced files 
  -encoding <encoding>       Specify character encoding used by source files
  -source <release>          Provide source compatibility with specified release
  -target <release>          Generate class files for specific VM version
  -version                   Version information
  -help                      Print a synopsis of standard options
  -Akey[=value]              Options to pass to annotation processors
  -X                         Print a synopsis of nonstandard options
  -J<flag>                   Pass <flag> directly to the runtime system

```

---

