---
title: "[SOLVED] Help an idiot out with his true/false tests"
date: 2008-07-09
forum: Programming Talk
---

### Post by aheckler on 2008-07-09
OK, here's the deal. I run Conky in the upper-right corner of my screen and I want to insert a line in there that pings my website's server and tells me if it's up or down.

I already have:

```
ping 207.210.111.30 -c 1 -w 5 | grep packets | cut -c 24
```

which returns a "1" if the server's up and a zero if not. Now, I'm trying to transform that output into the words "Up" and "Down" respectively, but I can never quite get my ifs working correctly. Can somebody hold my hand here?

Thanks!

---

### Post by ghostdog74 on 2008-07-09
```

ping 207.210.111.30 -c 1 -w 5 | awk 'BEGIN{a["1"]="Up";a["0"]="Down"}/packets/{print a[$1]}'

```
You might not really understand the above, so you should really get the basics first, like assigning results to [variables](http://tldp.org/LDP/abs/html/variables2.html) and [testing](http://tldp.org/LDP/abs/html/comparison-ops.html) them.

---

