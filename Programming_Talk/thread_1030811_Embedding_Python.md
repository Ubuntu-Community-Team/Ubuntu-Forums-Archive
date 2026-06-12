---
title: "Embedding Python?"
date: 2009-01-04
forum: Programming Talk
---

### Post by Zeotronic on 2009-01-04
I've been trying to follow the [Embedding Python in Another Application]("http://docs.python.org/extending/embedding.html") tutorial... but even seemingly following it word for word, I cant seem to get it to work. I believe it's for a newer version of Python, than is what I got from the repos (2.6.1 vs 2.5... seemingly). Perhaps someone can tell me what I'm doing wrong? I successfully compile the c app, and then type into terminal:
> ./main multiply multiply 3 2
and I get:
> ImportError: No module named multiply
Failed to load "multiply"
It *is* supposed to load multiply.py from the containing folder and run it's function 'multiply' is it not?

Any assistance would be greatly appreciated.

(included are the multiply.py file the tutorial instructed me to create, and main.c... which the tutorial *also* instructed me to create. Should I have sent the binary file as well?)

---

### Post by Zeotronic on 2009-01-05
*ONLY BUMP* Surely someone can help me?

---

