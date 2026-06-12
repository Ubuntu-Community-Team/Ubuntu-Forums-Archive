---
title: "Javascript e-mail validation"
date: 2008-09-21
forum: Programming Talk
---

### Post by zoobave on 2008-09-21
When i search js code for a  email validation, i found the following pattern is used to validate the given email address using "test()" method. Can anybody explain me the following code?

var emailfilter=/^\w+[\+\.\w-]*@([\w-]+\.)*\w+[\w-]*\.([a-z]{2,4}|\d+)$/i

---

### Post by jespdj on 2008-09-21
It's a regular expression. See [Regular expressions in JavaScript](http://www.devarticles.com/c/a/JavaScript/Regular-expressions-in-JavaScript/), or Google for it to find more information.

---

