---
title: "How can one execute an external program without waiting for it to finish?"
date: 2011-01-13
forum: Programming Talk
---

### Post by TheHimself on 2011-01-13
When I use system() or popen() my program halts until the external one is finished  but I don't want that. I'd also like the external program  to continue  even if my program is closed.

---

### Post by sharathcshekhar on 2011-01-13
You have to make your program run in multi threads/Process.. There is no other way to make a non blocking system call..

---

### Post by rnerwein on 2011-01-15
> **TheHimself said:**
> When I use system() or popen() my program halts until the external one is finished  but I don't want that. I'd also like the external program  to continue  even if my program is closed.
hi
it looks like you are programming C languge.
then you can do ( what even servers do and get rid of child procs - no zombies ) then uses any kind of
exec:
fork -> fork -> exec ( have a look of "man exec" ).
hint: if you use popen --> don't forget pclose or you will get zombie processes because pclose will be mayde
the embedded wait for you.
ciao
p.s. C is lake a razor but without a grip

sorry this one of the first try and the ubuntu server told me ---> fault :-)

---

### Post by rnerwein on 2011-01-15
> **TheHimself said:**
> When I use system() or popen() my program halts until the external one is finished  but I don't want that. I'd also like the external program  to continue  even if my program is closed.
hi
looks like you are programming in C.
system and popen is quite nice but i prefere " variants of exec calls".
first is: system allays wait for ending of the sub procress. but dangerouse of popen is that programmers forget the "pclose" and this results in zombie prosesses.
i use --> " fork - > fork --> exec" ( have a look at the man pages for the different kind of exec " to get 
rid of defunct processes.
ciao
 

sorry this was the second try and the ubuntu server told me ---> fault  :-))

---

### Post by rnerwein on 2011-01-15
> **TheHimself said:**
> When I use system() or popen() my program halts until the external one is finished  but I don't want that. I'd also like the external program  to continue  even if my program is closed.
hi
looks like you are programming in C.
system and popen is quite nice but i prefere " variants of exec calls".
first  is: system allays wait for ending of the sub procress. but dangerouse  of popen is that programmers forget the "pclose" and this results in  zombie prosesses.
i use --> " fork - > fork --> exec" ( have a look at the man pages for the different kind of exec " to get 
rid of defunct processes.
ciao
oh i see - every thing works before - sorry for all this qoutes

---

### Post by dwhitney67 on 2011-01-15
> **TheHimself said:**
> When I use system() or popen() my program halts until the external one is finished  but I don't want that. I'd also like the external program  to continue  even if my program is closed.

Run the external program in the background.  For example:
```

system("/path/to/external_program &");

```
Similarly with popen() you can run a program in the background, but this seems fishy/silly.
```

FILE* pd = popen("/path/to/external_program &", "r");
...
pclose(pd);

```

---

### Post by TheHimself on 2011-01-24
Re dwhitney67, what does the operator & do exactly?

---

### Post by Arndt on 2011-01-24
> **TheHimself said:**
> Re dwhitney67, what does the operator & do exactly?

From the bash manual page:

       "If  a  command  is terminated by the control operator &, the shell exe&#8208;
       cutes the command in the background in a subshell.  The shell does  not
       wait  for  the command to finish, and the return status is 0."

---

### Post by TheHimself on 2011-01-31
Thanks dwhitney67 and Arndt!
:guitar:

---

