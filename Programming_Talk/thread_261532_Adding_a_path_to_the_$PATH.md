---
title: "Adding a path to the $PATH"
date: 2006-09-20
forum: Programming Talk
---

### Post by thomasaaron on 2006-09-20
Hello,

How do I put an additional path into the $PATH variable?

Thanks,
Tom

---

### Post by ghostdog74 on 2006-09-20
PATH=/yournewpath:$PATH
export PATH

---

### Post by thomasaaron on 2006-09-20
Thank you.

---

### Post by thomasaaron on 2006-09-20
OK, I did that.

It works until I exit the terminal and come back into it again. Then, when I check $PATH, my new path is gone.

Is there a way to make the change permanent?

---

### Post by skymt on 2006-09-20
Run "gedit ~/.bashrc" and put the code in there.
By the way, you can do it in one line: "export PATH=$PATH:/foobar/bin".

---

