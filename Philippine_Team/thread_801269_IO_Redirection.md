---
title: "I/O Redirection"
date: 2008-05-20
forum: Philippine Team
---

### Post by Africanne on 2008-05-20
Haay...Though i've read a lot on the subject, i still can't grasp it. Even on windows, im not much familiar with the commands and syntaxes, coz i relied much on GUI. 

As according to what i understood, CLI is much powerful on certain tasks.

So Please, please, please help me understand these better:

1. What exactly is the standard input and output is for, and why the heck it's important.

2. And what does Pipes and Filters do?

Tsalamats..:confused:

---

### Post by loell on 2008-05-20
hmm.. how does one explain this concisely in layman's term? :D

1.standard input is the keyboard , and standard output is the screen, usually characters/letters.

2. pipes are.. when you think of a water pipe the water must pass through there, right?  and so characters/letters will pass through there reaching the other end which may be a program waiting for those characters/letters to be processed.  

filtering, think of it as a  strainer (pang-sala), sasalain mo ang gusto mong makuha. ;)

---

### Post by issih on 2008-05-20
Hmmn

This is by no means an exhaustive list of what you can do, but hopefully it will help you get the idea.

programs generally have an input, and an output. When we are talking about cli stuff, both the input and the output will be text of some form.

So at the most basic level you have the text you put in (input),
and the text that comes out (output).

The terms standard input and standard output then refer to the normal methods of entering the input and receiving the output. Generally that will be the keyboard and the screen respectively...simple enough really.

The important point is that the input and output of a program are just text, and can be something other than the "standard" ones

The simplest example is that you can redirect output to a file instead of standard output (the screen)

so:

```
ls -a
```

Will work out a list of all the files in the current directory, then (as nothing else is specified) write it to the standard output (print it to the screen)

 
```
ls -a > myFiles.txt
```

Does exactly the same thing, but the > myFiles.txt bit redirects the output so the list of files is written to the myFiles.txt file rather than to the screen.

In a similar vain inputs can come from the contents of a file rather than the standard input using <.

Pipes are similar to redirection, but rather than just sending the output to a different destination, a pipe links the output of one command to the input of another, it pipes the data from one command to the next.

as an example:

```
ps -eaf
```

will list all the processes running on your system on standard output


```
ps -eaf | grep gnome* 
```

here the process list output is piped to the input of the grep command, which filters the list so only processes starting with 'gnome' are kept...this filtered list is then written to standard out

I hope that helps a bit

---

### Post by Africanne on 2008-05-21
Gee..thanks a lot. I got it now!

---

