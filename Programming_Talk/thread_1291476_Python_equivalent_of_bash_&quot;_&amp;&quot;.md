---
title: "Python equivalent of bash &quot; &amp;&quot;"
date: 2009-10-14
forum: Programming Talk
---

### Post by giuspen on 2009-10-14
Hi,
I'm working on a module where I would need in a certain moment to run another process that has to be not waited from the main process.
Til now I solved the problem splitting the module in two executable modules:

module1 (main process) + module2 (new process)
and from module1 I call module2 through shell, exploiting the " &"
[PHP]subprocess.call("module2 &", shell=True)[/PHP]
This works fine, but I would like to be able to do not need to split into 2 modules.

I tried using the module threading but the behaviour is not the same as subprocess.call(...), the main process seems not able to conclude before the second module concludes too (even though I didn't bond them with the .join() function) and so they both proceed slowly.
Is there another way to have the same result of the " &"?
Thanks in advance.

---

### Post by Can+~ on 2009-10-14
[fork]("http://docs.python.org/library/os.html#os.fork")

---

### Post by giuspen on 2009-10-15
> **Can+~ said:**
> [fork]("http://docs.python.org/library/os.html#os.fork")

thanks a lot.

---

