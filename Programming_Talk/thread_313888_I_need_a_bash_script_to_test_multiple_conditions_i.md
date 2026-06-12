---
title: "I need a bash script to test multiple conditions in a while loop"
date: 2006-12-06
forum: Programming Talk
---

### Post by Brazen on 2006-12-06
Ok, I have three conditions that I need to test for.  Here is a snippet of what I have:

> while [ -n $FILE_1 -o -n $FILE_2 -o -n $FILE_3 ]; do            
    echo "do some stuff here..."
    ...
done

But this is giving me a "too many arguments error."  If you can't tell, I'm using '-n' to test if a file has a non-zero length and using '-o' to test the three files.  This isn't working for me and I'm wondering how I can test these three conditions in a while loop.

---

### Post by po0f on 2006-12-06
Brazen,

Use && to test for multiple conditions.
```
[FONT="Courier New"]while [ -s $FILE && -s $FILE2 && -s $FILE3]; do
  echo "blar"
done[/FONT]
```

According to [ABS](http://tldp.org/LDP/abs/html/), [-s](http://tldp.org/LDP/abs/html/fto.html) tests for zero size, [-n](http://tldp.org/LDP/abs/html/comparison-ops.html) tests to see if a string is null.

[EDIT]

Depending on what you're trying to accomplish, it might be better to test these files individually instead of all at once.

---

### Post by duff on 2006-12-06
> **Brazen said:**
> Ok, I have three conditions that I need to test for.  Here is a snippet of what I have:



But this is giving me a "too many arguments error."  If you can't tell, I'm using '-n' to test if a file has a non-zero length and using '-o' to test the three files.  This isn't working for me and I'm wondering how I can test these three conditions in a while loop.

Do any of these filenames have spaces in the path?  If so, add double-quotes.

---

