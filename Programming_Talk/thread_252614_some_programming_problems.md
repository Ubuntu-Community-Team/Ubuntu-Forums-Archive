---
title: "some programming problems"
date: 2006-09-07
forum: Programming Talk
---

### Post by Zacharias on 2006-09-07
Hi guys, 

I have some problems about programming. 

I want to write a programme in delphi, java, C, C++, php

I setup anjuta and eclipse for that, but unfortunately i couldnt handle it. i wrote basic C codes and tried to compile, but even i saved the file, the debug or compile options wansnt active in IDE.

The other question is about PHP, is it enough to setup php4, mysql, apache and phpmyadmin by apt-get? or should i something more?

the last question is about delphi. how can write and compile delphi.net in linux. 

Thanks a lot. Sorry for my english

---

### Post by ifokkema on 2006-09-07
> **Zacharias said:**
> I want to write a programme in delphi, java, C, C++, php

I setup anjuta and eclipse for that, but unfortunately i couldnt handle it. i wrote basic C codes and tried to compile, but even i saved the file, the debug or compile options wansnt active in IDE.
I don't know eclipse, but I do know that Ubuntu doesn't come with compilers by default. Install them first, and try again.
```
sudo apt-get install build-essential
```

> **Zacharias said:**
> The other question is about PHP, is it enough to setup php4, mysql, apache and phpmyadmin by apt-get? or should i something more?
All you need is:
```
sudo apt-get install apache libapache-mod-php4 mysql-server php4-mysql phpmyadmin
```
Everything should work automatically then. You can also pick Apache2 and/or PHP5 and/or MySQL 4.1. Note that I never used PHPMyAdmin, so I don't know about the install process.

HTH

---

### Post by Zacharias on 2006-09-07
even i setup the build essential pocket, i still cannot compile c code with anjuta ide.

---

### Post by ifokkema on 2006-09-11
Hi,

Been away for a couple of days, so just read your post. If the problem persists, possibly you're missing one of the 'Recommended' or 'Suggested' packages. Possibly a search on the forums or Google helps you out, since I never work with Anjuta or Eclipse.

---

### Post by X.Cyclop on 2006-09-11
[Apache + PHP + MySQL + phpMyAdmin + MySQL Admin]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Try another IDE (Code::Blocks).

;)

---

### Post by eha1990 on 2006-09-11
Does anyone know how to install Java Advanced Imaging?

I've followed the directions located at [http://java.sun.com/products/java-me...ALL-1_1_2.html](http://java.sun.com/products/java-me...ALL-1_1_2.html)

I downloaded the Java Advanced Imaging files at
[http://java.sun.com/products/java-me...oad-1_1_2.html](http://java.sun.com/products/java-me...oad-1_1_2.html)

---

### Post by ifokkema on 2006-09-12
> **eha1990 said:**
> Does anyone know how to install Java Advanced Imaging?

I've followed the directions located at [http://java.sun.com/products/java-me...ALL-1_1_2.html](http://java.sun.com/products/java-me...ALL-1_1_2.html)

I downloaded the Java Advanced Imaging files at
[http://java.sun.com/products/java-me...oad-1_1_2.html](http://java.sun.com/products/java-me...oad-1_1_2.html)

You're stealing someone else's thread. Bottom line: this is an unrelated question and it will not very likely be responded to. Please start a new thread, and include information about what went wrong (errors?).

---

### Post by junglepeanut on 2006-09-12
I am sorry to ask this but I just want to make sure I understand the issue.

You are using and IDE, in this IDE you can not compile by clicking on the compile button. 

If this is true, I ask "Does it compile from the command line?"

Sorry, I don't use the IDE you mentioned but I am trying to help.
And maybe able to give some information if I understand completely the issue.

---

