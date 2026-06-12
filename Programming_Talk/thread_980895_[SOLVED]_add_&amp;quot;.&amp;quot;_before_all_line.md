---
title: "[SOLVED] add &amp;quot;.&amp;quot; before all lines in a file using sed?"
date: 2008-11-13
forum: Programming Talk
---

### Post by PryGuy on 2008-11-13
Good day!
I need a hint! I have downloaded a restricted sites list (22918 sites) for my lovely squid, but they do not have the right syntax. I have to addd "." before all lines so they would look like '.site.com' not 'site.com'. Please give me a hint how do I do it in sed. Thank you, and I promise I'll finally manage myself to learn sed soon! :)

---

### Post by geirha on 2008-11-13
Use '^' to match only the beginning of each line, and replace it with '.'. It's hard to only give a hint when it's such a short and easy sed :)

Also read about the -i option to sed in its man-page.

---

### Post by PryGuy on 2008-11-13
got it, it's:```
sed -i 's/^/./' filename
```

---

