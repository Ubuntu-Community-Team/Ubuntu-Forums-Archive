---
title: "Is it possible to automatically give answers to an interactive program in bash?"
date: 2007-07-14
forum: Programming Talk
---

### Post by gramarga on 2007-07-14
Hello, everyone.

I am using an interactive program that mostly asks questions expecting yes/no answers. I need to run this program 1000 times and would like to do that with bash.

Is there any way to automatically give these yes/no answers to the program, since they will always be the same?

Thanks in advance,
Gabriel.

---

### Post by Ramses de Norre on 2007-07-14
How are they asked, what kind of interface? Can you modify the source of the program asking the questions?
You'll need to give more details...

---

### Post by kknd on 2007-07-14
You can do, redirecting the input / output to the program.
In Java, you can do that with the "Process" class.

---

### Post by slavik on 2007-07-14
program < inputfile_with_predetermined_answers

---

### Post by gramarga on 2007-07-14
Thank you all for the replies.

slavik, your hint was enough to do the job.
Thanks a lot!

Gabriel.

---

### Post by cwaldbieser on 2007-07-15
> **gramarga said:**
> Thank you all for the replies.

slavik, your hint was enough to do the job.
Thanks a lot!

Gabriel.

If you just want to give the same answer to all the questions, the "yes" command might also work:
```

$ yes | your-prog

```

---

### Post by slavik on 2007-07-16
> **cwaldbieser said:**
> If you just want to give the same answer to all the questions, the "yes" command might also work:
```

$ yes | your-prog

```
I did not know that existed :D

---

### Post by Keith Hedger on 2007-07-16
Try using a HERE script,
For full details see the Advanced Bash Scripting guide, its in the repos under abs somthing!

---

