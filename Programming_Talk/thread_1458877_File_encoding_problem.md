---
title: "File encoding problem"
date: 2010-04-20
forum: Programming Talk
---

### Post by nebi on 2010-04-20
I have problem with alot of .php files that are encoded with macroman and I need too convert them to UTF-8 because character problem. I tried to use iconv but it seems that iconv doesnt support macroman , any ideas ? It will take to long to change all the files manualy so that isnt a option.

---

### Post by geirha on 2010-04-20
According to [http://en.wikipedia.org/wiki/Mac_OS_Roman](http://en.wikipedia.org/wiki/Mac_OS_Roman)
> The Internet Assigned Numbers Authority identifies this encoding using the string "macintosh."

so try
```
iconv -f macintosh <inputfile >outputfile
```

---

