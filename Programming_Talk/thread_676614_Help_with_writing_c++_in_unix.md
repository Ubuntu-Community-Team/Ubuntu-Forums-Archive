---
title: "Help with writing c++ in unix"
date: 2008-01-23
forum: Programming Talk
---

### Post by angelicpox on 2008-01-23
Alright the title may by somewhat misleading but I didn't really know how else to title it...anyway on to my problem.

I am learning to write c++ and I am doing it in pico in unix command line. I've been compiling it using gcc and after fixing whatever syntax errors that may present themselves I try to run the program that I just wrote and I get a error that basically says bash:command not found. This is all on my personal computer. I haven't had this problem when I ssh into the unix systems at my school.  Any ideas?
thanks in advance. sorry if this is already somewhere else I couldn't find anything relating.

---

### Post by Senesence on 2008-01-24
You have to include the "./", like this:

./yourprogramname

---

### Post by jcwmoore on 2008-01-24
Also you need to know that by default gcc (and g++) produce and file called a.out, so if you just compile your code, to run in to will need to type
```
./a.out
```

---

### Post by girishv on 2008-01-24
Add the current working directory to your path variable. 
PATH=$PATH:.

To make it permanent, add this to your .bashrc as well.

Then you need not prefix the executable with ./

Girish

---

### Post by LaRoza on 2008-01-24
> **girishv said:**
> Add the current working directory to your path variable. 
PATH=$PATH:.


But don't do that. It is a security risk, especially if it is your home directory.

---

