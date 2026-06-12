---
title: "php include behaviour for includes from a different directory"
date: 2008-02-01
forum: Programming Talk
---

### Post by aleb on 2008-02-01
Hi,

Fact:I have 3 files: /a.php, /dir1/b.php, /dir1/c.php. a.php does **include("dir1/b.php")** and b.php does **include("c.php")**. Retrieving [http://server/a.php](http://server/a.php) shows that c.php cannot be found. The include path is ".". 

Comment: I understand this is the normal behavior, from what I read from the include documentation. I have an older apache/php setup (php 5.0.4) in which this works, the current directory does not change but the second include works just fine.

Question: What do I have to change in php.ini or elsewhere to make this code work, **without changing the code or moving the files or editing the include path**? 

I read the include documentation and I searched on forums but could not find an answer. I stared at the two php.ini files, but I cannot see what could alter the include behaviour. Any suggestions?

Thanks!

---

### Post by LaRoza on 2008-02-01
I realize you probably aren't looking for this, but can't you use absolute paths or server relative? It would make things easier.

---

### Post by aleb on 2008-02-01
> **LaRoza said:**
> I realize you probably aren't looking for this, but can't you use absolute paths or server relative? It would make things easier.
I only want to understand why the Ubuntu (Debian) installation behaves differently, and what causes the different behaviour.

---

### Post by LaRoza on 2008-02-01
a.php includes /dir1/b.php.

Then, /a.php includes /c.php, which is in /dir1/.

It is a case of the includes being executed after they are included.

That is they way I would expect it to work.

The contents of the includes are parsed after they are included.

---

### Post by aleb on 2008-02-01
> **LaRoza said:**
> a.php includes /dir1/b.php.

Then, /a.php includes /c.php, which is in /dir1/.

It is a case of the includes being executed after they are included.

That is they way I would expect it to work.

The contents of the includes are parsed after they are included.
Thanks! Good point. 

What you say is true for **Apache/2.2.4 (Ubuntu) mod_fastcgi/2.4.2 PHP/5.2.3-1ubuntu6.3** but not for **Apache/2.2.6 (FreeBSD) PHP/5.2.5**. 

I could uninstall Ubuntu's php version and try the latest to see how that one performs.

---

### Post by LaRoza on 2008-02-01
> **aleb said:**
> Thanks! Good point. 

What you say is true for **Apache/2.2.4 (Ubuntu) mod_fastcgi/2.4.2 PHP/5.2.3-1ubuntu6.3** but not for **Apache/2.2.6 (FreeBSD) PHP/5.2.5**. 

I could uninstall Ubuntu's php version and try the latest to see how that one performs.

Glad the differences were sorted out.

---

### Post by aleb on 2008-02-02
I tried the last stable php version: **Apache/2.2.3 (Ubuntu) PHP/5.2.5** (on Feisty, if that matters), and it acts differently than the default PHP installation on Gutsy:
```
aleb@feisty:/var/www$ cat a.php
a<?php include "a/b.php"; ?>
aleb@feisty:/var/www$ cat a/b.php
b<?php include "c.php"; ?>
aleb@feisty:/var/www$ cat a/c.php
c
```This prints "abc".

Any idea what causes the different behaviour?

---

### Post by aleb on 2008-02-04
**Apache/2.2.4 (Ubuntu) mod_fastcgi/2.4.2 PHP/5.2.5** on Gutsy acts differently than **Apache/2.2.3 (Ubuntu) PHP/5.2.5** on Feisty. The first one gives an error, the second one manages to find the third include file and prints "abc".

I'll stop here with my investigation, even though it's somewhat annoying to use a virtual machine only to run an apache + php.

---

