---
title: "Ajax Books"
date: 2007-08-17
forum: Programming Talk
---

### Post by rock freak on 2007-08-17
Morning everyone,

I am looking about the tinternet at the moment looking for books on Ajax and Ajax with PHP.

Have been looking at the O'Reilly one as I loved their practical C book, but didn't know if any of you could recommend any other!!

My main use for Ajax will be to integrate it with PHP and MySql if this helps!!

Cheers 
Ollie

---

### Post by pmasiar on 2007-08-17
O'Relly books are very good -- I don't recall a dud from them. And they have excellent intro books series - "Head-First", I read 2 or 3 books from series and they are good, so I would recommend [http://www.oreilly.com/catalog/headra/](http://www.oreilly.com/catalog/headra/) even without reading it :-)

You will need another book as reference (deeper one), but I would advise to pick a javascript/AJAX library instead and just use that. Check with PHP people what they prefer, or switch to real programming language like Python and Django or Turbogears.

OK bonus link why PHP sucks: because it leads to creating hard to maintain code mess, when you mix in one file presentation, processing logic, and data access. Use [Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) approach to create cleaner code.

---

### Post by LaRoza on 2007-08-17
> **pmasiar said:**
> OK bonus link why PHP sucks: because it leads to creating hard to maintain code mess, when you mix in one file presentation, processing logic, and data access. Use [Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) approach to create cleaner code.
Bonus post, why PHP doesn't suck:

* It can be clean, depending on who is coding (I don't mix anything)
* It is well supported
* Finding a PHP host is easy, and many times, free. (freehostia.com, for one, no ads)
* It is a recursive acronym, most recursive acronyms are cool :D.

---

### Post by pmasiar on 2007-08-17
I agree that PHP **can** be done clean but not many beginners do it, so... But Turbogears nudges you gently to wards good structure without any pain - it generates project structure for you.

And please don't hijack thread with OT questions, post question about Python/vista errors separately :-)

---

### Post by LaRoza on 2007-08-17
> **pmasiar said:**
> I agree that PHP **can** be done clean but not many beginners do it, so... But Turbogears nudges you gently to wards good structure without any pain - it generates project structure for you.
)

On [http://en.wikipedia.org/wiki/Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller), which you often cite, there are MVC frameworks for PHP.

---

### Post by pmasiar on 2007-08-17
> **LaRoza said:**
> there are MVC frameworks for PHP.

Yes, they are - but how many people actually use them? PHP style does not allow for clean MVC code without extra efforts, and constant vigilance. Many people don't see why, and don't have time.

Let's allow OP to decide if clean MVC approach is something she is interested. Chances are, not much ... :-(

OK I apologise for "PHP sucks". :-)

---

### Post by LaRoza on 2007-08-17
> **pmasiar said:**
> 
OK I apologise for "PHP sucks". :-)

Apology accepted :-)

To the OP:

I haven't use Ajax, but the books I have seen, used it with PHP, so a quick look through an Ajax book, may be the best way to tell.

This article may help (I don't know how much you know, so it might not) [http://www.webreference.com/programming/javascript/kh/](http://www.webreference.com/programming/javascript/kh/)

---

