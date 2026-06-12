---
title: "IOCTL in Python, how exactly do you do it?"
date: 2006-12-11
forum: Programming Talk
---

### Post by AsGF2MX on 2006-12-11
Is there any clean way to take a header file containing _IOR and IOWR macros and use them in Python? I am still confused as to how to access such stuff in Python. Also I'm not sure I quite get the ioctl syntax within python - seems a little different from C.

---

### Post by duff on 2006-12-11
i seem to recall a script called **h2py** somewhere that did the first part of your question, try google.

---

### Post by AsGF2MX on 2006-12-11
I have managed to get my hands on that but running it results in

./h2py.py 
: No such file or directory

I can't figure out what this means and it's driving me nuts. ](*,)

Also, is this supposed to be run with some sort of arguments or not as the result is the same regardless of whether or not there are any other arguments.

Edit: Managed to get it to run seems like there was some extra character after the first line. Pity it seems to skip those _IOR macros.

---

