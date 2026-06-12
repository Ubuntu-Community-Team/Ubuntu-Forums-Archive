---
title: "Python input sterilization"
date: 2012-06-26
forum: Programming Talk
---

### Post by bobman321123 on 2012-06-26
Does anyone have any advice/links on how to sterilize Python input?

---

### Post by greenpeace on 2012-06-27
hey bob, 

Depends... what are you going to do with the input?  

For interaction with a **database**, make sure you use a parameterized query and the execute() method..

Here's an example:

[http://stackoverflow.com/questions/5395290/sql-injection-prevention-in-python-is-using-parameterized-query-enough](http://stackoverflow.com/questions/5395290/sql-injection-prevention-in-python-is-using-parameterized-query-enough)

---

