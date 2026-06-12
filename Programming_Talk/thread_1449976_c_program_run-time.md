---
title: "c program run-time"
date: 2010-04-08
forum: Programming Talk
---

### Post by crowhill on 2010-04-08
hi there!

i'm trying to improve my c code. the result of this effort should be that the overall time required for the program to run is shorter. in order to be able to measure my success or failure i need to be able to compare the run-time before and after the change of the code.

how to i print the run-time of a c program to a file? which lines of code do i have to include?

if it can't be done from within the c program, is there a way to get the run-time of my c program from a tool such as **top**? (Type **top** in the command line and you get to see the running processes.) how to make **top** to print the run-time to a file?

thanks a bunch in advance,
cheers,
crowhill.

---

### Post by falconindy on 2010-04-08
use the `time` builtin of bash.

---

### Post by crowhill on 2010-04-08
i read about it but couoldn't find a simple example. do you have one? how do i use it?

---

### Post by doas777 on 2010-04-08
try not to fixate on time for performance optimization, but on raw operations. a given operation will take more or less time based on the system on which it is run, so the performance can be considered to be a function of the number of operations x the time each op takes. this is a very fine number though, so usually people focus on loops and flow control structures when determining optimality. 

look into Big-O analysis of algorithms to determine the number of ops, and the ideal run time:
[http://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation/](http://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation/)

[http://en.wikipedia.org/wiki/Big_O_notation](http://en.wikipedia.org/wiki/Big_O_notation)

---

### Post by doas777 on 2010-04-08
```

karmic:~$ time ls
Desktop    Downloads  Pictures    Templates  tmp
Documents  Music      Public

real    0m0.041s
user    0m0.004s
sys    0m0.028s
karmic:~$ 

```

---

### Post by crowhill on 2010-04-08
thx a lot for the reply.

the concern i have is this:
1. i ssh into a another (very fast) computer.
2. i compile my code by gcc code.c -o code -lm
3. i run my code by ./code &
4. then i type disown to be able to log out and log back in and everything is still there (the code runs several hours up to several days)

now with time ./code & and disown, how would i be able to get the output of time? how to print its output to a file?

thx and cheers,
crowhill.

---

### Post by doas777 on 2010-04-08
> **crowhill said:**
> thx a lot for the reply.

the concern i have is this:
1. i ssh into a another (very fast) computer.
2. i compile my code by gcc code.c -o code -lm
3. i run my code by ./code &
4. then i type disown to be able to log out and log back in and everything is still there (the code runs several hours up to several days)

now with time ./code & and disown, how would i be able to get the output of time? how to print its output to a file?

thx and cheers,
crowhill.
I'm told that Screen is execelent for handling resumable ssh sessions and whatnot.
you wouldn;t want to run anything with "time" as a background proc as that would defeat the purpose as you pointed out.

---

### Post by crowhill on 2010-04-08
> you wouldn;t want to run anything with "time" as a background proc as that would defeat the purpose as you pointed out.

can you clarify, please?

thx :)

---

### Post by wmcbrine on 2010-04-08
> **crowhill said:**
> 4. then i type disown to be able to log out and log back in and everything is still there (the code runs several hours up to several days)Interesting, I hadn't heard of "disown" before. But yeah, I'd use "screen" for this:

```
$ screen
$ time ./code
$ ^A d
[time passes]
$ screen -r
[see the output]
$ exit
```

---

### Post by doas777 on 2010-04-08
& at the end of a command runs it as a background process, meaning the shell lets go of it. you don't generally get messages from it in the shell anymore once it is put in the background. time is a program that runs in the forground, and runs another program in the background. it pipes back the output of the subcommand, followed by it;s own output. since the time command is being run in the background you would have to redirect sdtout to get the times when you are done. in theory it would be like:
```
time <command> > outputfile &
```
then you would have to read the output file to get the time.

---

### Post by MadCow108 on 2010-04-08
I never heard of disown before (my system does not even have a manpage for it...) but it is really useful, too often I forget to start my programs with nohup or screen, thanks :)

for your problem redirection is probably the way to go.
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)
but with the bash builtin time it is a bit tricky. It will only redirect the output of the command it executes and not the output if time
The solution is to start it in a subshell:
(time command) 2> log.txt
2> only redirects stderr to a file
the same can be archived by writing a script:
#!/bin/bash
time $1
and execute that with normal redirection

You can also use the unix time command. This saves you the subshell stuff.
It is usually installed in /usr/bin
So to get the time do this:
/usr/bin/time command > log.txt 2>&1
2>&1 redirects stderr to stdout so you can capture both

---

### Post by falconindy on 2010-04-08
> **MadCow108 said:**
> I never heard of disown before (my system does not even have a manpage for it...) but it is really useful, too often I forget to start my programs with nohup or screen, thanks :)
It's a shell builtin, see man (1)bash. Also, if you're using bash, you can use the bashism &> to redirect both stdout and stderr at the same time.

---

### Post by crowhill on 2010-04-08
thx for the many answers.

to sum up, can i do the following?

1. ssh to remote machine
2. gcc code.c -o code -lm
3. time ./code &> duration.txt &
4. disown
5. exit
6. wait until done
7. log back in
8. be happy and open duration.txt

is this the way to go?

thx so much!

---

### Post by crowhill on 2010-04-08
i tried the above:

1. in the terminal window i get the output
[B]real	30m39.445s
user	27m21.463s
sys	3m17.756s[/B]

2. after the above output i'm not getting back the command line ... is there's some process that's sill running?

3. the file duration.txt is empty!

how to fix this? does disown kill the workings of time and redirection?

---

### Post by crowhill on 2010-04-08
ok, i figured it out:

replace 

> 3. time ./code &> duration.txt &

by 

3. (time ./code) &> duration.txt &

that does the trick.

thx so much for everything!

---

### Post by doas777 on 2010-04-09
I think you may wanna drop the interior '&' as you would want everything to run in the background, but since you got it going to your satisfaction, enjoy.

---

