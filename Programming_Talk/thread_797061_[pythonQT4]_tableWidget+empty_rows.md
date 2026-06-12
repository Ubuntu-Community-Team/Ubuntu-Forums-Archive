---
title: "[python/QT4] tableWidget+empty rows"
date: 2008-05-16
forum: Programming Talk
---

### Post by tsic on 2008-05-16
Good Morning,
I have a tableWidged in witch we  can add rows. When I put empty rows and I try to save these data in a list, the program blocks.
So how can we remove the empty rows from the tableWidget or even don't let the user save else all items are != ""
And how can we check that all cells != ""
Thank you for help.

---

### Post by Verminox on 2008-05-17
I suppose you check whether the data to be entered is an empty string or not *before* you add it to the TableWidget, and then either ignore it or report an error, whatever you wish to do.

By the way, why did you create **3 threads** for the same issue?

---

### Post by tsic on 2008-05-17
Hello,
The insertion to the tableWidget is done directly in the Window form. So what function or SIGNAL should I use? cellModified ?
Thank you

---

