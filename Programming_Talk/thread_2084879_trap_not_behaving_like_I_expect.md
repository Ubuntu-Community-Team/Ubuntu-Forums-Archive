---
title: "trap not behaving like I expect"
date: 2012-11-16
forum: Programming Talk
---

### Post by floobit on 2012-11-16
I'm trying to determine what kill signals sshd sends a child process when a session disconnects, and thought I'd write a simple bash script that catches all the signals and writes them to a file, then exits.  I am having a hard time with trap, however.  Here is a sample program: 
```
#!~/bin/bash
echo $$ 
trap "echo banana" 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64
while true;
do
sleep 9999;
done
```

I run this.  Say the pid is 7878.  In a separate window, I run 
```
kill -s 15 7878
```

I would expect the text "banana" to show up in my window.  This does not occur.  However, if I do a kill -9 7878, the process dies successfully with only the standard "Killed" as output.  Also, if in the window running my script, I do ctrl-C, "banana" is returned.  

I am perplexed.  Thoughts?

---

### Post by Vaphell on 2012-11-16
it works just fine, but you cannot trap SIGKILL (9). It's unconditional, it gives no time to gracefully exit. Bam, you are dead.

```
echo $$
for i in {1..20}; do trap "echo trap: $i" $i; done
while :; :; done

```
```

$ ./trap.sh  |
7796         |
^Ctrap: 2    | $ kill 7796
trap: 15     | $ kill -s 7 7796
trap: 7      | $ kill -s 10 7796
trap: 10     | $ kill -s 9 7796
Killed       |
```

---

### Post by spjackson on 2012-11-16
When you send the signal to bash using kill, bash won't respond to the signal while it is waiting for sleep to complete. When you hit Ctrl-C in the terminal, it is the sleep process that receives the INT first.

---

### Post by floobit on 2012-11-19
Thanks, all.  As spjackson suggested, the sleep command was interfering with trap.  when I switched to an active wait (as in Vaphell's example), I got normal behavior.  Not the behavior I'd expect for sleep, but I'm sure the wise and powerful maintainers of bash have a good reason for doing it this way.

---

