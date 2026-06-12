---
title: "Problem with gcc"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Google Spider on 2008-07-02
I have build-essential and whenever I try to run gcc it says:

```
me@my-desktop~ $ gcc
Unable to exec gcc.real: No such file or directory

```

What should I do now?

---

### Post by bumanie on 2008-07-02
I think you have to run the compiler by nominating a file ie 
> gcc <filename.c>
> gcc <filename.c> -o <myfilename> Can be different from source filename or the same
> ./<myfilename>That should work if you are trying to compile your own text editor "C" syntax.

---

### Post by Google Spider on 2008-07-02
```
~$gcc hello.c -o hello
Unable to exec gcc.real: No such file or directory

```

I think its supposed to say "gcc:No input files" if I just run "gcc".

---

### Post by Google Spider on 2008-07-02
I think I have found the reason but don't know how to fix it. The gcc.real link is broken;see the screenshot.

---

### Post by bumanie on 2008-07-02
Find gcc in synaptic and choose for it to be reinstalled.  That is the easiset thing to try first or > sudo apt-get instll build-essential in termainal and see if downloads properly.

---

### Post by Google Spider on 2008-07-02
yep. Did that already. I removed and installed build-essential again, but it still says gcc.real was not found. I think it has something to do with the broken link. Perhaps if I can get the actual location where gcc.real points then I will replace that link with another onw which ain't broken?

---

### Post by bumanie on 2008-07-02
Try > sudo dpkg --configure -a if it is a broken package that may work. But as it says broken link, it may not. I'm not sure how to track down a broken link.

---

### Post by Google Spider on 2008-07-02
If you go to /usr and search for gcc maybe gcc.real will come up and you can tell me where exactly it points to?

---

