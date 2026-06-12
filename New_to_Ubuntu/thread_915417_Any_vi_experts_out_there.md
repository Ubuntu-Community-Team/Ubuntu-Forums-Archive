---
title: "Any vi experts out there?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by WelshChris on 2008-09-09
I'm trying to delete all occurrences of '.' (i.e. one full-stop) in a document.  I'm trying to use global search and replace with

:%s/.//g

Which, of course, doesn't work.

Any help?

---

### Post by Pro-reason on 2008-09-09
The dot is a regular-expression thingy.  You have to escape it with a backslash if you want to use it literally.

```

:%s/[COLOR="Red"]\.[/COLOR]//g

```

More specifically, the dot represents &#8220;any character&#8221;; so, using it unescaped in your example will delete the entire file.

See [http://www.zytrax.com/tech/web/regex.htm#intro](http://www.zytrax.com/tech/web/regex.htm#intro)

---

### Post by WelshChris on 2008-09-10
Ah, of course.  Thanks.  I'll need to dig out my Mastering Regular Expressions manual..

---

### Post by Pro-reason on 2008-09-11
Happy to help out.

Perhaps you could use the &#8220;Thread Tools&#8221; menu to mark this as Solved.

---

