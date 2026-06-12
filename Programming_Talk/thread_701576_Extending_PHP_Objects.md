---
title: "Extending PHP Objects"
date: 2008-02-19
forum: Programming Talk
---

### Post by Das Oracle on 2008-02-19
I was wondering, if I have 2 classes named person and client and they are in two seperate php files, named person.php and client.php respectively....would i be able to have client extend person? if so, how would I code that? Thanks!

---

### Post by LaRoza on 2008-02-19
What version of PHP?

In PHP5, you can. [http://www.php.net/zend-engine-2.php](http://www.php.net/zend-engine-2.php)

Hint: the keyword is "extends"

---

### Post by lnostdal on 2008-02-19
make sure you load (use *require*) the one you are "extending from" first

edit:
or can php handle lazy/late resolving of this stuff? .. i dunno =)

---

### Post by Das Oracle on 2008-02-19
using php5 but when i do "client extends person" it says it can't find person to load. the php files are in lowercase and the classes are Person and Client with caps in the beginning, I don't think that is the issue though, thanks for the quick replies

---

### Post by Das Oracle on 2008-02-19
thanks LaRoza, the require was what I was missing, *used to Java, which doesn't need that part*

---

### Post by LaRoza on 2008-02-19
> **Das Oracle said:**
> thanks LaRoza, the require was what I was missing, *used to Java, which doesn't need that part*

lnostdal said that, not me.

I am not used to PHP5 OO features. My host uses PHP4, so I use that.

---

