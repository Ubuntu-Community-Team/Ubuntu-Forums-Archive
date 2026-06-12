---
title: "easy JAVA question"
date: 2006-01-24
forum: Programming Talk
---

### Post by Griff on 2006-01-24
So I just started an intro to computer systems class and we're going to be doing some java programming.  Anyway, I just need to write up a simple 'hello world'ish program.  I did, but upon inspection of requirement they want

<name>
<date>

but with only using a single print statement.
I.E. I can't just do:  System.out.println("<name>");
                            System.out.println("<date>");
Can't seem to find the syntax anywhere for it.  Help? :rolleyes:

---

### Post by otake-tux on 2006-01-25
edit-sorry I misunderstood the question.

---

### Post by omair.majid on 2006-01-25
The '\n' character will insert a 'new line'.

so the code is:

system.out.println("<name> \n <date>");

---

