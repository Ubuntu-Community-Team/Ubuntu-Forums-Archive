---
title: "Bash: Missing `]'"
date: 2013-06-11
forum: Programming Talk
---

### Post by duke.tim on 2013-06-11
Does anyone see what is wrong with this line of code? I have no idea what is wrong.

```
if [ ${Array[$xSrcIP]} == "$SrcIP" && ${Array[$yDstIP]} == "$DstIP" ] ;then
```

> ./script.sh: line 5: [: missing `]'

The normal issue is missing spaces but i'm not missing spaces.

---

### Post by duke.tim on 2013-06-11
Whoops never mind just saw what was wrong


```
 if [ "${Array[$xSrcIP]}" == "$SrcIP" ] && [ "${Array[$yDstIP]}" == "$DstIP" ] ;then
```

---

