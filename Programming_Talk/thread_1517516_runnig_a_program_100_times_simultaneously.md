---
title: "runnig a program 100 times simultaneously"
date: 2010-06-25
forum: Programming Talk
---

### Post by Reyhane_Developer on 2010-06-25
Hi

I faced a problem with my tcsh script. 

I have 2 c++ codes, I compiled them and their execution names are: A.out , B.out
First I want to run A.out and the script should wait as long as this program ends.
Then my script runs "B.out" for 100 times with a while statement, but the problem is that the second "B.out" starts by ending of first "B.out" program.
(the while script waits for each "B.out" program to terminate, and then goes next.)
How is it possible to run the "B.out" for 100 times simultaneously?

Here is my script in tcsh language, thats ok if u can write it with bash or etc.

```
#!/bin/tcsh

set a = "./a.out"
set b    = "./b.out"

${a}

set i = 1
while ( ${i} < 100 )
    ${b} -number ${i}  -o logs/${i}  &
    @ i++
end
```

---

### Post by dwhitney67 on 2010-06-25
Unless you have 100 CPUs, your programs will not be able to run "simultaneously".

You can launch them, one after another, as you have done, but it is possible that one instance of the program will end before you even reach the point where you are launching the Nth instance.

Regardless, even if you successfully launch 100 instances of your application (and btw, you are only launching 99 in your script), these will _share_ the CPU(s) your system possesses.  Undoubtedly, the majority of these processes will be dormant while a few actually get a chance to "run", and then you must also consider that you have other processes running on your system that must share the same system resources.

You may want to consider looking into multi-threading, but even this may not solve the issue you are facing.

---

### Post by Reyhane_Developer on 2010-06-25
Thanks dwhitney, O:)
Yeah You are right, I made a mistake and the while works for 99 times, but the number is not really important.;-)
I know the fact of cpu proccesses being shared, yet it's not the matter,
Actually I am trying to solve a problem with ant colony optimization (ACO) algorithm, and as this is a collective behavior algorithm,
I should run the ants together like the players of a soccer team.

Do You think my script works? :-k

---

### Post by dwhitney67 on 2010-06-25
> **Reyhane_Developer said:**
> Thanks dwhitney, O:)
Yeah You are right, I made a mistake and the while works for 99 times, but the number is not really important.;-)
I know the fact of cpu proccesses being shared, yet it's not the matter,
Actually I am trying to solve a problem with ant colony optimization (ACO) algorithm, and as this is a collective behavior algorithm,
I should run the ants together like the players of a soccer team.

Do You think my script works? :-k

I have more familiarity with a real ant colony, having stepped in quite a few as a child.  As for the ACO algorithm, no I'm not familiar with it.

As for your script, it will launch N version of b.out, and each will run in the background.  Whether the programs run forever is dependent on how you wrote the code.  Thus I don't know whether you will have N instantiations of the application running on your system, or whether they will exit after a very brief period before you ever get around to launching the Nth application.

---

### Post by Reyhane_Developer on 2010-06-25
when I  write a code like below:

set program = "./pro.out"
${program}
echo "Yes"
[B]
Do You think the script waits for program termination or it will go to next line and echo Yes without a pause ?[/B] :confused:

***if** You think that it goes to next line, without a pause, so my first script faces this problem:
As I want to wait for "A.out" to end, I should add a wait script.

***else if** You think that this script waits for program termination, so my script has a problem with the while!
As Certain You Know, my ants (B program) are like soccer players , and I should run them together. (each B program takes a long period about 15 minutes, but their processor usage is not too high)

so whether your answer is yes or no, still there is something wrong in my code, and I don't know how to solve it.   ](*,)  :-(

---

### Post by soltanis on 2010-06-26
Yes, any Bourne shell will wait for the process to finish, and I imagine that **tcsh** probably does too. In **sh**, the command would have an ampersand appended to it, like so

```

command -options foo &

```

The result is that the shell forks before executing the command in its own process, i.e. running it in the "background" instead of the "foreground" (where you would have to wait for it to finish).

If all you are trying to do is run instances of a program simultaneously, then this should be sufficient for your needs. If you're trying to run a simulation where the programs are interacting with each other, your C++ programs will need to have some way of communicating with each other, however, which I hope you realize.

---

### Post by Reyhane_Developer on 2010-06-26
> **soltanis said:**
> Yes, any Bourne shell will wait for the process to finish, and I imagine that **tcsh** probably does too. In **sh**, the command would have an ampersand appended to it, like so

```

command -options foo &

```The result is that the shell forks before executing the command in its own process, i.e. running it in the "background" instead of the "foreground" (where you would have to wait for it to finish).

Great Answer! \\:D/

I didn't know this !!! :-D


> **soltanis said:**
> If you're trying to run a simulation where the programs are interacting with each other, your C++ programs will need to have some way of communicating with each other, however, which I hope you realize.

Yeah, I've taken it into consideration already, their communications works well.

Thanks soltanis and dwhitney67,
U Really Helped me.
O:)

---

