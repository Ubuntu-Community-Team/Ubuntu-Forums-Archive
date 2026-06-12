---
title: "Deleting lines with a string based on upper and lower cased words"
date: 2015-08-01
forum: Programming Talk
---

### Post by Justin C on 2015-08-01
I have a script that downloads tweets so I can respond to them offline.

A lot of the tweets are junk spam.

**Examples**
```
The basics in consideration of creating la marketing shoestring: phzMplDkD
Discovering duck cognation marketing research basics: VoEKPVh
Discovering client patrocliny marketing research basics: mWXwaxa
```

One's like that are the biggest problem, they take up like 20%. They all have this random length of jumbled up characters.

It's some kind of bot doing it and I want to delete 'em.

To solve the problem I think, deleting any line containing these character patterns in a "word":
XyZ (uppercase, lowercase, uppercase)
xYZ (lowercase, uppercase, uppercase)

Is it possible to find a line using these kind of character patterns?

Thanks!

---

### Post by steeldriver on 2015-08-01
You should be able to use POSIX character classes [:upper:] and [:lower:] in most regex tools - e.g. to delete matching lines using sed

```

sed -e '/[[:upper:]][[:lower:]][[:upper:]]/d' -e '/[[:lower:]][[:upper:]][[:upper:]]/d' *somefile*

```

---

### Post by mystics on 2015-08-01
You can find a pattern like that using a regular expression (a.k.a.  regex). If you need a quick run down on how to use them, then this site  should work very well:

[http://regexone.com/](http://regexone.com/)

It offers an  interactive tutorial. There are also online testers to help you test a  regex before applying it. You also should be able to find information on  how each language implements them, provided the language supports them.

---

