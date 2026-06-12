---
title: "Bash script question (remove lines of a file)"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by DBrocks on 2008-05-10
Hey guys.

I am writing a script, but I need to know, how can I delete the first 10 lines of a file, and the last 5 lines of that file? I'm sure it has a simple solution that I'm missing. :lolflag:

Thanks!

~Dan

---

### Post by CAsurfer on 2008-05-10
Which language are you using?

---

### Post by DBrocks on 2008-05-10
In the title: Bash :lolflag:

---

### Post by sdennie on 2008-05-10
I think:

```

cat input | head -n-5 | tail -n+10 > output

```

Edit:

Opps.  Remove 10 from the top instead of 5

---

