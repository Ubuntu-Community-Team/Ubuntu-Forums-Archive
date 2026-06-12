---
title: "Bash inserting lines and such"
date: 2011-03-29
forum: Programming Talk
---

### Post by bcooperizcool on 2011-03-29
How can I insert new lines after a set point of a file, using text from another file.   This file contains charachters such as <, /, ?, and a few others.


They need to be inserted into a file after this line:
<plist version="1.0">

Thanks!  :D

---

### Post by bcooperizcool on 2011-03-29
Well, I just found a simpler solution, I just echoed the beginning and ending of the files, but I am still interested on how to do this, for learnings sake.

---

### Post by papibe on 2011-03-29
Bash by itself doesn't look like the right tool. I would suggest awk. Check this [tutorial ]("http://www.thegeekstuff.com/2010/01/awk-introduction-tutorial-7-awk-print-examples/")to get started.

Regards.

---

### Post by Vaphell on 2011-03-29
sed is ok too
example data:
```
$ echo $'something\n<plist version="1.0">\nsomething'

something
<plist version="1.0">
something
```

example piped to sed:
```

echo $'something\n<plist version="1.0">\nsomething' | sed -r 's/(<plist version="1.0">)$/\1\nNEW LINE\nANOTHER NEW LINE/g'

something
<plist version="1.0">
NEW LINE
ANOTHER NEW LINE
something
```

sed -ir 's/(<plist version="1.0">)$/\1\nNEWLINE/g' <source file>
should do the same with the source file in place (-i)

---

