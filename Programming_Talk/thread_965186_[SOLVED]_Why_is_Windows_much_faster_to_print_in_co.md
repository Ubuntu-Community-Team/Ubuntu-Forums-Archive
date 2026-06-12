---
title: "[SOLVED] Why is Windows much faster to print in console from a fortran program?"
date: 2008-10-31
forum: Programming Talk
---

### Post by hutxubix on 2008-10-31
Hello,

I am working on some codes for numerical stuff that are programed in fortran (I am compiling with Intel Fortran Compiler)

The original subroutines print information of every iteration on the console, saying things like number of iteration, time elapsed and time expected to finish.

I found that the real bottleneck is printing in the console this information, because if I do not print, the algorithm goes perhaps 20 times faster.

My advisor uses windows XP, and it goes very fast for him, as printing in the console is very very fast.

I am using statements like

      WRITE (*,104) CHAR(13), I, NFR, ETIM, PTIM, RTI
104   FORMAT (A1,' FREQ.', I4, ' of', I4, ' , T.E.T. =', E16.5,
     * ', A.P.T. =', E16.5, ', E.R.T. =', E16.5, /)

Has anyone any clue about this?
Is really anoying to have Window faster in such a thing!!!

---

### Post by LaRoza on 2008-10-31
Faster than what?

---

### Post by hutxubix on 2008-10-31
Faster in printing the information on the console.

Te same program, with the same parameters, takes say 20 seconds for me in ubuntu and 2 seconds for him in Windows. It is not because his computer is better, or because of optimization parameters of the compiler, and if I remove my printing in the console the algorithms takes something like one second. So, printing in the console is taking too much time in ubuntu and I do not know why.

---

### Post by hutxubix on 2008-10-31
Faster in printing the information on the terminal.

Te same program, with the same parameters, takes say 20 seconds for me in ubuntu and 2 seconds for him in Windows. It is not because his computer is better, or because of optimization parameters of the compiler, and if I remove my printing in the console the algorithms takes something like one second. So, printing in the console is taking too much time in ubuntu and I do not know why.

---

### Post by the_one(2) on 2008-10-31
I'm guessing it has something to do with buffering. The more that is buffered the faster printing to the console is (don't know anything about fortran though).

---

### Post by dribeas on 2008-10-31
> **hutxubix said:**
> Faster in printing the information on the terminal.

Te same program, with the same parameters, takes say 20 seconds for me in ubuntu and 2 seconds for him in Windows. It is not because his computer is better, or because of optimization parameters of the compiler, and if I remove my printing in the console the algorithms takes something like one second. So, printing in the console is taking too much time in ubuntu and I do not know why.

I guess you should be more specific about what 'terminal' is in ubuntu. In windows it is the cmd terminal, but in ubuntu you could be using gnome-terminal, konsole, xterm (any of N variants of it) or the real text console.

Maybe you should try one of these options:
[LIST]
[*]Try different graphic terminals (start with plain xterm)
[*]Use the text console
[*]Redirect output to a file and later read that file (less)
[/LIST]

---

### Post by hutxubix on 2008-11-02
Wow,

You have taught me something new.

Times for the same executable with the same data in different terminals:

xterm:                        1.17 s
Ctrl+Alt+F1 (text console??): 2.54 s
terminal 2.22.1:              7.523 s

I really didn't now this difference. Now it keeps the pace of Windows. 

Why is terminal so slow?

Thanks

---

### Post by angustia on 2008-11-02
> **hutxubix said:**
> 
...

Why is terminal so slow?

Thanks

maybe because they use antialiased fonts, or something like custom backgrounds...

---

### Post by dribeas on 2008-11-03
> **hutxubix said:**
> Why is terminal so slow?

Because it does not need to be faster (at least to the great majority of users).

The console is a user interface, and usually the bottleneck in performance is not there but on the calculus underneath. If the output of the program can be read by a user as it is being processed, then the user will not notice the performance issue. If a user cannot process the output, then it will be fed to another process or output redirected to a file. If output is redirected, the terminal performance does not affect the user in any way.

Now, the user wants fancy features like antialiasing of fonts, full UTF with khanji characters (not that you will use or understand them) and a beautiful watermarked image.

Try redirecting your input to a file:
```
$ program > output.txt
```

---

### Post by hutxubix on 2008-11-04
The use of the output was printing the iteration on which the program is working and the remaining time.

Depending on the problem, this output can be very fast or not, but I would not redirect it to a file (unless one reads it with something like "tail -f").

What do you think?

---

### Post by dribeas on 2008-11-04
> **hutxubix said:**
> The use of the output was printing the iteration on which the program is working and the remaining time.

Depending on the problem, this output can be very fast or not, but I would not redirect it to a file (unless one reads it with something like "tail -f").

What do you think?

You are right, there is no sense in 'storing' the equivalent of a progress bar for 'later processing'. Some (to huge) performance gains could be achieved by reducing the number of times that the system outputs progress (say, only once of every 10 (20, 30...) times you do output now)

---

### Post by hutxubix on 2008-11-05
That's really the answer,

Thank you!

---

### Post by raf_kig on 2008-11-06
Instead of doing the ouput every n-th loop (which will give varying results based on the system/load/etc) just make it update the output every n secs.

Regards

raf

---

