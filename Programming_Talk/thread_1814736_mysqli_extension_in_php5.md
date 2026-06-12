---
title: "mysqli extension in php5"
date: 2011-07-30
forum: Programming Talk
---

### Post by allan_ong on 2011-07-30
[FONT=Arial][SIZE=3]I'm using an Asus EEE 1215B running Ubuntu 11.x (Natty Narwhal) with apache2, mysql and php5.3.5.

I got the following error:

[/SIZE][/FONT][FONT=Arial][SIZE=3]Fatal error: Class 'mysqli' not found in /public_html/DocCon/DocConPHP/db_fns.php on line 22 [/SIZE][/FONT]
[FONT=Arial][SIZE=3]I installed php5 and mysql using the apt-get command. Should I go back and rebuild it from the source? Total newbie here... 

I have another box running Ubuntu 10.x and can do what I need to do without any problems. Any ideas on how to fix this? I suppose worst case I can just go back and reinstall Ubuntu 10.x... [/SIZE][/FONT]

---

### Post by indytim on 2011-07-30
How did you install LAMP?

IndyTim / DataMan

---

### Post by allan_ong on 2011-07-30
Sorry -- what do you mean by LAMP? I'm a total newbie when it comes to Linux (well, I've used it before but never actually configured my environment)...

---

### Post by Bachstelze on 2011-07-30
LAMP is an acronym for Linux Apache MySQL PHPH, basically he's asking how you installed Apache, MySQL and PHP.

---

### Post by SeijiSensei on 2011-07-30
Probably this will help:

```
sudo apt-get install php5-mysql
```

This package contains the PHP module that interfaces with the MySQL server.

---

### Post by Barrucadu on 2011-07-30
Uncomment the mysqli extension in php.ini.

---

### Post by allan_ong on 2011-07-30
> **Barrucadu said:**
> Uncomment the mysqli extension in php.ini.


I uncommented this line: "mysqli.allow_local_infile = On" and it worked. That line was the only one commented in the php.ini file. 

Indytim, I used apt-get install to install (as root, of course) all the packages, including php5-mysql.

---

### Post by vectorthorn on 2012-07-24
@allan_ong's solution worked for me as well. funny, before i switched to ubuntu i'd never even noticed that line before, and i do this stuff for a living... o_0

p.s. @allan_ong: you might want to mark this thread [SOLVED] ;)

---

### Post by chichio9000 on 2012-09-23
Thanks [allan_ong]("http://ubuntuforums.org/member.php?u=1378819")

---

