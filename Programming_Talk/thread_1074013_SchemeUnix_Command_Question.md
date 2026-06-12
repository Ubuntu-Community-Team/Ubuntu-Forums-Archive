---
title: "Scheme/Unix Command Question"
date: 2009-02-18
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-02-18
I need to execute a system command in Scheme, (system ??) just doesn't cut it. I need to execute the command and read the output as a string.

I would like to do this by using IOStreams that lisp support, so its the same as reading and writing to a file. The two ways to do this are, either Scheme supports an already defined method or Unix has a set of files (devices) that do console IO like stdout/stdin.

I would prefer the second, because this is far more versitile, but I don't know if that exists.

---

### Post by Mr.Macdonald on 2009-02-18
Seeing as there are no responses, I wish to broaden the question.

Could I use the system function, and read stdout into a string? Would that do the same?

Also tell me anything that might help on my quest (like "thats, impossible").

---

### Post by geirha on 2009-02-19
I have never tried scheme, at all, but since you haven't gotten a reply yet...

In python, when you want to read the output of a command, you create a pipe with popen. Popen starts the command and returns a pipe object that handles just like a file object. If you write to the pipe, you write to stdin of the process. If you read from the pipe, your read from stdout of the process. See if you can find any popen equivalent in scheme.

---

### Post by nvteighen on 2009-02-19
In MIT/GNU Scheme: [http://www.gnu.org/software/mit-scheme/documentation/mit-scheme-ref/Subprocesses.html](http://www.gnu.org/software/mit-scheme/documentation/mit-scheme-ref/Subprocesses.html)

---

### Post by Cracauer on 2009-02-19
> **Mr.Macdonald said:**
> Seeing as there are no responses, I wish to broaden the question.

Could I use the system function, and read stdout into a string? Would that do the same?

Also tell me anything that might help on my quest (like "thats, impossible").

Dude. Without telling us which of the gazillion scheme variants you use it'll be very, very hard to answer that question.

---

### Post by Mr.Macdonald on 2009-02-19
> Dude. Without telling us which of the gazillion scheme variants you use it'll be very, very hard to answer that question. 
I have found scheme variants to be very similar, but I am using scm.

there isn't a popen function.

How about a Unix solution, like a device?

---

### Post by Cracauer on 2009-02-19
> **Mr.Macdonald said:**
> I have found scheme variants to be very similar, but I am using scm.

there isn't a popen function.

How about a Unix solution, like a device?

If your loser scheme implementation doesn't have a universal run-process thingy that allows you to specify what to do with the output via a couple parameters (hell, even Emacs Lisp has one), then yes, you could do a system() call redirecting output to a name pipe and you can open that named pipe in scheme. Of course if you don't have threads this can turn into a synchronization nightmare.

---

### Post by Mr.Macdonald on 2009-02-19
> If your loser scheme implementation doesn't have a universal run-process thingy

Have you used scm, or are you assuming. I haven't found anything wrong with scm. If your scheme has a process execution then tell me because my scheme probably has the same one.

Scheme has a standard, anyone can implement it and they normally follow the standard when they do. You scheme is the same as mine (for the most part). Scheme is a Lisp not Lisp, Lisp has a million variants. And Emacs Lisp isn't Scheme, so you are wrong to relate them.

When I said there isn't a popen function, I mean't that there is no definition for "popen". There could be a function that does the same task.

Don't assume that I know every function in any scheme, thats why I am asking.

---

### Post by nvteighen on 2009-02-20
> **Mr.Macdonald said:**
> Have you used scm, or are you assuming. I haven't found anything wrong with scm. If your scheme has a process execution then tell me because my scheme probably has the same one.

Scheme has a standard, anyone can implement it and they normally follow the standard when they do. You scheme is the same as mine (for the most part). Scheme is a Lisp not Lisp, Lisp has a million variants. And Emacs Lisp isn't Scheme, so you are wrong to relate them.


Yes, there's a Scheme standard (R5RS and the newr R6RS). The problem: nobody follows it. For example, the PLT Scheme family uses "print" where the MIT familiy uses "display" (the standard)... And then you have lots of non-standard features that you use without ever noticing what's really standard and what's not (ever used while, when, unless? Those are PLT built-ins... or the REPL modifiers MIT/GNU uses, etc.).

---

### Post by Mr.Macdonald on 2009-02-20
Apparently I was wrong about the whole scheme people following the standard. So lets change the question,

Is there a means to execute system commands in Unix, by reading/writing to device files or other such tools?

---

### Post by Cracauer on 2009-02-20
> **Mr.Macdonald said:**
> Apparently I was wrong about the whole scheme people following the standard. So lets change the question,

Is there a means to execute system commands in Unix, by reading/writing to device files or other such tools?

I already said it. You just use the non-output system() call to first create a named pipe, then start the command with that pipe as output, then read from that pipe.

You also need to see whether your scheme's Lisp implementation has options to output to a string. In the Lisp world, system() and popen() are usually the same thing just different paramters to the same function.

---

