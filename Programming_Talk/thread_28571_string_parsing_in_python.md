---
title: "string parsing in python"
date: 2005-04-20
forum: Programming Talk
---

### Post by paulfox on 2005-04-20
Hi all,
i'm wondering whats the best way for parsing a long string of text.
say i have a sentance like:
"hello my name is paul : )"
I'd want it to be scanned and then every occurance of "hello" is replaced with "howdy", and ": )" is replaced with "(SMILE)"

are there any easy ways of doing this in python?

thanks a lot for reading!

---

### Post by jdonnell on 2005-04-20
[http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)

```

>>> str = "hello my name is paul : )"
>>> str.replace('hello', 'howdy')
'howdy my name is paul : )'
>>>

```

---

