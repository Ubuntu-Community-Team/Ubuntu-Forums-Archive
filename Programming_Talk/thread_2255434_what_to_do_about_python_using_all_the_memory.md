---
title: "what to do about python using all the memory?"
date: 2014-12-05
forum: Programming Talk
---

### Post by jeff106 on 2014-12-05
Im new to programming so IDK how to handle all situations. I had a situation earlier where I used up all the memory in a python program and the desktop started to freeze up. Is there a way I can prevent python from doing this? Or do I just have to be savvy with the keyboard and watch out that I never let that happen?

---

### Post by veddox on 2014-12-05
Usually if a program you write as a newbie manages to hog all the memory, there's a coding error in there somewhere... (Believe me, I know from first-hand experience ;-) )

Could you be a bit more specific about what you were trying to do when that happened? Or even better, could you let us see some code? (Use the [code] tags provided by the forum.)

---

### Post by jeff106 on 2014-12-05
I was doing problems on Project Euler(#41)[[https://projecteuler.net/problem=41]](https://projecteuler.net/problem=41]) and I did something that I knew was going to take a lot of memory, but I was just attempting a brute force solution before I moved onto something more efficient.  

I was trying to put together a list of a billion [False] tags to build a Sieve of Eratosthenes

```

x = [False] * 987654321

```

and it just immediately stalled when I started it. Aside from it being an inefficient way of solving the problem, how could I go about avoiding this error and locking up y computer if by accident or on purpose in the future?

---

### Post by veddox on 2014-12-05
I'm not surprised it stalls there ;-)  But there are much more efficient ways of solving that problem, just have a think about it for a while... (A couple of weeks ago I spent ~24h trying to to optimize my code for another Euler problem - I had started off with a similarly brute-force approach, managed to get a final speed increase of something like 3*10^8 times.)  Basically if in future you are worried about one of your programs locking up the computer, adjust your code first to make it more efficient. There will (almost) always be a way. If for some reason you can't, you could try to find the process your program is running in in the system monitor and change its priority, that might help.

---

### Post by ofnuts on 2014-12-05
> **jeff106 said:**
> I was doing problems on Project Euler(#41)[[https://projecteuler.net/problem=41]](https://projecteuler.net/problem=41]) and I did something that I knew was going to take a lot of memory, but I was just attempting a brute force solution before I moved onto something more efficient.  

I was trying to put together a list of a billion [False] tags to build a Sieve of Eratosthenes

```

x = [False] * 987654321

```

and it just immediately stalled when I started it. Aside from it being an inefficient way of solving the problem, how could I go about avoiding this error and locking up y computer if by accident or on purpose in the future?
You can't do much to avoid this if the whole memory is allocated in one python instruction....

It's easy to demonstrate that a pan-digital number of 9 digits cannot be a prime (because the sum of digits 1-9 is a multliple of 9 ((9*(9+1))/2, so all such number are mutiple of 9). So your list is just 87654321 elements and you just went from one gig to a hundred megs (or 400 if python is using 32-bit ints) :)  And with a bit more thinking you can go down to 2160 (still assuming a brute force approach).

---

### Post by veddox on 2014-12-05
Good thinking, ofnuts, but don't spoil the puzzle for us ;-)

---

### Post by kpatz on 2014-12-05
You can use ulimit -v to limit the amount of memory allowed by any program you launch from that shell afterward.

In the below example, I use ulimit -v 250000 to limit python's memory usage to around 250 megabytes (the units are kilobytes).

I recommend doing this in a subshell, because unless you're root you can reduce the limits but can't increase them afterward, and exiting the subshell returns you to the parent shell that doesn't have the limit.  Otherwise you'd have to exit your shell (or log out if you're sshed into a login shell) to undo the limit.

```
kpatz@quattro:~$ bash    # launch a subshell - you'll see why later

kpatz@quattro:~$ python
Python 2.6.5 (r265:79063, Feb 27 2014, 19:43:51)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> x = [False] * 50000000
>>> exit()

kpatz@quattro:~$ ulimit -v 250000    # Set the (sub)shell's virtual memory limit to 250000 kilobytes
kpatz@quattro:~$ python
Python 2.6.5 (r265:79063, Feb 27 2014, 19:43:51)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> x = [False] * 50000000
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
MemoryError
>>> exit()

kpatz@quattro:~$ ulimit -v
250000

kpatz@quattro:~$ ulimit -v unlimited    #Can't do this unless root - thus the reason for the subshell
bash: ulimit: virtual memory: cannot modify limit: Operation not permitted

kpatz@quattro:~$ exit    # Close the subshell that has the limit set

kpatz@quattro:~$ ulimit -v
unlimited

kpatz@quattro:~$

```

ulimit -a shows all the limits that can be set.

```

kpatz@quattro:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 16384
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

---

