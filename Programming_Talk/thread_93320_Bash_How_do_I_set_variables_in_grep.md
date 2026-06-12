---
title: "Bash: How do I set variables in grep?"
date: 2005-11-21
forum: Programming Talk
---

### Post by bashhelp on 2005-11-21
```

            for xrm in `ls`; do
            if echo $xrm | grep -q *.html; then
            rm $xrm
            fi; done

```

The asterisk (*) are not functioning as variables.  How do I make grep understand variables?

---

### Post by dabear on 2005-11-21
try using egrep instead

---

### Post by toojays on 2005-11-22
The code you have doesn't make sense in the context of either grep or egrep. What exactly are you trying to do?

---

### Post by dabear on 2005-11-22
I would assume he's trying to delete all files in a directory which contains &#171;.html&#187;

---

