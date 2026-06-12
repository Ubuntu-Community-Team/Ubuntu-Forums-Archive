---
title: "Uniq to remove echoed lines"
date: 2011-07-30
forum: Programming Talk
---

### Post by bcooperizcool on 2011-07-30
I have noticed that even when using the correct synatx, uniq does not remove the lines I have echoed into a file.

say, I echo in the following:
```
echo "Line1" >> file
      echo "Line2" >> file
      echo "Line1" >> file
```

so the file contains those lines.

Then, I run it through uniq:
```
cat file | uniq >> file_no_duplicates
```

but the contents of file_no_duplicates is still the same.  I have tried it multiple different ways, but can't figure it out.  Any ideas why?

Thanks!  :)

---

### Post by MadCow108 on 2011-07-30
uniq only works with sorted files.
> Filter **adjacent** matching lines from INPUT
so do:
```
sort file| uniq
```

or shorter for simple cases:
```
sort -u file
```

---

### Post by Bachstelze on 2011-07-30
[http://pubs.opengroup.org/onlinepubs/9699919799/utilities/uniq.html](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/uniq.html)

> The uniq utility shall read an input file **comparing adjacent lines**, and write one copy of each input line on the output.

[http://ifaq.wap.org/computers/abcsofunix.html](http://ifaq.wap.org/computers/abcsofunix.html)

> 
**U is for uniq, which is used after sort**, and
V is for vi, which is hard to abort.

---

### Post by bcooperizcool on 2011-07-30
Ohhhhhh.....    that would be why.   Thank you!

---

