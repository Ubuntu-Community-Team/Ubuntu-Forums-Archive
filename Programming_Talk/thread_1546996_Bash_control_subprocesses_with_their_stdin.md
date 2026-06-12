---
title: "Bash: control subprocesses with their stdin"
date: 2010-08-06
forum: Programming Talk
---

### Post by liviogasp on 2010-08-06
Hi,
I'm trying to learn to use Bash: I work on some linux machines, and it's useful to do some scripts that do some simple and repetitive jobs.
Now here is the problem: I have a simulation running in the background, its output are some text files, each formed by two colums: simulation time and some value at that simulation time. I use gnuplot to view the status of the simulation while it's running, and I wrote an octave script that control a gnuplot process through a pipe and continuously re-plot  the updated data.
Now I would like to use the same script on an other machine, where octave is not installed, so thought to use bash instead, but I don't know how to do it, and after looking for a solution on google for a while, now I'm here to ask for some help from you.
The code in octave that do the work is this:

```
  Octave code:

1   gplt=popen('gnuplot','w');
2   fputs(gplt,sprintf('some_string\n'))
```

The man pages for popen (it's c, I know, but I it's the same in this case) "The  popen() function opens a process by creating a pipe, forking, and invoking the shell". So the first line opens a new process "gnuplot", and conntects its stdin to a pipe.
gplt is the file id of the pipe, that I can use to write something in the stdin of the launched process. So I can write in the pipe with something like the second line, and gnuplot execute the command contained in "some_string".

I know that I can create a child process "gnuplot" from bash with

> gnuplot &

and I can read the child's PID, so I can kill it. Is there a way I can input commands to the child process whenever I want?
Thanks

---

### Post by DaithiF on 2010-08-06
Hi,
I imagine you could use a named pipe to send commands to gnuplot.  so:
1. create a named pipe:
```
mkfifo mypipe
```
2. run gnuplot, using mypipe for its stdin
```
gnuplot < mypipe &
```
3. to send commands to gnuplot write them to the pipe:
```
echo "somecommand" > mypipe
```
or
```
cat "filewithcommands" > mypipe

```

---

### Post by liviogasp on 2010-08-06
Thanks for the reply DaithiF.
I tried to use named pipes in a way similar to the one you suggested, but that's not exactly what I want to do: when I use

```
gnuplot < mypipe &
```I create a gnuplot process that waits for somethin to be written in 'mypipe'; when it finds something it executes the commands, and then the process quits. 
What I want is to create a single process "gnuplot" in the background, that executes the instructions I give it some way, then it waits in the background for more instructions, and again it executes some new instructions when I give them, until I give it the command 'exit'. 
That's what I can do with my octave script: I start the process as I said, and whenever I use the command
```

fputs(gplt,sprintf('some_string\n'))
```I can give instructions always to the same gnuplot process.
Any ideas?

---

### Post by DaithiF on 2010-08-06
I've no particular experience with gnuplot so this is largely guesswork, but try this:

```
mkfifo mypipe
gnuplot firstfile - <(tail -f mypipe) &

```then echo commands to mypipe as before

---

### Post by liviogasp on 2010-08-06
> **DaithiF said:**
> I've no particular experience with gnuplot so this is largely guesswork, but try this:

```
mkfifo mypipe
gnuplot firstfile - <(tail -f mypipe) &

```then echo commands to mypipe as before

Ok, I made it, following your suggestion: the working one is:

```
(tail -f mypipe) | gnuplot
```

and then I can control the gnuplot process! And better: if I append the &>> log I can read any error in output of gnuplot from the file log. 
When I exit the gnuplot process tail is still there, until I echo one more  command (I can write anithing), and then tail stops itself, too

Thanks DaithiF, you where really helpfull!

---

