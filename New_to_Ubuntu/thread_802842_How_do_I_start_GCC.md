---
title: "How do I start GCC?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by sooperspook on 2008-05-21
I'm just starting to learn how to program and need to use gcc for my course.

According to the Package Manager Ubuntu already comes with gcc but I can't find it anywhere.

Is it built into the terminal? Do I have to start it from the terminal? If so, what commands do I use?

Thanks in advance. 

Also apologies if this is a really silly question. :)

---

### Post by garyed on 2008-05-21
gcc is run in terminal :

type :  "man gcc" in the terminal & you should see a good bit of stuff.
You may have to install build-essential.


To just do a simple compile: 
```
 gcc filename.c -o program 
``` 
where "filename.c" is your source code & "program" is the name you want to give to your compiled program. If its C++ code then subtitute g++ instead of 
gcc

---

### Post by amingv on 2008-05-21
Yes, it's in the terminal

First:

```
sudo apt-get install build-essential
```

then

```
gcc -o myprogram sourcefile1.c sourcefile 2.c ... sourcefileN.c
```

If you want a front-end for it (an IDE) then check the FAQ in the Programming Talk subforum,. there's many to choose from.

---

### Post by sooperspook on 2008-05-22
Ah! Thank you , thank you!

I'll never get over just how fast (and friendly) the Ubuntu forums are. 

:)

---

