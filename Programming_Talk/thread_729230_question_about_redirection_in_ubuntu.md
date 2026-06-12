---
title: "question about redirection in ubuntu"
date: 2008-03-19
forum: Programming Talk
---

### Post by thungmail on 2008-03-19
hi
I tried to use redirection stdin from the file but I got the message
```

tuan@tuan:~/workspace/2031$ ls
Debug  q1  q1.c  q1Testing  sample.c
tuan@tuan:~/workspace/2031$ q1<q1Testing
bash: q1: command not found
tuan@tuan:~/workspace/2031$ 

```
Can anyone tell me the reason and how to fix it
thanks

---

### Post by LaRoza on 2008-03-19
./ql 

If the program isn't in your $PATH specify the path.

---

### Post by thungmail on 2008-03-19
just curious, you said "my program is not in your path".I dont get it here. What do you mean about my path ( I meant what is a path here)

---

### Post by mssever on 2008-03-19
> **thungmail said:**
> just curious, you said "my program is not in your path".I dont get it here. What do you mean about my path ( I meant what is a path here)

Not path, $PATH. $PATH is an environment variable that specifies where the system should look for executable programs.

---

### Post by Mr. C. on 2008-03-19
> **thungmail said:**
> just curious, you said "my program is not in your path".I dont get it here. What do you mean about my path ( I meant what is a path here)

See Lecture 5, starting with slide 30 in the Coursework section at:

[http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)

---

### Post by mssever on 2008-03-19
> **Mr. C. said:**
> See Lecture 5, starting with slide 30 in the Coursework section at:

[http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)
It took me quite some time to find this, because I had to remember the directions, then click the link, only I didn't remember the directions accurately. It would have been better to give the specific link: [http://cis68a.mikecappella.com/files/lecture5.pdf](http://cis68a.mikecappella.com/files/lecture5.pdf).

---

### Post by Mr. C. on 2008-03-19
What I provided was good enough.  One could say that knowing what is good enough is better than "better".

Perhaps you might work on that short term memory issue! ;-)

---

