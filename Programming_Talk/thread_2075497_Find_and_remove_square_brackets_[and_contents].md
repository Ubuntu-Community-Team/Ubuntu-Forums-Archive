---
title: "Find and remove square brackets [and contents]"
date: 2012-10-24
forum: Programming Talk
---

### Post by raincityrunner on 2012-10-24
How could BASH be used to find and remove square brackets [as well as all contents] from directory names and recursively to underlying files too?

I've tried a few things with find/rename and sed, but can't seem to get the syntax quite right.

---

### Post by steeldriver on 2012-10-24
Try

```
shopt -s globstar; rename -nv 's/\[(.*?)\]//' **/*
```(if it looks right you can remove the -n no-act option)

---

### Post by raincityrunner on 2012-10-24
Thanks. It does seem to do the trick except that the hyphen that replaces square brackets poses a problem if it's at the start of the filename. I should be able to figure it out from here, however.

---

### Post by steeldriver on 2012-10-25
Hyphen? Hmm... it should replace the entire [between brackets] string with nothing

Can you post an example of where it's going wrong?

---

