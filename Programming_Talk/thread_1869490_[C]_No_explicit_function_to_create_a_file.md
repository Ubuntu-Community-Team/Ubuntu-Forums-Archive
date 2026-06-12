---
title: "[C] No explicit function to create a file?"
date: 2011-10-25
forum: Programming Talk
---

### Post by t1497f35 on 2011-10-25
Hi,
I was wondering, there's a function to open a file "int open(...)", one to close it "int close()", to rename and to delete.
**Is there a corresponding "int create" function to create a file?**
Looks like not, "int mkdir" only creates dirs not files.
At this level of I/O is one supposed to use "int open (.., O_CREAT)" (and then have to close it) to create a file?

---

### Post by Simian Man on 2011-10-25
> **t1497f35 said:**
> [SIZE=3][SIZE=2]Hi,
I was wondering, there's a function to open a file "int open(...)", one to close it "int close()", to rename and to delete.
**Is there a corresponding "int create" function to create a file?**
Looks like not, "int mkdir" only creates dirs not files.
At this level of I/O is one supposed to use "int open (.., O_CREAT)" (and then have to close it) to create a file?[/SIZE]
[/SIZE]

If you want to create a file, presumably you want to put data in it 99% of the time.  Thus you would need to use open anyway, so why have a function just to create a file?

---

### Post by Bachstelze on 2011-10-25
The answer to the question is bold is no, and the answer to the other one is yes.

---

### Post by t1497f35 on 2011-10-25
Thanks anyone, I was wondering whether creating a file by calling "int open(.., O_CREAT)" is the proper solution, now I know it is.

---

### Post by Arndt on 2011-10-26
> **t1497f35 said:**
> Thanks anyone, I was wondering whether creating a file by calling "int open(.., O_CREAT)" is the proper solution, now I know it is.

There is a system call 'creat', described on the same manual page as 'open'.

---

### Post by Bachstelze on 2011-10-26
> **Arndt said:**
> There is a system call 'creat', described on the same manual page as 'open'.

It is equivalent to open(), though, and you still have to close() the fd.

---

### Post by t1497f35 on 2011-10-26
> **Arndt said:**
> There is a system call 'creat', described on the same manual page as 'open'.
But it's marked as deprecated.

---

### Post by Arndt on 2011-10-26
> **t1497f35 said:**
> But it's marked as deprecated.

Could be, but where does it say so?

---

### Post by t1497f35 on 2011-10-26
The glibc docs say so, see screenshot.

---

### Post by Arndt on 2011-10-26
> **t1497f35 said:**
> The glibc docs say so, see screenshot.

Interesting. I wonder where they got that idea. glibc doesn't define the system calls.

Of course, since you can do the same thing with 'open', you don't need 'creat'.

To answer the original question, I would use 'fopen' followed by 'fclose', and not 'open'.

---

### Post by t1497f35 on 2011-10-26
> **Arndt said:**
> Interesting. I wonder where they got that idea. glibc doesn't define the system calls.
Glibc doesn't define system calls, but the GPL states that it doesn't guarantee, nor is it responsible for anything, which makes sense since even Microsoft isn't responsible for (almost) anything despite having to pay for their products.
I also saw custom functions defined in glibc because they care more about usability rather than strict conformance. I heard in window$ there is a big pile of functions which mostly duplicate the libc functionality (I think one of the reasons is to make porting from window$ to other systems more difficult), so it's not like anyone's trying to be the most pedantic system in the world.

---

### Post by Bachstelze on 2011-10-26
creat() is not going to disappear from glibc any time soon, there is too much old software that depends on it (which is the only reason why it is still in POSIX, as well).

---

