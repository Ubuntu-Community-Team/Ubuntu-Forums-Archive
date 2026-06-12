---
title: "print nth line of a file and filename for all files in a folder"
date: 2012-09-12
forum: Programming Talk
---

### Post by kjfarley on 2012-09-12
I've learned a bit about using head, but I'm trying to output some lines from a config file with the file name.  

Thanks!

---

### Post by steeldriver on 2012-09-12
how about 

```
for file in *; do echo "$file"; sed '*n*!d' "$file"; done
```where *n *is the line number

---

### Post by Lars Noodén on 2012-09-12
Well without more details, it's hard to come up with specifics but [find](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1posix.html) and [awk](http://manpages.ubuntu.com/manpages/precise/en/man1/awk.1posix.html) seem to do what you want.   The example below finds files ending in .conf and prints the file name and then the third line, with a blank line before each file.  

```

find . -name '*.conf' \
       -exec awk 'BEGIN { print "\n{}"} NR ==3 {print}' {} \;

```

Adjust as needed. The dot '.' means the current directory.  It could just as easily point to another directory using the full or relative path.

If you're looking for a specific pattern instead of the nth line, awk can do that, too.

---

### Post by kjfarley on 2012-09-13
Thank you so much! This did exactly what I needed.  steeldriver, I used your line (for file...).  Lars, I will try yours as well when I get time later.  Thanks again!

---

