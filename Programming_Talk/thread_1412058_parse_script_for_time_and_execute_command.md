---
title: "parse script for time and execute command"
date: 2010-02-20
forum: Programming Talk
---

### Post by supulton on 2010-02-20
Say I have a text file containing strings such as

2010 feb 24, wash car, 13:00
2010 jun 25, discover meaning of life, 15:00
2011 jan 1, celebrate new year, 0:00

Would it be possible to parse ONLY the times "13:00, 15:00, 0:00, etc," ignoring the dates and to-dos, and somehow execute a command if one of the times in the file matched the current system time?

---

### Post by Barrucadu on 2010-02-20
Something like this?

```
grep ', `date +%H:%M`$' /path/to/file | \
while read line; do
    some-command "$line";
done
```

---

### Post by kaibob on 2010-02-20
This is another way to do what you want:

```
#!/bin/bash

current="$(date +%H:%M)"

while read line ; do
   time=${line##*, }
   if [ "$time" = "$current" ] ; then
      echo "There was a match at $current"
   fi
done < file
```

---

### Post by supulton on 2010-02-20
> **kaibob said:**
> This is another way to do what you want:

```
#!/bin/bash

current="$(date +%H:%M)"

while read line ; do
   time=${line##*, }
   if [ "$time" = "$current" ] ; then
      echo "There was a match at $current"
   fi
done < file
```

Thanks, perfect. :)

---

