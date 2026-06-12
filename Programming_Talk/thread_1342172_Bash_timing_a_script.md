---
title: "Bash: timing a script"
date: 2009-11-30
forum: Programming Talk
---

### Post by tg1w on 2009-11-30
Hi

I need to benchmark a certain application and I want to use bash for this. I have already read that there is a **/usr/bin/time** program, apart from bash's own time command.

I have two questions:
[LIST=1]
[*]/**usr/bin/time** outputs the "elapsed real time" and also the time spent by the program in user/kernel mode. Which of these is most relevant. If I am running other processes in the background, both elapsed time and user mode time are affected - there is no pure timing of a certain process
[*]**/usr/bin/time** outputs to stderr. How may I collect the information in a variable (for example, with argument '/usr/bin/time -f "%e" some_program' I should obtain the execution time in seconds of "some_program". I cannot however say execution_time=/usr/bin/time -f "%e" some_program
[/LIST]

Thank you all very much. PS: Still gaining experience in Ubuntu, so bare with me.

---

### Post by Martin Witte on 2009-11-30
Maybe [this link]("http://tldp.org/HOWTO/KernelAnalysis-HOWTO-3.html") helps understanding te difference between kernel mode and user mode

---

### Post by tg1w on 2009-12-02
> **Martin Witte said:**
> Maybe [this link]("http://tldp.org/HOWTO/KernelAnalysis-HOWTO-3.html") helps understanding te difference between kernel mode and user mode

Thank you very much. It makes now sense why an application run in user mode, will also involve kernel mode operations.

Would it sound reasonable then to time my simulation by summing the user mode and kernel mode times? Would it be more representative than just using the user mode?

Thank you all.

---

### Post by tg1w on 2009-12-02
**/usr/bin/time** outputs to stderr. How may I collect the information in a variable (for example, with argument '/usr/bin/time -f "%e" some_program' I should obtain the execution time in seconds of "some_program". I cannot however say execution_time=/usr/bin/time -f "%e" some_program

---

### Post by Arndt on 2009-12-02
> **tg1w said:**
> **/usr/bin/time** outputs to stderr. How may I collect the information in a variable (for example, with argument '/usr/bin/time -f "%e" some_program' I should obtain the execution time in seconds of "some_program". I cannot however say execution_time=/usr/bin/time -f "%e" some_program

For example:

```
$ \time sleep 5 2>/tmp/timefile; execution_time=`cat /tmp/timefile`
```

There is also an --output option to 'time'. What do you want to happen if the program also outputs on stderr?

---

### Post by tg1w on 2009-12-02
> **Arndt said:**
> For example:

```
$ \time sleep 5 2>/tmp/timefile; execution_time=`cat /tmp/timefile`
```

There is also an --output option to 'time'. What do you want to happen if the program also outputs on stderr?

Interesting solution. The above, I presume, uses bash's time function, rather than /usr/bin/time. 

My main goal is to execute a number of simulations, time each of them individually and then display the total/average time.

I just read about times... maybe it would be better to use it, instead of doing arithmetical operations with time.

---

### Post by tg1w on 2009-12-02
> **tg1w said:**
> Interesting solution. The above, I presume, uses bash's time function, rather than /usr/bin/time. 


I wonder why using read doesn't solve the situation:

```

$ /usr/bin/time sleep 1 2>&1 | read -s sleep_time
$ echo $sleep_time

$

```

---

### Post by Arndt on 2009-12-02
> **tg1w said:**
> Interesting solution. The above, I presume, uses bash's time function, rather than /usr/bin/time. 




No, it does not. The backslash inhibits the builtin function. I just didn't want to spell out where the program is, even if it's unlikely to be somewhere else.

With bash's builtin time function, it's harder to redirect its output, maybe not possible.

---

### Post by tg1w on 2009-12-02
[QUOTE=Arndt;8425395]For example:

```
$ \time sleep 5 2>/tmp/timefile; execution_time=`cat /tmp/timefile`
```

Could you please help me out with the arithmetic operations too?

If I want to get only the user mode seconds, the results will be something like 
```

$ \time -f "%U" sleep 1 2>/tmp/timefile; execution_time=`cat /tmp/timefile`
$ echo "$execution_time"
0.00
$

```

That x.xx is anything but something that I can add then to other simulation times. Bash also doesn't support float numbers.

Any help is welcomed. Thank you very much all.

---

