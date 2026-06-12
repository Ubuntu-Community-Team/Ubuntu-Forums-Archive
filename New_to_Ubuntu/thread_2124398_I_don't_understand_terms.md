---
title: "I don't understand terms"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by TXbirder on 2013-03-10
I am trouble shooting and a resposnse included "...comment out the top few lines...", and a result on Terminal included  "Uncomment the following two lines....

How does one COMMENT or UNCOMMENT lines?  A thesauraus does not provide an answer. 

John

---

### Post by Absolute Terror on 2013-03-10
[http://www.unix.com/unix-dummies-questions-answers/35565-commenting-lines.html](http://www.unix.com/unix-dummies-questions-answers/35565-commenting-lines.html)

Two seconds on Bing.

---

### Post by oldos2er on 2013-03-10
Generally # (or sometimes two together ##) is a comment mark, which tell the system to ignore that particular line in a given file. For an example run ```
cat /etc/apt/sources.list
```

---

### Post by lancasterjoe on 2013-03-10
You must be like me ... totally new to this :) I get something which looks like the old DOS Prompt, instead of something graphic which kooks quite like a Windows prompt - ubunto 12.10 should be quite like operating Windows, but something is amiss.

---

### Post by coldcritter64 on 2013-03-10
> **lancasterjoe said:**
> ...ubunt**u** 12.10 should be quite like operating Windows, but something is amiss.

bolding is my alteration, one to add to your systems dictionary? ;)

Please have a careful read of: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm). (I think as you are a new ubuntu user you may also be new to this forum :lol: , mar 2013... welcome ;))

@ OP, simply placing a # symbol before a line, or removing a # symbol from a line, either comments out or uncomments a line respectively as previously mentioned.

---

### Post by TXbirder on 2013-03-12
Thank you.

---

### Post by vasa1 on 2013-03-12
My two bits ...
Different file types have different ways to indicate comments. I'm familiar with the following ones.

Files with a **.rc** suffix usually have **#** at the start of a line to indicate a commented out line.
**.css** files have commented material within **/*** and ***/**.
**.html** (and .xml) files have commented material within **<!--** and **-->**.

---

### Post by schragge on 2013-03-12
There are also C++ style comments sometimes (e.g. CUPS and Apache web server configuration files): **//**

---

### Post by vasa1 on 2013-03-12
> **coldcritter64 said:**
> bolding is my alteration, one to add to your systems dictionary? ;) ...
Someone has a list of the variations ;)

---

### Post by Cheesemill on 2013-03-12
You occasionally get ; used for comments as well (php.ini).

Unless stated otherwise though you can usually assume the # is used for comments in Ubuntu configuration files.

---

