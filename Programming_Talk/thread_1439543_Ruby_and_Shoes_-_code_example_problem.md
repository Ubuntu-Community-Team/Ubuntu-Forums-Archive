---
title: "Ruby and Shoes - code example problem"
date: 2010-03-26
forum: Programming Talk
---

### Post by samjh on 2010-03-26
I'm pretty new to Ruby, and have encountered a problem with one of the code examples for Shoes.  The problem is with the Clock example here: [http://shoes.heroku.com/](http://shoes.heroku.com/)

The error is in the third line:
```
every 1 do
```
The Shoes interpreter says "undefined method 'every'".

Google searches aren't helping, because "every" is such a common word, although I've come across other code examples on the web that use the "every" keyword.  Could someone enlighten me, please?

---

### Post by stylishpants on 2010-03-26
"every" is not a built-in keyword of ruby.  It must be a method definition from shoes.

Probably you need to 'require' some library before that code will work.

---

### Post by samjh on 2010-03-26
That's strange, because none of the code examples use 'require' - on the Shoes official website or other websites.  Also, the "every" method is used in non-Shoes applications too.

---

