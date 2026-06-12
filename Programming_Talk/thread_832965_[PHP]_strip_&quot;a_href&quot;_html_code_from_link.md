---
title: "[PHP] strip &quot;a href&quot; html code from links"
date: 2008-06-18
forum: Programming Talk
---

### Post by ELD on 2008-06-18
Hi all i am looking for a quick and easy way to strip html hyperlink from web address's in a string.

for example

string:
```

<a href="http://www.google.com">www.google.com</a>

```

Would become
newstring:
```

www.google.com

```

Sounds simple but i don't know how to do it.

---

### Post by Sportingfan on 2008-06-18
You can use php's function [str_replace]("http://be.php.net/manual/en/function.str-replace.php") and [ereg_replace]("http://be.php.net/manual/en/function.ereg-replace.php").
```

$link = str_replace("<a href=\"","",$your_link);
$link = ereg_replace("\">()</a>","",$link);

```

Check [php.net]("http://be.php.net/manual/en/function.str-ireplace.php") for more info and other possibilities.

---

### Post by NormR2 on 2008-06-18
Do those functions  span lines? <A href ... can be on multiple lines.
The example given by the OP is ambiguous. The string shown as the newstring is both the link and the text/comment. The code given by Sportingfan wouldn't return the newstring requested, it would have http:// as a prefix.

---

### Post by Mickeysofine1972 on 2008-06-18
try strip_tags()

I think thats what your looking for

Mike

---

### Post by jdvb on 2008-10-22
Hi,

perhaps you would still be interested in this code?

```
$yourcodewithoutlinks = preg_replace('/<a href=\"(.*?)\">(.*?)<\/a>/', "\\2", $yourcodewithlinks)
```

found this page by searching on google for what you wanted, and do not want to remove all html, could not find what I wanted and wrote it myself.

---

