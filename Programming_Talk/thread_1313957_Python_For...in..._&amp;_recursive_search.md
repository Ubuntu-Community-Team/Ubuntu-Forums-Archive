---
title: "Python: For...in... &amp; recursive search"
date: 2009-11-04
forum: Programming Talk
---

### Post by jesuisbenjamin on 2009-11-04
Hello forum, ):P

With Python i would like to iterate through files in a directory **and** its sub-directories.
Is there any means to make [FONT="Courier New"]for...in...[/FONT] recursive, or do i need to create a function to find directories and add them to the list of directories to iterate?

Thanks for the tips!

---

### Post by Bjalf on 2009-11-04
Check out os.walk() and os.path.walk()
[http://docs.python.org/library/os.html#os.walk](http://docs.python.org/library/os.html#os.walk)
[http://docs.python.org/library/os.path.html#os.path.walk](http://docs.python.org/library/os.path.html#os.path.walk)

---

### Post by ghostdog74 on 2009-11-04
use os.walk() and not os.path.walk()

---

