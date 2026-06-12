---
title: "Running 317 RSPS client using shell not .bat"
date: 2013-02-22
forum: Programming Talk
---

### Post by Ahmedo0o on 2013-02-22
Hi, this is my first post in this forums 

I'm kinda new to Ubuntu and I used to play RSPS ( runescape private server ) on windows 7, now when I updated to ubuntu I noticed that I can't run .bat other than using a program called wine which I didn't like, so I need to create a .sh file to run the client 

this is the run.bat

```
@ECHO OFF
color 81
echo Dragon-History Client
echo Made by Aintaro
JAVA -Xmx500m EGUI
```

and this is my shell command that I made

```
#!/bin/bash

JAVA -Xmx500m EGUI
```

now when I run the run.sh it opens and closes fast .. *I use run in terminal*

---

### Post by albandy on 2013-02-22
Linux is case sensitive, change JAVA to java, also I recommend you to do the tests in an previous opened terminal.

---

### Post by Ahmedo0o on 2013-02-22
> **albandy said:**
> Linux is case sensitive, change JAVA to java, also I recommend you to do the tests in an previous opened terminal.

okay I changed JAVA to java and the client showed up 
but I get this error in the terminal 

```
Error: loaderror Starting up 20
urlstream
```

---

### Post by albandy on 2013-02-22
> **Ahmedo0o said:**
> okay I changed JAVA to java and the client showed up 
but I get this error in the terminal 

```
Error: loaderror Starting up 20
urlstream
```

Check what jvm are you using:
java -version

---

### Post by Ahmedo0o on 2013-02-22
> **albandy said:**
> Check what jvm are you using:
java -version

```
java version "1.7.0_15"
Java(TM) SE Runtime Environment (build 1.7.0_15-b03)
Java HotSpot(TM) Server VM (build 23.7-b01, mixed mode)
```

---

### Post by Ahmedo0o on 2013-02-22
> **albandy said:**
> Check what jvm are you using:
java -version

Btw, I think It's something about the cache getting ..
cuz in the server I couldn't run it until I changed "config\\" to "config//"

---

### Post by Perfect Storm on 2013-02-22
I'm moving this thread from Gaming to Programming talk. You might get better help there.

regards
A.I.

---

### Post by Ahmedo0o on 2013-02-22
> **Artificial Intelligence said:**
> I'm moving this thread from Gaming to Programming talk. You might get better help there.

regards
A.I.

Okay, thanks

---

### Post by albandy on 2013-02-26
Where can I download the program you're trying to run?

---

