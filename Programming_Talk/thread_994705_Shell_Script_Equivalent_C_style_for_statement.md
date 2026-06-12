---
title: "Shell Script Equivalent C style for statement?"
date: 2008-11-27
forum: Programming Talk
---

### Post by kevdog on 2008-11-27
Is there an equivalent shell script syntax that would mimik C's for statement syntax (for i=0; i<5; i++){....};

The best I can come up with would be something like this:
c=0
while [ c -lt 5 ]; do
c=`expr $c + 1`;
done

Seems like a clumsy way of doing the same thing to me??

---

### Post by ghostdog74 on 2008-11-27
check out the bash guide in my sig under chapter 10, section 1. you can find example of for loop with C like syntax. Best of all, read the whole document.

---

### Post by kevdog on 2008-11-27
Wow -- that is good stuff, and I really learned a lot.

---

