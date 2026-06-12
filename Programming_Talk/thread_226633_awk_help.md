---
title: "awk help"
date: 2006-07-31
forum: Programming Talk
---

### Post by kook44 on 2006-07-31
Hi
I have a file of text that was cut from html with many, many lines of:
<option value="xxxx">yyyyyyy</option>
and I need to extract the text between the quotes and between the tags and output them in some arbitrary format, say: xxxx;yyyyyy
I'm trying to use awk, but I'm having some difficulty.  I can get the line to match on the regex, but in awk, once you match a line, you then have "fields" - separated by some delimeter - available to you as variables.  What I need is to have the "matched" part of the line available to me.  Also - I need to do it twice on the same line.
Does anybody know how to do this?  Is awk the right tool for this?
Thanks

---

### Post by kook44 on 2006-07-31
I was able to figure it out:

```
gawk -F "[\"><]" '/</ {print $3";"$5}'
```

took care of it...

---

### Post by m83 on 2006-07-31
Very nice. Thanks for posting the solution also.

---

