---
title: "setting enviroment variables for use in a script from a 'C' program"
date: 2009-08-15
forum: Programming Talk
---

### Post by Keith Hedger on 2009-08-15
Hope someone can help with this, I want to be able to set an environment variable from an external c program that is readable by the calling script, I can read the variables using getenv() and can alter them using setenv() but once the program terminates the changes are lost.

---

### Post by uljanow on 2009-08-15
That's not possible. The program gets a pointer to a copy of the environment variables.

---

### Post by dwhitney67 on 2009-08-15
You could always have the C program launch the script using one of the exec family of functions; perhaps the execle() could be used.

If launching the script from the C program is not an option, then as uljanow pointed out, you would be up the creek without a paddle.  The C program, once launched (say from a shell), runs in an environment that is separate from the one that launched it.  It merely has a copy of the environment variables when it is launched.

The C program can set environment variables (using setenv()) within its own environment, but this has no effect on other environment(s).

---

### Post by MadCow108 on 2009-08-15
I don't think starting a shell script from C will help because the script again will run in its own enviroment

---

### Post by dwhitney67 on 2009-08-15
> **MadCow108 said:**
> I don't think starting a shell script from C will help because the script again will run in its own enviroment

I believe it is possible to configure the environment in which the script runs.  I do not have any experience doing this, but I think execle() allows for this.

---

### Post by soltanis on 2009-08-15
When you start a sub-process, that process inherits the environmental variables of the one that launched it.

So yes, it would help, assuming you set all the variables you wanted to, then launched the sub-processes (by forking and then exec'ing, or just straight exec'ing).

Look at execve + buddies for replacing process images, or system() for forking then running processes in the background.

---

### Post by MadCow108 on 2009-08-15
as far as I understand execle only allows to change the enviroment variables of the new process image but does not change the original environment
but I never used it myself so I may have misinterpreted.

---

### Post by soltanis on 2009-08-15
Yes, you can't change the original environment variables using this method. But the question is, why would you want to?

---

### Post by Keith Hedger on 2009-08-16
Well I thought I was on to a loser with this one as I have tried various things and googled all sorts of combinations and had no luck, thanks for the help anyway!

---

### Post by MadCow108 on 2009-08-16
if you call the c program with a script, why not just set the enviroment variables in the script?

---

### Post by Keith Hedger on 2009-08-16
> **soltanis said:**
> Yes, you can't change the original environment variables using this method. But the question is, why would you want to?

I've written a program to read/set music tags from an mp3/flac/m4a file and a conversion script, so I wanted to read the tags and set enviroment variables then convert the file and write the tags to the new file using the variables, at the moment I read the tags and output the results on stdout and assign them them to vars convert the file and then set the tags on the new file, really I just wanted to do all this in one go.(it sounds more complex than it is!)
In case anyone is interested it can be found here:
[http://sourceforge.net/projects/kute/](http://sourceforge.net/projects/kute/)

---

