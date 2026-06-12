---
title: "use regex from one variable to another"
date: 2016-09-29
forum: Programming Talk
---

### Post by cazz on 2016-09-29
I guess this is very easy but I have search and have not find any good that I can use.

I have a variable $upload and I want to run a regex and save the info to another variable $newupload

I can easy print it out but have problem to make it into a variable


```
echo "$upload" | grep -oP "GBytes\s+\K\d+"
```

It print out the info I want to have into another variable ($newupload)

---

### Post by cazz on 2016-09-29
I did find it :)

```
newupload=$(echo "$upload" | grep -oP "GBytes\s+\K\d+")
```

---

