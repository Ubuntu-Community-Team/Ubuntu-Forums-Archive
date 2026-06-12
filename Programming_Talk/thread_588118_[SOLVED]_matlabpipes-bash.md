---
title: "[SOLVED] matlab/pipes-bash"
date: 2007-10-23
forum: Programming Talk
---

### Post by Claus7 on 2007-10-23
Hello,

I want to change directory while using matlab, yet the path will be given by a command using bash.

Up to now with this command : ```
find -name "name_of_directory" | matlab
```
I can print to matlab the path I want, yet I'm not able to change to this directory.
I also tried ```
cd `find -name "name_of_directory"` | matlab
```, yet with no results.

Has anyone any idea of how I will be able to use the command cd *inside *matlab, yet the path given *outside* of it?
For example maybe using pipes differently? 
In case someone has any other idea I will ble glad to hear.

Regards!

---

### Post by cwaldbieser on 2007-10-24
If you want to change the current working directory before invoking matlab, a simple script like:
```

#! /bin/bash

cd /some/dir
matlab

```

Should work.  You can include logic to get the directory name before cd'ing.

---

### Post by Claus7 on 2007-10-24
Hello,

this is the point : I want to change the directory not **before** invoking matlab, yet **after** I have started matlab **inside** matlab.
About the logic thing you said I didn't understand what you mean. I neither find a bash command nor a matlab one. Could you be a little more precise in this?

Thank you!
Regards!

---

### Post by cwaldbieser on 2007-10-24
> **Claus7 said:**
> Hello,

this is the point : I want to change the directory not **before** invoking matlab, yet **after** I have started matlab **inside** matlab.
About the logic thing you said I didn't understand what you mean. I neither find a bash command nor a matlab one. Could you be a little more precise in this?

Thank you!
Regards!

I haven't had experience with the matlab program, but I am not sure I follow what you mean by changing the current directory "inside" matlab.

If your shell script sets its current directory to "/foo/bar", then starts the matlab program, matlab will be a child process of the shell and inherit the current directory from it.

Maybe if you explained a little more about what you are trying to accomplish by changing the current directory inside matlab, the situation would become more clear.

---

### Post by Claus7 on 2007-10-25
Hello,

[http://web.cecs.pdx.edu/~gerry/MATLAB/howTo/setMATLABpath.html](http://web.cecs.pdx.edu/~gerry/MATLAB/howTo/setMATLABpath.html)
There it sais :
On DOS and Unix computers the current working directory is the directory you were in when you typed ``matlab'' to launch MATLAB.

The truth is that on one computer this is really the case. On my computer I cannot do that. From wherever I try to open matlab if I type pwd (in matlab) then the path it returns is /home/"user_name"/matlab

That would have been a nice solution, avoiding the pipes.
I'm focusing on this and see how I will be able to configure it.

Regards!

---

### Post by Claus7 on 2007-10-25
Hello,

What I wanted to do is to do post process with matlab in a specific directory. 

I did knew the name of the directory, yet I didn't want to supply the path manually. Instead with the command find I wanted to "pass" the output of this command (which is the path of the directory) to matlab via a pipe.

Yet  cwaldbieser said :

> If your shell script sets its current directory to "/foo/bar", then starts the matlab program, matlab will be a child process of the shell and inherit the current directory from it.

As a result I wanted to see if matlab understood the working directory every time I invoked the program inside that directory. From wherever I tried the output of the command pwd was /home/"user_name"/matlab .

In another linux system with matlab that was not the case. So I was curious why in my system that's didn't work.

I started to check it out further and the folloing link was the one that I stepped upon :
[http://maven.smith.edu/~nhowe/teaching/csc370/mconfig.html](http://maven.smith.edu/~nhowe/teaching/csc370/mconfig.html)

There it stated about a file called **startup.m** This file is responsible of what matlab will do at startup.

I typed (in /home/"user_name") :
find -name "startup.m"
and the result was :
./matlab/startup.m

This file had the following :
cd /home/"user_name"/matlab/

I comment it out with % (not # because that's the comment symbol in matlab) and my problem was solved. Wherever I opened matlab and typed pwd the path was the current one.

For anyone who wants to see a discussion about pipes concerning this problem, yet with no result, I provide the following link :
[http://mathforum.org/kb/thread.jspa?forumID=80&threadID=1644293&messageID=5962522#5962522](http://mathforum.org/kb/thread.jspa?forumID=80&threadID=1644293&messageID=5962522#5962522)

Thank you!
Regards!

---

