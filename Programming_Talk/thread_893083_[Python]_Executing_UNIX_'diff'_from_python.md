---
title: "[Python] Executing UNIX 'diff' from python"
date: 2008-08-17
forum: Programming Talk
---

### Post by GammaPoint on 2008-08-17
Hi, I'm trying to execute the UNIX command 'diff' from python and connect to it's output stream so that I can tell if the files differ. But I'm having some issues. I tried something simple like the following:

 ```

os.popen('diff file1 file2')

```diff: standard output: Broken pipe

and then I was going to .readlines() from that resulting object. 

But I got the following error message:
```

diff: standard output: Broken pipe

```

What am I doing wrong? Does anyone know how to do this with the newer subprocess module?

---

### Post by meanburrito920 on 2008-08-17
Can you give some more info on your python version, etc? I just tried it on python 2.5.1 on ubuntu 7.10 and it worked fine. How are you passing the filenames to popen?

---

### Post by ghostdog74 on 2008-08-17
filecmp is the module you would use in Python. Avoid calling external commands where possible. Makes your code portable. Also, look at the Python library reference for more useful modules.

---

### Post by GammaPoint on 2008-08-18
> **meanburrito920 said:**
> Can you give some more info on your python version, etc? I just tried it on python 2.5.1 on ubuntu 7.10 and it worked fine. How are you passing the filenames to popen?

I am using 2.5.2 on Hardy Heron. I tried using os.popen as shown in my first post (the same as if I would have used os.system() but I wanted to connect to the output stream so I decided to use popen instead).

Also, thanks for the suggestion ghostdog, I wasn't aware of this function. Although I am still curious as to why the above didn't work...:confused:

---

