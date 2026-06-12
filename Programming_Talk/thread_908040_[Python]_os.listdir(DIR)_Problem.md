---
title: "[Python] os.listdir(DIR) Problem"
date: 2008-09-02
forum: Programming Talk
---

### Post by regomodo on 2008-09-02
#

---

### Post by ghostdog74 on 2008-09-02
even though you have listed out the directory information using os.listdir(), however, if you are doing further processing , you should change directory to that directory first, using os.chdir()

---

### Post by regomodo on 2008-09-02
#

---

### Post by WW on 2008-09-02
That's strange--look at the traceback. It says the bad line is
> 
    files = os.listdir(dir_now)

but there is no such line in your code.  Are you sure it was the latest version of your file in which the problem occurred?

---

### Post by regomodo on 2008-09-02
#

---

### Post by WW on 2008-09-02
OK, but now I don't understand how ghostdog74's suggestion fixed your problem.  The error was definitely with os.listdir(...) (and not some subsequent command), and you gave apparently give it a full path name (that's what the traceback shows), so why should os.chdir(...) have any effect?

---

