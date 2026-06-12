---
title: "whats the point of shell scripting?"
date: 2010-02-25
forum: Programming Talk
---

### Post by WinterMadness on 2010-02-25
can someone explain it to me? it does not seem very difficult to grasp, but i dont see why i would want to do this if i could just write a program that does the same thing in a language such as c++.

please enlighten me. :)

give any kind of examples you can think of of where its useful

---

### Post by dwhitney67 on 2010-02-25
Ah, it seems another line has been cast to troll the forum for biased responses.

The most obvious reason for using a script versus a C/C++ application is that it does not need to be compiled on each machine where it is used.  There are no dependencies to worry about, other than having the appropriate shell interpreter available; since these are included in most Linux distros, it's rarely ever a concern.  Ubuntu is the holdout because it does not include /bin/bash until it is installed after the initial installation.

I'm sure there will be other replies, but I am done here.

---

### Post by steviefordi on 2010-02-25
It's horses for courses really. In my opinion administrative tasks that involve finding, moving, removing and backing up files can be scripted more quickly and easily using bash. 

Similar functionality written in C for such tasks will usually (not always) take many more lines of code. When you have more code, you have more opportunity for bugs to arise + programs can become more unreadable.

C is a great tool, but is more low-level than many day-to-day coding tasks require.

---

### Post by benj1 on 2010-02-25
[http://catb.org/~esr/writings/unix-koans/ten-thousand.html]("http://catb.org/~esr/writings/unix-koans/ten-thousand.html")

---

### Post by nischalinn on 2010-02-25
There are many advantages of shell programing over other compilers. It's easy to debug and no need of compilation steps with shell but the main problem with shell is it's late execution speed.

---

### Post by Bachstelze on 2010-02-25
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

> Why do you need to learn the command line anyway? Well, let me tell you a story. Not long ago we had a problem where I used to work. There was a shared drive on one of our file servers that kept getting full. I won't mention that this legacy operating system did not support user quotas; that's another story. But the server kept getting full and stopping people from working. One of the software engineers in our company spent the better part of a day writing a C++ program that would look through the directories of all the users and add up the space they were using and make a listing of the results. Since I was forced to use the legacy OS while I was on the job, I installed a version of the bash shell that works on it. When I heard about the problem, I realized I could do all the work this engineer had done with this single line:

```
du -s * | sort -nr > $HOME/space_report.txt

```

---

### Post by nvteighen on 2010-02-25
Because shell scripting languages are specialized in process managament, while C++ is aiming towards general programming and therefore, it may lack features that might help you do it more easily.

It's just a matter of practicity.

---

### Post by spupy on 2010-02-25
> **dwhitney67 said:**
> Ah, it seems another line has been cast to troll the forum for biased responses.

The most obvious reason for using a script versus a C/C++ application is that it does not need to be compiled on each machine where it is used.  There are no dependencies to worry about, other than having the appropriate shell interpreter available; since these are included in most Linux distros, it's rarely ever a concern.  Ubuntu is the holdout because **_it does not include /bin/bash until it is installed after the initial installation._**

wat? :shock:

---

### Post by The Cog on 2010-02-25
> **nvteighen said:**
> Because shell scripting languages are specialized in process managament, while C++ is aiming towards general programming and therefore, it may lack features that might help you do it more easily.

Absolutely. You aould argue (and I do) that the difference between a scripting language and a programming language is just that - programming languages are for general purpose programming, and scripting languages are aimed at being a script (as in a theatrical script - directions for an actor to follow) - that automates the something a user/technician would otherwise have to do manually. The most basic scripts tend to be just a few commands - copy a file then delete the original for instance. Or the one-liner posted above.

---

### Post by LintonHanes on 2010-02-25
bash is the basis man"

besides it's just a shell in a C environment right? and much like C anyhoose

---

### Post by CptPicard on 2010-02-25
> **The Cog said:**
> Absolutely. You aould argue (and I do) that the difference between a scripting language and a programming language is just that - programming languages are for general purpose programming, and scripting languages are aimed at being a script 

Nvteighen was specifically speaking of *shell* scripts, which do this sort of stuff on system commands, process management and so on... things the user might do on the command line. Of course the general meaning of "scripting language" is ill-defined and tends to be used as a bit of a term of abuse by people who insist on a definition of "programming language" as a language that compiles into a native binary, say.

But where to draw the line in "general purpose programming" is of course maybe *the* age-old discussion here. There are, of course, very specialized languages for specific problem domains -- they may even lose Turing-completeness in the process, but those don't count, IMO... shell scripting has indeed made so many choices in the direction of serving a particular problem domain that it no longer works "reasonably well for anything".

---

### Post by blur xc on 2010-02-25
> **WinterMadness said:**
> can someone explain it to me? it does not seem very difficult to grasp, but i dont see why i would want to do this if i could just write a program that does the same thing in a language such as c++.

please enlighten me. :)

give any kind of examples you can think of of where its useful

Here's a little script I use to transfer files from my compact flash card to folder arranged by date on my external hard drive.

I just wrote it in a bout 10 mins (my scripting kung-fu is weak).  I know next to nothing about programming in C (hello world is WAY over my head) so for the purpose of illustrating the benefits of shell scripting over C programming for the tasks shell scripting is intended, please write an equivalent program in C to my crappy little script.

```
#!/bin/bash

FILEPATH=`date +%Y/%Y-%m-%d`

if [ -d $FILEPATH ]; then
    echo "The directory already exists"
else
    mkdir -pv $FILEPATH
fi

find /media/disk/DCIM -type f -exec cp -v '{}' $FILEPATH \;

```

---

