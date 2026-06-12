---
title: "awk extract 3 days logs and put to new file"
date: 2017-08-25
forum: Programming Talk
---

### Post by philipe003a on 2017-08-25
I need extract 3 days old logs from one file and put to new file. I trying using awk (maybe is other way?) but unfortunately is not working :/ access3.log is empty and don't know why. :(

```

TZ_START=$(date +%Y-%m-%d -d'now-3 days') 
awk -F,'{if($5 >= '$TZ_START') print}'< access.log > access3.log
```
```
xx: xxxxxx ; xxxx:2017-08-10T15:19:00; xxxxxxxx: xxxxxxxxxxxxxxxxxxxxxxxxxx 
xx: xxxxxx ; xxxx:2017-08-13T15:19:24; xxxxxxxx: xxxxxxxxxxxxxxxxxxxxxxxxxx 
xx: xxxxxx ; xxxx:2017-08-14T15:12:35; xxxxxxxx: xxxxxxxxxxxxxxxxxxxxxxxxxx 
xx: xxxxxx ; xxxx:2017-08-18T15:13:43; xxxxxxxx: xxxxxxxxxxxxxxxxxxxxxxxxxx 
xx: xxxxxx ; xxxx:2017-08-19T15:15:43; xxxxxxxx: xxxxxxxxxxxxxxxxxxxxxxxxxx 
xx: xxxxxx ; xxxx:2017-08-23T15:13:17; xxxxxxxx: xxxxxxxxxxxxxxxxxxxxxxxxxx 
xx: xxxxxx ; xxxx:2017-08-24T15:12:21; xxxxxxxx: xxxxxxxxxxxxxxxxxxxxxxxxxx
```

---

### Post by Habitual on 2017-08-25
maybe /path/to/access.log ?

---

### Post by aromo2 on 2017-08-25
why are you providing comma (,) as the field separator for awk (-F,) ?  You need a proper logic to extract the yyyy-mm-dd from access.log in order to compare it with $TZ_START.
I suggest testing by doing this and see if the output is what you would expect:
cat access.log | awk ... (or whatever command)
for instance:
```
awk -F: '{split($3,date,"T"); print date[1]}'
```
And then work from there.

---

