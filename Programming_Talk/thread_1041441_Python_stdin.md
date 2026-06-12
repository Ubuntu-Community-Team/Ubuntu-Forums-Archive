---
title: "Python std::in???"
date: 2009-01-16
forum: Programming Talk
---

### Post by djbushido on 2009-01-16
How would one go about getting input from std::in on python?
My idea is to get something like the C++ equivalent of cin.get(), such that it grabs only 1 character. This is probably a stupid question, but I can't find it documented anywhere.
Thanks!

---

### Post by days_of_ruin on 2009-01-16
```
string = raw_input("enter a character:")
print string
```

---

### Post by Wybiral on 2009-01-16
```

import sys
print sys.stdin.read(1)

```

---

### Post by djbushido on 2009-01-16
thanks for the sys.stdin, that should work! will let you know if it doesn't.

---

### Post by eightmillion on 2009-01-16
```
$ echo "The quick brown fox jumped over the lazy dog." | python -c 'import sys;print sys.stdin.read()'
The quick brown fox jumped over the lazy dog.
```

---

