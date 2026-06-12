---
title: "[SOLVED] script syntax questions"
date: 2008-10-09
forum: Programming Talk
---

### Post by lovinglinux on 2008-10-09
A few questions about script syntax and rules.

I know I have to start the script with

```
#!/bin/bash 
```

but do I need to finish the script with something or it will just close after running all commands? 

Do I really need to use "**;**" after a command? I have a few scripts with several commands and they run just fine without anything between them.

If I want to wait for a command to execute before executing the next one I have to add "&&" between them. So, if the command 1 is to run a program, then the second command will only run after closing the program started by command 1 right? What about just "&"?

---

### Post by schauerlich on 2008-10-09
You might get better help for this question in the [Programming Talk subforum](http://ubuntuforums.org/forumdisplay.php?f=39). Be sure to read the stickies, they contain a lot of good information. I've asked a mod to move this thread, so no need to start a new one in PT.

---

### Post by lovinglinux on 2008-10-09
> **EDavidBurg said:**
> You might get better help for this question in the [Programming Talk subforum](http://ubuntuforums.org/forumdisplay.php?f=39). Be sure to read the stickies, they contain a lot of good information. I've asked a mod to move this thread, so no need to start a new one in PT.

Sorry. I thought these questions were too basic to be posted elsewhere and I usually get a lot of help about simple command questions here.

---

### Post by Rocket2DMn on 2008-10-09
Moved to Programming Talk.

---

### Post by Sam on 2008-10-09
> **lovinglinux said:**
> A few questions about script syntax and rules.

I know I have to start the script with

```
#!/bin/bash 
```

but do I need to finish the script with something or it will just close after running all commands?
No need to add something at the end.

> **lovinglinux said:**
> Do I really need to use "**;**" after a command? I have a few scripts with several commands and they run just fine without anything between them.
You don't need to add a semicolon.

> **lovinglinux said:**
> If I want to wait for a command to execute before executing the next one I have to add "&&" between them. So, if the command 1 is to run a program, then the second command will only run after closing the program started by command 1 right? What about just "&"?
The "&&" means that the second program is only run if the first one exits with no error (error code). The "&" means that the previous command will be forked.

---

### Post by lovinglinux on 2008-10-09
> **Sam said:**
> No need to add something at the end.


You don't need to add a semicolon.


The "&&" means that the second program is only run if the first one exits with no error (error code). The "&" means that the previous command will be forked.

Thank you. Sorry for my bad English, but I don't know what forked means in this context. What I can understand is that both commands will run at the same time and if you stop one the other will also stop. Is that correct?

---

### Post by wd5gnr on 2008-10-09
If you say:

foo &
bar &

Then foo and bar will run more or less at the same time. Bar might finish first or foo might finish first.

If you write:

foo && bar

Then foo will start and then if it is successful bar will start

if you write:

foo ; bar

then foo will run and after it is done (no matter what happens) bar will run.

---

### Post by lswb on 2008-10-09
Hi, I'll try to answer your questions.

No special command or statement is needed at the end of script but you can use the exit command to exit the script at any time or if you want to return a specific value from the script. ( exit n where n is the numerical value being returned)

For shell scripts, a semicolon ; is required to separate commands that otherwise would be on separate lines.  These could be separate simple commands, e.g

echo Directory List; ls ; echo End of list

or keywords that are used together like if/then/else/fi. For instance, to execute a command if a certain file exists, you could use

    if [ -e filename ]; then command; fi
and this would be equivalent to:
   if [ -e filename ]
   then
   command
   fi

Very often you will see "then" tacked on at the end of the "if" statement like this:

if [ -e filename ]; then

command 
command
command
fi

There are also some special uses for the ; like in case/esac statements.

separating commands with && will cause the second command to run only if the 1st completes without errors. So if you need the 2nd to run regardless of whether the 1st ran successfully or not, put the 2 commands on separate lines, or separate them with ;

a single & at the end of a command causes it to run in the background. The next command will start without waiting for the command with the & to complete.

There's a good bash scripting tutorial (html) in the repositories, search for "abs-guide" in synaptic. It's ususally a couple versions old, for the most up-to-date go right to the authors website at [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by Sam on 2008-10-09
No. forked means that the command is run in background (read [this](http://en.wikipedia.org/wiki/Fork_(operating_system)))

If you stop one it won't stop the other command.

Examples:```
command1
# wait until command1 is done, then execute command2
command2
```

```
command1 &
# run command1 and send it to background, it will finish when it's over
command2
# command2 will run in parallel with command1. Either command1 or command2 can end first, and it won't get any incidence to the other process

```

```
command1 && command2
# first command1 is run, and only if it exits with no error code, command2 is run
```

---

### Post by lovinglinux on 2008-10-09
Thank you all. Everything is clear now.

---

