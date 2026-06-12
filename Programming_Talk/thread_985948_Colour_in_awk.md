---
title: "Colour in awk"
date: 2008-11-18
forum: Programming Talk
---

### Post by Mbengi Bongi on 2008-11-18
Can someone advise me on how to make the output of an awk statement a different colour?

My statement is:

```
awk -v KEY=/$input/ 'BEGIN { FS = "," } KEY { print "Name: " $2 }' data1.csv
```

The statement retrieves data from a csv file, what I want is the value [COLOR="Indigo"]$2[/COLOR] a different colour from **Name:**

Any help would be appreciated :)

---

### Post by geirha on 2008-11-18
No hits on "colo(u)r" in the man-page, so I guess the only way is with ansi escapes.
```
{ print "Name: \033[1;31m" $2 "\033[0m" }
```

[http://en.wikipedia.org/wiki/ANSI_escape_code](http://en.wikipedia.org/wiki/ANSI_escape_code)

---

### Post by Mbengi Bongi on 2008-11-18
That's perfect Geirha, that works a treat!

I did try ANSI escape codesd before but I got the quotes in the wrong place! :oops:

Thank you very much ):P

---

### Post by masuch on 2011-09-12
thanks , that's exactly what i needed

---

