---
title: "&quot;time&quot; command and gettimeofday disprepency"
date: 2008-11-28
forum: Programming Talk
---

### Post by DBQ on 2008-11-28
Hi everybody. I am trying to time my program (wall clock time).  Here is how i do it:

```

gettimeofday(&t1,NULL);
.
.
do_stuff();
gettimeofday(&t2,NULL);

timersub(&t2,&t1,&t3);

double elapsed = (double)(t3.tv_sec) + (double)(t3.tv_usec) * 1e-6;
cout << "elapsed: " << elapsed << endl;
exit(0);

```

When I do this i get this output from my program: 

elapsed: 0.00047

When I comment out all the time keeping code, and just do this at the command line: 

bash$ time prog

real	0m0.219s
user	0m0.184s
sys	0m0.032s

I get the output above.  Thats a HUGE discrepancy! My question is why?  I am aware that my code above (in the code tags) does not take the exiting of the program into account (ie the exit(1) system call), and the time command does.  But it seems a little odd that the discrepancy is so high.  Any explanations? I am doing something wrong?

---

### Post by slavik on 2008-11-28
one thing to keep in mind is that time looks at the whole run of a program. what you are doing is benchmarking a piece of it.

---

### Post by DBQ on 2008-11-28
Yes I know.  The piece of code I was timing was my whole program.  However, I did find the reason.  My timing did not take into account the initializations of some constructors which were declared globally.  Now I understand.  But thank you in any case.

---

