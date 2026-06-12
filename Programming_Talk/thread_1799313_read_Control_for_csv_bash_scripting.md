---
title: "read Control for csv bash scripting"
date: 2011-07-07
forum: Programming Talk
---

### Post by conradin on 2011-07-07
Hi all, I have a CSV plain text database,
I want to read the file line by line, asigning variables to my script, from each line. 
The file is an IP address, followed by a secod number specifying a range.
130.111.192.2,24
130.111.144.18,64
... And so on.
So how might I get the first number into a variable with the second comma separted variable in another varaible?

---

### Post by slavik on 2011-07-07
quickest solution I came up with:

```
echo "a,b,c" | sed 's/,/ /g' | while read d e f; do echo "$d $e $f"; done
```

---

### Post by sisco311 on 2011-07-07
See: [http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001)

```
#!/bin/bash

while IFS=, read -r ip range
do
  echo "$ip"
  echo "$range"
done < file

```

---

### Post by slavik on 2011-07-07
I always forget about IFS :(

---

### Post by pafoo on 2011-07-07
LOL, well I do quite alot of shell scripting and thats the first I heard of it. Thats the reason why I read these forums, helps me learn and help me stay sharp.

My question is, what man page gives information on that?

Is it man bash?

---

### Post by sisco311 on 2011-07-07
> **pafoo said:**
> 
Is it man bash?

Yep that's it. 

In addition, check out [Greg's Wiki]("http://mywiki.wooledge.org/"):  [http://mywiki.wooledge.org/IFS](http://mywiki.wooledge.org/IFS)

---

### Post by pafoo on 2011-07-07
Thanks

---

