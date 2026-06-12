---
title: "timing the execution of a program"
date: 2009-07-08
forum: Programming Talk
---

### Post by flylehe on 2009-07-08
Hi,
Is there a way to show when the running of a program starts and finishs in linux terminal? I heard "time" but it seems only give the time elapsed.
Thanks and regards!

---

### Post by Simian Man on 2009-07-08
You could do:
```
date && program && date
```

Which would give you the time right before and right after it ran.

---

### Post by flylehe on 2009-07-08
Thanks!
My program will output a lot to the screen and sometimes possibly bump the beginning out of the screen. How can I get the start time in such case?

---

### Post by johnl on 2009-07-08
Try something like this:

date | tee time.log && program && date | tee -a time.log


"date | tee time.log" will print the current time and also write it to time.log
"date | tee -a time.log" will print the current time and append it to time.log

This way you will see the output on the console, but also in the time.log file.

ex:

$ date | tee time.log && program && date | tee -a time.log

Wed Jul  8 12:49:33 MDT 2009
....
Wed Jul  8 12:49:41 MDT 2009

$ cat time.log

Wed Jul  8 12:49:33 MDT 2009
Wed Jul  8 12:49:41 MDT 2009

---

### Post by fensirien on 2009-07-08
If you want to see the result immediately in the console:

```
start=`date` && program && echo $start && date
```

---

### Post by stroyan on 2009-07-08
If you have started a program from bash shell then you can see the start
time in the output of history by setting the shell variable HISTTIMEFORMAT
to a string that matches the strftime() function.  See "man bash" and
"man strftime".  (You may need to "apt-get install manpages-posix-dev".)

HISTTIMEFORMAT='%r - ' history 5

Of course, there may be a substantial delay between when the application
finished and the time that you note that it finished.  A following "date"
command or having a "\t" in your PS1 prompt variable would tell you more
accurately when the command completed.

---

