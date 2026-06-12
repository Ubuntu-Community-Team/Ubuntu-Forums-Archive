---
title: "[SOLVED] #!/bin/bash recursively remove *.BK\!"
date: 2008-05-30
forum: Programming Talk
---

### Post by toobuntu on 2008-05-30
I need a way to recursively remove all WordPerfect auto-backups from our file server every night.  There has to be a better way than the following, but I was not having success with recursive options so I kludged this together.  Can someone help make this more elegant?

```
for x in $( ls -R /tmp/play/ | grep \: | cut -d \: -f 1 ) ; do ( y=$( ls $x/*.BK\! 2> /dev/null | grep -v \/\/ ; ls $x*.BK\! 2> /dev/null | grep -v \/\/ ) ; rm $y 2> /dev/null ) ; done
```

---

### Post by WW on 2008-05-30
The **find** command can do that:
```

find /tmp/play -type f -name '*.BK!' -delete

```

---

### Post by odyniec on 2008-05-30
You can do it much easier with find:
```
find /dir -name '*.BK!' -exec rm {} ';'
```

---

