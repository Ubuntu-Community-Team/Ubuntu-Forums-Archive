---
title: "Automagic HTML tags parser for python/django"
date: 2011-07-30
forum: Programming Talk
---

### Post by kvv_1986 on 2011-07-30
Hello,

I am attempting to create a simple blogging platform using Django. Is there an API or module or something that will automagically parse a limited set of HTML tags, for displaying formatted content in comments or posts?

It is not beyond my ability to build a simple parser, but that I want to avoid doing it if possible due to obvious reasons.

I am still a newbie, so please pardon me if there is an obvious answer to my question. :p

---

### Post by soltanis on 2011-07-30
[https://docs.djangoproject.com/en/dev/topics/templates/](https://docs.djangoproject.com/en/dev/topics/templates/)

---

### Post by kvv_1986 on 2011-08-02
Thanks. But if I read that right, by default it either autoescapes everything or nothing. I will still have to create custom filters to enable or disable certain tags, am I right?

For instance, I want to allow < b> < p>, but not < script>.

---

### Post by slavik on 2011-08-02
if you want to allow your users to do tags (similar to how this forum does), do what this forums does ... bbcode.

---

### Post by LemursDontExist on 2011-08-03
There are a number of libraries you can use.  BBCode is good, but python support for it isn't great.  I'd recommend using markdown or textile for which a nice [Django module]("https://bitbucket.org/carljm/django-markitup/src") already exists.

---

