---
title: "Text Manipulation"
date: 2009-04-20
forum: Programming Talk
---

### Post by Catsworth on 2009-04-20
Hey Guys :)

I've got some HTML source that contains elements for a drop-down selection box on a page.

Each selectable option is delimited in the following fashion:

```
<option>This is Option 1</option>
```

At present all of the options are in one long line in the source, I would like to split each option out into a separate line in a new text file called by_line.txt.

Anybody got any ideas where I could start with this?

Thanks :)

---

### Post by Catsworth on 2009-04-20
Forgot to say, happy to do this either in shell or Python, whichever is easiest/best :)

---

### Post by ghostdog74 on 2009-04-20
```

# more file
<option>This is Option 1</option><option>This is Option 2</option><option>This is Option 3</option><option>This is Option 4</option>

# awk 'BEGIN{RS="</option>"}{print $0 RT}' file
<option>This is Option 1</option>
<option>This is Option 2</option>
<option>This is Option 3</option>
<option>This is Option 4</option>


```

---

### Post by Catsworth on 2009-04-20
Awesome thanks :)

---

