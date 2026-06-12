---
title: "javascript split"
date: 2008-08-07
forum: Programming Talk
---

### Post by g3k0 on 2008-08-07
Hi, I am having a little difficulty with split.  I run into a problem when there are two delimeters in a row.  For instance if I was doing a split like this str.split(",") where str = a,b,,c,d it will return "a" "b" "c" and "d" but what I want is "a" "b" "" "c" "d"

Is there an easy way to get this rather than manually going through a string checking character by character?

Thanks

---

### Post by mssever on 2008-08-07
> **g3k0 said:**
> Hi, I am having a little difficulty with split.  I run into a problem when there are two delimeters in a row.  For instance if I was doing a split like this str.split(",") where str = a,b,,c,d it will return "a" "b" "c" and "d" but what I want is "a" "b" "" "c" "d"

Is there an easy way to get this rather than manually going through a string checking character by character?

Thanks
In firebug:
```
>>> str = 'a,b,c,,d'
"a,b,c,,d"
>>> str.split(',')
["a", "b", "c", "", "d"]
```
EDIT: You can also split on regular expressions: ```
str.split(/,/)
```

---

### Post by g3k0 on 2008-08-07
well.  I am doing this for IE, not sure if split is different there.  I also simplified my split and sample string to make it easier to understand so maybe something changed the result between my changing the data and browser.  Here is what I am working with 

contents = strContents.split(/\".\"|\"\n\"|\"\n\n\"/g) 

one of the things it is looking for is "," (quotes included) but when two are in a row  ",""," it doesn't give me an empty string for between them

---

### Post by g3k0 on 2008-08-08
so is this a lost cause? :(

---

### Post by mssever on 2008-08-08
> **g3k0 said:**
> so is this a lost cause? :(
Surely not, but I don't know much about scripting in IE. You might be better off asking in forums that are focused on web development. They'd probably be more familiar with IE's quirks.

---

### Post by pmasiar on 2008-08-09
Another approach to deal with IE quirks is to switch from plain JS to a JS library like dojo, jQuery, scriptaculous etc and use their functions, which deal with (and hide) differences JS between IE and FF.

---

