---
title: "Syntax error when trying to get objects in other objects [PHP]"
date: 2008-01-20
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2008-01-20
Hi,

I have an object called *Something* and it has another object in it called *AnotherThing*. AnotherThing object has a method called *DoSomething* which returns a string. I try to reach that method like this:

[PHP]echo $Something->AnotherThing->DoSomething();[/PHP]

And it works on my localhost, however the web sites I uploaded the script gives a syntax error like:

*Parse error: syntax error, unexpected T_OBJECT_OPERATOR, expecting ',' or ';' in ...*

Is there another way to do this?

---

### Post by ZuLuuuuuu on 2008-01-20
Ok, I found out that syntax was not supported by PHP4 and my hosting uses PHP4 by default. I have them install PHP5 and the problem solved. But if there is a better syntax which PHP4 and PHP5 both supports then I appreciate learning it?

---

### Post by LaRoza on 2008-01-20
> **ZuLuuuuuu said:**
> Ok, I found out that syntax was not supported by PHP4 and my hosting uses PHP4 by default. I have them install PHP5 and the problem solved. But if there is a better syntax which PHP4 and PHP5 both supports then I appreciate learning it?

The OO in PHP4 is really simple. PHP5 is more complete, and not backwards compatible.

PHP5 does OO nice, PHP4 just has a way to define a class with a constructor.

---

