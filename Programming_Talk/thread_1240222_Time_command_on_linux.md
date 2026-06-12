---
title: "Time command on linux"
date: 2009-08-14
forum: Programming Talk
---

### Post by studybuddy09 on 2009-08-14
Can someone please tell me what is the[COLOR=Black] time[/COLOR] command on linux and what is its syntax?

Also how does one use it to compare different programs??

---

### Post by Mirge on 2009-08-14
man time

---

### Post by MadCow108 on 2009-08-14
actually man time mostly gives the man for the time in /usr/bin
bash has its own time which with less (or other) options.
so don't be suprised when the command line arguments don't work in bash (except you explicitly call the right time)

---

### Post by geirha on 2009-08-14
Indeed.
```
$ type time
time is a shell keyword

```

If it's a shell builtin or keyword, check the shell's man-page, or in the case of bash, use the help command
```
$ help time
time: time [-p] PIPELINE
    Execute PIPELINE and print a summary of the real time, user CPU time,
    and system CPU time spent executing PIPELINE when it terminates.
    The return status is the return status of PIPELINE.  The `-p' option
    prints the timing summary in a slightly different format.  This uses
    the value of the TIMEFORMAT variable as the output format.
times: times
    Print the accumulated user and system times for processes run from
    the shell.

```

---

### Post by MindSz on 2009-08-14
```
$ date

```

prints local (or what your system considers local) date and time.

---

