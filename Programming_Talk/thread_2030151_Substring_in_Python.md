---
title: "Substring in Python"
date: 2012-07-20
forum: Programming Talk
---

### Post by quickvfr on 2012-07-20
I am trying to parse off the last substring between the last two /'s.

This is an example of what I am trying to do:

xml extract of raw text:

['http://www.somewebsite.com/tag/someimage/somestore/a/0/0/0/0/0/1/0/0/1/1/1/1/2/2/0/0/1/0/0/1/32913/44023/]("http://www.somewebsite.com/tag/someimage/somestore/a/0/0/0/0/0/1/0/0/1/1/1/1/2/2/0/0/1/0/0/1/32913/44023/")'

I need to be able to put 32913 into one variable and 44023 into another to map correctly to my local system.  Since these two numbers can be of any length, I cannot utilize the static number of character lengths as I understand substrings work in Python.

Thanks for any help in advance.

Pat Quick
Jacksonville, FL

---

### Post by Bachstelze on 2012-07-20
```
>>> s = 'http://www.somewebsite.com/tag/someimage/somestore/a/0/0/0/0/0/1/0/0/1/1/1/1/2/2/0/0/1/0/0/1/32913/44023/'
>>> s.split('/')[-3:-1]
['32913', '44023']
```

---

### Post by quickvfr on 2012-07-23
Very elegant.  Thank you!

---

### Post by markbl on 2012-07-23
```

s.rsplit('/',3)[1:3]

```
slightly more efficient?

---

