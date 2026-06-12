---
title: "Why does egrep &quot;[0-9*]&quot; f.txt not show the lines with no digits whatsoever in them?"
date: 2017-03-27
forum: Programming Talk
---

### Post by s3a on 2017-03-27
Hello, everyone. :)

Why does egrep "[0-9*]" f.txt not show the lines with no digits whatsoever in them (in addition to showing the lines with digits in them)?

When I do egrep "[0-9+]" f.txt, it outputs the same as when I put a *, instead of a +.

Having said that, when I do egrep "[^0-9]" f.txt to show only lines without numbers, it works as I intend.

Could someone please help me figure out why the * is not working as I intend?

---

### Post by TheFu on 2017-03-27
In your example, it matches 0-9 and the '*' character because it is inside the brackets.
The same applies to the '+' inside brackets - it doesn't mean at least 1 match in that case.

BTW, there are different regex engines on Linux. I always have to look up which constructs work in grep, egrep, perl and sed. They are all slightly different regex languages.

Usually **egrep '[0-9]*' file** is used ... notice where the * is (outside the brackets) and notice how single-quotes are used to prevent aggressive shell filename expansion.

---

### Post by s3a on 2017-03-27
That was very helpful! Thanks!

---

