---
title: "sqldeveloper - startup issues"
date: 2007-03-13
forum: Programming Talk
---

### Post by hibernatus on 2007-03-13
Hi,

I just have download the latest sqldeveloper version an tried to lauch it.

i have  download the version  sqldeveloper-1.1.2.2579-no-jre.zip

> unzip  sqldeveloper-1.1.2.2579-no-jre.zip

then go to the directory 

cd sqldeveloper

change the permission on the sqldeveloper.sh
> 
chmod +x sqldeveloper.sh

and try to lauch it 
> 
./sqldeveloper.sh

then i get the following error 

> Addin: Translator PlSql is trying to register a input type (.plsql) which conflicts with translator PlSql who already using this input type


Can some one help me?
hibern

---

### Post by hibernatus on 2007-03-20
Anny body can help me????

---

### Post by freakinduck on 2007-03-30
also having the same issue here, but i suspect that that error isn't the culprit.

The UI frame appears, but there is no java ui presented...

it's just a ghost of a shell....  no response, and no exceptions in terminal window after launch except the "to register a input type (.plsql)" error

---

### Post by dyno_fu on 2007-04-04
same problem, any idea?

---

### Post by dyno_fu on 2007-04-04
it turns out if i turn off the desktop effect, sqldeveloper works as usual:)

---

### Post by hibernatus on 2007-04-12
Hi,

I have allso try with out beryl and then it was working 

:-(

---

### Post by troach on 2007-05-25
> **dyno_fu said:**
> it turns out if i turn off the desktop effect, sqldeveloper works as usual:)

If youw ant SQL Developer to work with Beryl then you need to edit the sqldeveloper.sh file that you use to launch sql developer. You need to insert this line in between the shell to use and the line that executes sqldeveloper.

export AWT_TOOLKIT=MToolkit

This is how it should look.


#!/bin/bash
**export AWT_TOOLKIT=MToolkit**
cd "`dirname $0`"/sqldeveloper/bin && bash sqldeveloper $*

---

### Post by bated_breath on 2007-06-07
Thank you troach fixed sqldeveloper on Edgy with Beryl & XGL.

---

### Post by Cold-Gin on 2007-07-11
Thank you very much! Troach's script modification works for Feisty also.

---

### Post by burnechr on 2007-07-16
Worked like a champ...  Thanks!!!

---

### Post by DSn0wMan on 2007-08-11
For some reason the the export line works, but I cant enter any text in the SQL statement box. It works fine without compiz-fusion running.

---

### Post by bmw330i on 2007-09-11
Hey all,

My first chance to post :)

Nothing listed here worked completely. JAVA_HOME did need to be set but not until after I (synaptic package manager) installed EVERYTHING in the jdk6 find list for jdk

My exact steps (read all of them before starting):
 1. Open Synaptic Package Manager
 2. search for "jdk"
 3. checked to install: sun-java6-bin, sun-java6-demo, sun-java6-doc, sun-java6-javadb, sun-java6-jdk, sun-java6-jre, sun-java6-source (I admit likely you don't need everything)
 4. the terminal complained it needed a root owned file in /tmp named: jdk-6-doc.zip and that you download it from: [https://sdlc3b.sun.com/ECom/EComActionServlet;jsessionid=1FD3F1170694C51E831C41166F3C41F7](https://sdlc3b.sun.com/ECom/EComActionServlet;jsessionid=1FD3F1170694C51E831C41166F3C41F7)
or
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) and click the "Documentation" button, accept lic. agreement, download it to /tmp/
I suggest do the download to tmp first chown to root then do step 1 above.and avoid this issue.
5. after finished installing exit S.P.M.
6. export JAVA_HOME=/opt/SDK/jdk
7. I put my sqldeveloper in /usr/local/share so my command is: 
"/usr/local/share/sqldeveloper/sqldeveloper/bin/sqldeveloper"
NOTE: there is a sqldeveloper.sh script that for me doesn't work so I am calling the binary directly. I suggest creating a symlink to it in /usr/local/bin 
"ln -s /usr/local/share/sqldeveloper/sqldeveloper/bin/sqldeveloper /usr/local/bin/sqldeveloper"

At this point I launch it with: 
"export JAVA_HOME=/opt/SDK/jdk; sqldeveloper"

Works for me...hope this helps anyone who didn't find the above worked like me. 

-D

---

### Post by the_who on 2007-09-26
i'm trying to install sqldeveloper on my feisty
begin with extract file : 

sqldeveloper-1.2.1.3213-no-jre.zip

but when i'm enter this command :

$ ./sqldeveloper.sh

this error appear :

Oracle SQL Developer
 Copyright (c) 2006, 2007, Oracle. All rights reserved.  

WARNING: error instantiating 'java.util.logging.FileHandler,' referenced by handlers, class not found
java.lang.ClassNotFoundException: java.util.logging.FileHandler,
   <<No stacktrace available>>
Exception during runtime initialization
java.lang.ExceptionInInitializerError
   <<No stacktrace available>>
Caused by: java.lang.NullPointerException
   <<No stacktrace available>>
vandread@quick:/media/sda4/download/sqldeveloper$ 

anybody can give me solution for those problem?

---

### Post by the_who on 2007-09-26
i'm so sory repost

---

### Post by destiney on 2007-11-19
Worked for me, thanks.

---

### Post by slusig on 2008-05-03
Anyone able to get SQL Developer to work with Hardy?

With effects turned off, it seems to work.  With effects turn on, I get a grey, blank window after it starts startup.  

I tried adding "export AWT_TOOLKIT=MToolkit" to sqldeveloper.sh as described in a previous post, but it didn't seem to work.

Anyone have any ideas?

---

### Post by terjelm on 2008-05-05
You must disable compiz for sqldeveloper (and jdeveloper) to work.

---

