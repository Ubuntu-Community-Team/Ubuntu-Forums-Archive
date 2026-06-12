---
title: "RegEx Tools"
date: 2008-06-04
forum: Programming Talk
---

### Post by altonbr on 2008-06-04
I'm looking for some RegEx tools (not just documentation) that can help me build a regular expression and can run the regex on some test text.

Does such a tool for GNOME or on the web exist? I know of kregexpeditor, but it's finicky at best.

ie: try using this regex... /^.+\.(.+?)$/ ... and it will return an error.

---

### Post by Can+~ on 2008-06-04
Regular expressions are not standard, so depends on the language you're working on.

---

### Post by Phenax on 2008-06-04
There are some tools online.

I often use [Rubular](http://rubular.com/) for Ruby regular expressions.

---

### Post by ghostdog74 on 2008-06-04
> **altonbr said:**
> I'm looking for some RegEx tools (not just documentation) that can help me build a regular expression and can run the regex on some test text.

Does such a tool for GNOME or on the web exist? I know of kregexpeditor, but it's finicky at best.

ie: try using this regex... /^.+\.(.+?)$/ ... and it will return an error.

show how your strings look like and what you want to get.

---

### Post by altonbr on 2008-06-06
> **Phenax said:**
> There are some tools online.

I often use [Rubular](http://rubular.com/) for Ruby regular expressions.

This looks like a fantastic tool, thank you!

> **ghostdog74 said:**
> show how your strings look like and what you want to get.

ghostdog, I know you're a BASH/Perl/RegEx genius (as you've helped me on this forum a plethora of times, but I don't want to keep bugging you got each regular expression I need to make! Thank you for your kind offer however!

---

### Post by skraps on 2011-08-15
Rubular is frikin spankin awesome!

---

### Post by Habitual on 2011-08-15
[http://www.gskinner.com/RegExr/](http://www.gskinner.com/RegExr/)

---

### Post by Kreaninw on 2012-11-22
I'm trying to match user agent string via javascript. I can match Android by

```
var isAndroid = navigator.userAgent.match(/(Android)/);
```

But I have no idea how to include the number. I want to detect Android below or equal to 4.0.4 - i.e. 4.0.3, 3.2, 2.3.3, etc. How can I achieve this? Thanks! :)

---

### Post by slavik on 2012-11-22
> **Kreaninw said:**
> I'm trying to match user agent string via javascript. I can match Android by

```
var isAndroid = navigator.userAgent.match(/(Android)/);
```

But I have no idea how to include the number. I want to detect Android below or equal to 4.0.4 - i.e. 4.0.3, 3.2, 2.3.3, etc. How can I achieve this? Thanks! :)
this was a dead thread.

but to give you some pointers:
1. messy - you can use regex to put combinations of versions to do what you want.
2. better - parse out the version into actual numbers and then do comparisons/arithmetic

---

