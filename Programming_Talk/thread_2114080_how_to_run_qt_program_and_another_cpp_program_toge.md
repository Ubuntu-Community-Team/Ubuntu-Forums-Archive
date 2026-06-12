---
title: "how to run qt program and another cpp program together"
date: 2013-02-09
forum: Programming Talk
---

### Post by sanda199 on 2013-02-09
Hi everyone, I wrote qt program at gedit and run it on ubuntu terminal. It worked fine. Now I wanna run that Qt program and another simple cpp program together. How can I do it? Is it possible to do that? Thanks millions. :)

---

### Post by Tony Flury on 2013-02-09
> **sanda199 said:**
> Hi everyone, I wrote qt program at gedit and run it on ubuntu terminal. It worked fine. Now I wanna run that Qt program and another simple cpp program together. How can I do it? Is it possible to do that? Thanks millions. :)

As I said in your other thread you can use system() to call one program from another. 

But since I know you have written both programs and both are written in C you can just call one from the other and compile and link then together.

---

### Post by sanda199 on 2013-02-09
> **Tony Flury said:**
> As I said in your other thread you can use system() to call one program from another. 

But since I know you have written both programs and both are written in C you can just call one from the other and compile and link then together.

How to call one from the other? Actually, as I mentioned at the other thread, I wanna run server program and Qt program at the same time. Compiler is G++. Is it possible to do it?
Thanks :(

---

