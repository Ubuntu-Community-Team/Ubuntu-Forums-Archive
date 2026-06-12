---
title: "[SOLVED] Measuring execution speed?"
date: 2008-06-05
forum: Programming Talk
---

### Post by nvteighen on 2008-06-05
Hi there,
I've seen people claiming their code runs at "x seconds", but I don't understand how that time is measured. Of course, you can't measure 0.34 secs so easily in a watch, so I suppose there's a tool that does this work.

Thanks in advance.

---

### Post by mike_g on 2008-06-05
you could add a timer to your program. In C you could look up using get_time_of_day. Theres also the clock() function in time.h, but in linux I think it measures clock cycles. 

Then just get the start time before your do what you want.
When you have finished get the end time.
Subtract the start time from the end time, and you get the time elapsed.

---

### Post by Lau_of_DK on 2008-06-05
Hi,

If you do some Lisp you can use a little macro I made, you can pass any function or body of functions to it, and it will output the result and the time it took to compute

[php]
(defmacro time-it (&rest body)
  `(let ((start (get-universal-time)))
    (progn (print ,body))
    (format t "~%~%Execution: ~d seconds~%" (- (get-universal-time) start))))
[/php]

so an example could be
```

(time-it (map #'evenp '(1 2 3 4 5 6)))
(2, 4, 6)
0.0001 seconds

```

/Lau

---

### Post by CptPicard on 2008-06-05
A very common alternative is to just use the "time" command in the shell.

---

### Post by robheus on 2008-06-05
```

time ls -l

real	0m0.740s
user	0m0.008s
sys	0m0.012s

```

---

### Post by nvteighen on 2008-06-06
Thanks for your input!

The "time" command is all I wanted, I think.

Actually, I won't use this that much. It was just the concept; I'm not a speed-obsessive (but a memory management one... that's another story).

---

