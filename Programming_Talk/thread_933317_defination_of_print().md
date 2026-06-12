---
title: "defination of print() ???"
date: 2008-09-29
forum: Programming Talk
---

### Post by kcode on 2008-09-29
declaration of printf() can be found in stdio.h,
where can i find the defination??
the real code..

---

### Post by Npl on 2008-09-29
> **kcode said:**
> declaration of printf() can be found in stdio.h,
where can i find the defination??
the real code..in the sourcecode, typically you only have the headers installed. So [get the source]("http://www.gnu.org/software/libc/")

---

### Post by nvteighen on 2008-09-29
If you have "Sources" repositories activated, you could just do:

```

mkdir libc-src
apt-get source libc6

```

(NO root privileges needed)

---

### Post by snova on 2008-09-29
It's buried deep in glibc's IO sublibrary. The printf() function is actually a stub (with its own file, for whatever reason) that calls another, more generic function. If I recall correctly, *that* function then calls another, and possibly another, before getting to the actual formatting code.

Out of curiousity, why do you want it? If you just want to see how it works, there are other, more readable implementations available.

---

### Post by nvteighen on 2008-09-30
> **snova said:**
> It's buried deep in glibc's IO sublibrary. The printf() function is actually a stub (with its own file, for whatever reason) that calls another, more generic function. If I recall correctly, *that* function then calls another, and possibly another, before getting to the actual formatting code.

Out of curiousity, why do you want it? If you just want to see how it works, there are other, more readable implementations available.
Yes, I don't know exactly what "calls path" glibc performs but printf() is just a wrapper for a fprintf() or maybe a vfprintf() using stdout as output stream...

---

### Post by kcode on 2008-09-30
> **snova said:**
> 
Out of curiousity, why do you want it? If you just want to see how it works, there are other, more readable implementations available.

just 'out of curiosity'.
thanks for telling me that.

---

### Post by snova on 2008-09-30
> **nvteighen said:**
> Yes, I don't know exactly what "calls path" glibc performs but printf() is just a wrapper for a fprintf() or maybe a vfprintf() using stdout as output stream...

I think it goes down to vfprintf(), which calls vsnprintf(). glibc isn't exactly the epitome of readable code.

---

### Post by kcode on 2008-09-30
> **nvteighen said:**
> Yes, I don't know exactly what "calls path" glibc performs but printf() is just a wrapper for a fprintf() or maybe a vfprintf() using stdout as output stream...

what does wrapper mean??

---

### Post by bruce89 on 2008-09-30
> **kcode said:**
> what does wrapper mean??

It internally just calls another function. (in this case)

---

### Post by Lux Perpetua on 2008-09-30
To elaborate a bit: often, you need to implement a certain functionality, and you already have a function that does it, but it has the wrong interface. In this case you write a *wrapper* function that has the interface you want and whose implementation is simply (or little more than) a call to the existing function that implements your functionality.

---

