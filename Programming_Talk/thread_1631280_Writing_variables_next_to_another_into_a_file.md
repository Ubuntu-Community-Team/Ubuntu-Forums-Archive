---
title: "Writing variables next to another into a file"
date: 2010-11-26
forum: Programming Talk
---

### Post by Peter.Paul on 2010-11-26
Hello Community,

I like to write two variables, separated by a tab into a file. I tried some things with echo and so, but it all did not work out. Can can help me with that?
```

voltage= awk 'BEGIN{total=0;} {total+=$1} END{printf (total/50)}' $1tail.txt 
current= awk 'BEGIN{total=0;} {total+=$2} END{printf (total/50)}' $1tail.txt

```thank in advance

---

### Post by bredsaal on 2010-12-22
Try this:
```
echo -e "$voltage\t$current"
``` :-)

---

