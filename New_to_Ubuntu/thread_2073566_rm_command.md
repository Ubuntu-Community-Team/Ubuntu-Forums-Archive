---
title: "rm command"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by unibroker on 2012-10-19
Trying to bulk remove all files in HP Pocket Media Drive that begin with "duplicity".

```
jim@jim-computer:/media/HP Pocket Media Drive$ find -name . 'duplicity*' -exec rm -f {} \;
```

And it returned 
```
find: paths must precede expression: duplicity*
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
```

Not sure where I went wrong.

---

### Post by mikewhatever on 2012-10-19
Try putting the '.' before '-name', as '.' tells find where to look. I'd also refrain from using rm -f, it's completely unnecessary.

---

### Post by unibroker on 2012-10-19
> **mikewhatever said:**
> Try putting the '.' before '-name', as '.' tells find where to look. I'd also refrain from using rm -f, it's completely unnecessary.

Worked.  Thank you.

---

