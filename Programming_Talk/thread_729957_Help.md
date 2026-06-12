---
title: "Help???"
date: 2008-03-20
forum: Programming Talk
---

### Post by pleasure on 2008-03-20
Hi , I have no ideas how to start writing the code in C that creates my own thread and use it to do whole bunch of matrix multiplication The thread can be very simplistic and must take the cpu away in a slice time that involve SIGALARM()

Thread switching must be done in 1 situation only: when a SIGALARM is caugt by handler.The handler does not perform a longjmp() but sets a variable to a predetermined value. This variable is checked before entering a loop and the thread execuates a function yield() to give up the CPU.

Please help me .Thank you

---

### Post by WW on 2008-03-20
I can't help you with your question, but I can suggest that in the future, you give a more descriptive topic when you start a thread in the forum. "Help???" is not very helpful. :)  Maybe something like "I need help with threads and SIGALARM() in C."

---

### Post by Zugzwang on 2008-03-20
Just out of curiosity: Why do you want to do so? Your description isn't easily comprehensible, so clarification would be wise. Also, it touches a lot of different fields (signals, threads, longjumps, ...), so only people that are familiar with all of them can answer. If you state what you want to do, you might get more answers (using different techniques to do the same).

Oh, any I definitely second WW's comment. :KS

---

### Post by pmasiar on 2008-03-20
Read "how to ask questions" in my sig - and start by creating posts with more meaningfull titles, :-) and mention you level of experience, so people can respond on level you can understand. 

See also sticky FAQ with links to many good resources about C programming.

---

### Post by CptPicard on 2008-03-20
Well, first of all, the whole point of using threads is that you don't need to code your own co-operative multitasking. The OS pre-empts threads whenever it pleases, and it's all transparent to you.

If the only case of thread yielding is with SIGALARM, and you want to hand over processing to something else at that point, I have a feeling that it would be much easier to just abandon the idea of threads completely, just check for the signal and go do something else when it is received...

---

### Post by pleasure on 2008-03-20
Ok Sorry about that. All the stuff below is done in C programming language. I think it requires advanced skills.  I try to clarify as much as i can :

I have to generate randomly 6 matricesnamed A1,A2,A3,A4,A5,A6. All those matrices hav 2 dimentions like A[size][size]. I have to multiply A1*A2 and store in B1. Similaly B2=A3*A4 and  B3=A5*A6. I have to do those multiplication with a thread i create and implement that thread inside that program which has matrix multiplication. 
I have the hint for matrix multiplication:
[PHP]
for(i=0;i<N;i++)
   for(j=0;j<N;j++)
         for(B[i]p[j]=0,k=0;k<N;k++)
                 B[i][j]+=A1[i][k] * A2[i][j];


[/PHP]
I need to have a thread switching to do those so i dont know where to start. Thank you

---

### Post by CptPicard on 2008-03-20
Why can't you use OS threads and just let them be scheduled whichever way it goes, if you really need to be using threads at all (the reason, I assume, is making use of multiple CPUs/cores)?

---

### Post by pleasure on 2008-03-20
i dont know much about threading, the only thing i know  about thread is to do the operation the way we want and i m not supposed to used the thread already had in 0S. That is the purpose of this excercise

---

### Post by LaRoza on 2008-03-20
> **pleasure said:**
> i dont know much about threading, the only thing i know  about thread is to do the operation the way we want and i m not supposed to used the thread already had in 0S. That is the purpose of this excercise

Homework?!

There is a sticky on how to get help with homework.

---

### Post by pleasure on 2008-03-20
no its part of the course im taking for operating system
It is hard :(

---

### Post by LaRoza on 2008-03-20
> **pleasure said:**
> no its part of the course im taking for operating system
It is hard :(

In what way is it hard? The difficult doesn't justify posting school work on this forum.

If it is for personal gain, ok, but the point of courses and schools is to teach. 

Tell us exactly how this relates to the course, and take the advice in the sticky (ask your teacher, or heaven forbid, figure it out with your own research)

"If I did your homework for you, then you might pass your class without learning how to write a program like this. Then you might graduate and get your degree without learning how to write a program like this. You might become a professional programmer without knowing how to write a program like this. Someday you might work on a project with me without knowing how to write a program like this. Then I would have to do you serious bodily harm." [Thanks to Jack Klein]

[http://www.parashift.com/c++-faq-lite/how-to-post.html#faq-5.2](http://www.parashift.com/c++-faq-lite/how-to-post.html#faq-5.2)

---

### Post by ha1f on 2008-03-20
I can't believe that who ever is teaching you this wouldn't have gone over this in class before creating this assignment (or maybe this knowledge was a prereq?).  Pay attention in class.

---

### Post by pleasure on 2008-03-20
Thank you for your advice. But i want to know if there is any real helpful resouces that can help me to have a better understanding of Thread as well the demonstration how to use it:lolflag:

---

### Post by ha1f on 2008-03-20
```

man pthread
man signal

```

---

### Post by pleasure on 2008-03-20
> **ha1f said:**
> ```

man pthread
man signal

```

Thank you half, but there is  no manual for pthread. I know how to use signals. Some of the webs i found just go crazy on Thread make me having a hard time trying to undestand

---

### Post by CptPicard on 2008-03-20
Well, he's not allowed to use pthreads... I still am not quite sure of the point of the assignment, but apparently it has something to do with creating your own "thread library" by longjmping to another function at SIGALARM which is a timer signal(?) I'm actually not a that-low-level geek frankly so I don't really know...

So what we're doing is that you need to

1) Hook up a signal handler to listen to alarm events. When this happens, toggle a flag that signals the timer event

2) Create functions for your "threads". Store their addresses in an array.

3) Every now and then in your functions, call another function, yield().

4) In yield(), check for the timer event flag. If it's not on, return. If it is on, clear the flag and longjmp to the address of the next function in your array

Someone with more low-level C and UNIX experience should scold me now if I'm full of it so that I don't mislead... :)

---

### Post by ruy_lopez on 2008-03-20
For SIGALRM
```

man alarm
man setitimer /* more granular */

```

For pthreads (even though you're not meant to use them)
```

man pthreads

```

Maybe of interest (from clone manpage: "the main use of clone is to implement threads"):
```

man clone

```

---

### Post by pleasure on 2008-03-21
> **CptPicard said:**
> Well, he's not allowed to use pthreads... I still am not quite sure of the point of the assignment, but apparently it has something to do with creating your own "thread library" by longjmping to another function at SIGALARM which is a timer signal(?) I'm actually not a that-low-level geek frankly so I don't really know...

So what we're doing is that you need to

1) Hook up a signal handler to listen to alarm events. When this happens, toggle a flag that signals the timer event

2) Create functions for your "threads". Store their addresses in an array.

3) Every now and then in your functions, call another function, yield().

4) In yield(), check for the timer event flag. If it's not on, return. If it is on, clear the flag and longjmp to the address of the next function in your array

Someone with more low-level C and UNIX experience should scold me now if I'm full of it so that I don't mislead... :)

Thanks CptPicard, i think your steps are very :Dhelpful

---

