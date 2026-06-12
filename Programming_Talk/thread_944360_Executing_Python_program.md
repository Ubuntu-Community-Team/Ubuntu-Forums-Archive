---
title: "Executing Python program"
date: 2008-10-11
forum: Programming Talk
---

### Post by 7raTEYdCql on 2008-10-11
I read that you must include '#!usr/bin/env python' as the first line in the python program and then after making the file executable by using  chmod a+x abc.py, i will be able to execute the program by double clicking on it.

However this does not seem to happen. on running in terminal './abc.py' i get the error message that usr/bin/env not a file/directory.

I also tried the following shebang: #!usr/bin/python2. On running the script i got the same error.

Any suggestions.

---

### Post by Canis familiaris on 2008-10-11
Do with:

#!/usr/bin/python

It'll work.

---

### Post by Yannick Le Saint kyncani on 2008-10-11
> **i.mehrzad said:**
> I read that you must include '#!usr/bin/env python' as the first line in the python program

It's #! /usr/bin/env python

Regards.

---

### Post by LaRoza on 2008-10-11
> **i.mehrzad said:**
> I read that you must include '#!usr/bin/env python' as the first line in the python program and then after making the file executable by using  chmod a+x abc.py, i will be able to execute the program by double clicking on it.

However this does not seem to happen. on running in terminal './abc.py' i get the error message that usr/bin/env not a file/directory.


Use /usr/bin/env python.

Without the leading /, it is a relative path.

> **Anurag_panda said:**
> Do with:

#!/usr/bin/python

It'll work.

That works too, IF Python is in /usr/bin/, which it is, for default installations.

---

### Post by Canis familiaris on 2008-10-11
> **LaRoza said:**
> Use /usr/bin/env python.

Without the leading /, it is a relative path.



That works too, IF Python is in /usr/bin/, which it is, for default installations.

So is it more advisable to use "**#!/usr/bin/env python**" ?

---

### Post by Steveway on 2008-10-11
> **Anurag_panda said:**
> So is it more advisable to use "**#!/usr/bin/env python**" ?

Yes because you can't be sure that everyone has python in the same location but almost everyone has env at the same position.

---

### Post by LaRoza on 2008-10-11
> **Anurag_panda said:**
> So is it more advisable to use "**#!/usr/bin/env python**" ?

For distribution, yes, but for personal use, it doesn't matter.

---

### Post by nvteighen on 2008-10-11
<a-bit-offtopic>
Have you thought what a great invention the shebang is? Otherwise, we'd hassle with file type associations like in Windows!

Three hurras for the Shebang!
</a-bit-offtopic>

---

### Post by jordilin on 2008-10-11
> **i.mehrzad said:**
> I read that you must include '#!usr/bin/env python' as the first line in the python program and then after making the file executable by using  chmod a+x abc.py, i will be able to execute the program by double clicking on it.

However this does not seem to happen. on running in terminal './abc.py' i get the error message that usr/bin/env not a file/directory.

I also tried the following shebang: #!usr/bin/python2. On running the script i got the same error.

Any suggestions.

I would not recommend chmod a+x as this involves execution permission for everybody. Just do chmod +x or chmod u+x.

---

### Post by Canis familiaris on 2008-10-11
> **nvteighen said:**
> <a-bit-offtopic>
Have you thought what a great invention the shebang is? Otherwise, we'd hassle with file type associations like in Windows!

Three hurras for the Shebang!
</a-bit-offtopic>

+1

Anyways thanks for mentioning it so that I google searched for it and discovered what this great phenomenon meant.

---

### Post by Yannick Le Saint kyncani on 2008-10-11
> **Anurag_panda said:**
> So is it more advisable to use "**#!/usr/bin/env python**" ?

Sometimes, people have python installed in /usr/local/ for example.

---

