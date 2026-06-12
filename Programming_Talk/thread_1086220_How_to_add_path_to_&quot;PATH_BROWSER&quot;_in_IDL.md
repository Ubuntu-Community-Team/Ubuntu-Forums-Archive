---
title: "How to add path to &quot;PATH BROWSER&quot; in IDLE"
date: 2009-03-03
forum: Programming Talk
---

### Post by mal_conductor on 2009-03-03
The Python book I am learning from asks to import programs as modules with the command "import"

The programs being imported are part of the companion CD.

How do I edit the Path Browser to include the directory where I saved the companion CD.

(I do not want to save the CD in any of the paths currently in sys.path.  I want to add a path to sys.path)


Thank you

=========================

---

### Post by days_of_ruin on 2009-03-03
```
import sys
sys.path.append('/media/cdrom/something')
```

Something like that should work.

---

### Post by mal_conductor on 2009-03-03
Thank you.  Worked great.

---

