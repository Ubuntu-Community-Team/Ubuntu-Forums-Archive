---
title: "Launch programs from script"
date: 2009-11-05
forum: Programming Talk
---

### Post by MathUHenry on 2009-11-05
I want to use a script to launch two files that are related, exempli gratia:

#!/bin/sh
gedit /home/ScilabNotes.txt
scilab

but the script is linear. It opens my note page and waits for me to close my notes before it opens Scilab. I want them both to open at the same time.

I think what I need to do is a fork. The documentation of forks, so far, make no sense to me. Am I on the right track.

---

### Post by bapoumba on 2009-11-06
Moved to PT.

---

### Post by diesch on 2009-11-06
```
#!/bin/sh
gedit /home/ScilabNotes.txt &
scilab
```

---

### Post by MathUHenry on 2009-11-06
Awesome! Thanks Diesch_._

---

