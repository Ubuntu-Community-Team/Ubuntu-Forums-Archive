---
title: "Permission"
date: 2011-12-13
forum: Programming Talk
---

### Post by achuth on 2011-12-13
Sir, 
Suppose I have created a file named "myfile" with the following content:
***echo "Hello World"***

When I type **"./myfile"** at the prompt, is gives permission denied error.
but When I use **"bash myfile"** to execute, then there is no permission denied error. Why is it so?


What is the difference between these two ways of executing the script?

---

### Post by drmrgd on 2011-12-13
The reason is because you didn't make the file executable.  To do that, issue:

```
chmod +x myfile
```

Then when you try to run it as you have, it will work.  Asking bash to run it as you did, avoided having to make it executable in order to run.

---

### Post by Bachstelze on 2011-12-13
> **achuth said:**
> 
What is the difference between these two ways of executing the script?

The difference is that with [font=monospace]./myfile[/font] you are executing the script directly, while with [font=monospace]bash myfile[/font], you are executing Bash and telling it to execute the script. If you want to go the first way, you have to add a ["shebang"](http://en.wikipedia.org/wiki/Shebang_%28Unix%29) line nd make the script executable with [font=monospace]chmod +x[/font].

---

### Post by Telengard C64 on 2011-12-13
> **Bachstelze said:**
> If you want to go the first way, you have to add a ["shebang"](http://en.wikipedia.org/wiki/Shebang_%28Unix%29) line nd make the script executable with [font=monospace]chmod +x[/font].

Strictly speaking the *shebang* line isn't required, but it is a good idea to always include it.

By the way, if you want your script interpreted by BASH then please use

```
#! /bin/bash
```

---

### Post by CoffeeRain on 2011-12-13
I find it easier to tell Bash to execute the file. The way to do this, is to end the filename with .sh and then execute it with ```
bash myfile.sh
``` In Python it is .py and run by saying ```
python myfile.py
```

---

### Post by sisco311 on 2011-12-13
sh is not bash. The .sh extension serves no purpose, and it's completely misleading. Scripts define new commands that you can run, and commands are generally not given extensions.

[http://mywiki.wooledge.org/BashGuide/CommandsAndArguments#Scripts](http://mywiki.wooledge.org/BashGuide/CommandsAndArguments#Scripts)
[http://www.in-ulm.de/~mascheck/various/shebang/](http://www.in-ulm.de/~mascheck/various/shebang/)

---

### Post by fdrake on 2011-12-13
> **Telengard C64 said:**
> Strictly speaking the *shebang* line isn't required, but it is a good idea to always include it.

By the way, if you want your script interpreted by BASH then please use

```
#! /bin/bash
```

i disagree! how is the system supposed to know if you are running  a bash, perl or python script then? shebang line is not an option. maybe your system can try to run a txt file as a bash script due to some configurations but that not work for othe kind of scripts.. unless you run them trought the interpreter itself:  "/bin/python myscript"

---

### Post by Telengard C64 on 2011-12-13
> **sisco311 said:**
> sh is not bash. The .sh extension serves no purpose, and it's completely misleading.

The only purpose served by such an extension is to inform human users what interpreter the script is intended for. In the context of CoffeeRain's reply you are correct, of course. The **.sh** implies a traditional **sh** shell script, whereas CoffeeRain clearly intends the script to be interpreted by BASH.

```
test$ ls -gGh $(which sh)
lrwxrwxrwx 1 4 2009-04-02 11:12 /bin/sh -> dash
test$
```

[http://manpages.ubuntu.com/manpages/oneiric/en/man1/dash.1.html](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dash.1.html)
[http://packages.ubuntu.com/oneiric/dash](http://packages.ubuntu.com/oneiric/dash)
[http://gondor.apana.org.au/~herbert/dash/](http://gondor.apana.org.au/~herbert/dash/)

---

### Post by CoffeeRain on 2011-12-13
> **sisco311 said:**
> sh is not bash. The .sh extension serves no purpose, and it's completely misleading. Scripts define new commands that you can run, and commands are generally not given extensions.

My computer must be configured differently or something. It gets confused without it. Anyways, it's still a good idea so you know what type of program you are running so you know to use bash instead of something else.

Oh, didn't see Telengard's reply.

---

### Post by Telengard C64 on 2011-12-13
> **fdrake said:**
> "/bin/python myscript"

That works 100% of the time, assuming you really know the location of the interpreter (not hard to discover).

I'm interested to know why you disagree with my use of *shebang* in my scripts. Care to elaborate?

---

### Post by CoffeeRain on 2011-12-13
I think they misunderstood, and thought you meant the location of the interpreter was not needed.

---

### Post by Bachstelze on 2011-12-13
> **Telengard C64 said:**
> Strictly speaking the *shebang* line isn't required, but it is a good idea to always include it.


Uh, no.

---

### Post by sisco311 on 2011-12-13
> **fdrake said:**
> i disagree! how is the system supposed to know if you are running  a bash, perl or python script then? shebang line is not an option. maybe your system can try to run a txt file as a bash script due to some configurations but that not work for othe kind of scripts.. unless you run them trought the interpreter itself:  "/bin/python myscript"

If the shebang is not present, the OS will try to run the script (any executable plain text file) in the invoking user's default login shell. Ergo the shebang is not mandatory, and the script will work if it's written in the user's login shell.

---

### Post by Telengard C64 on 2011-12-13
> **CoffeeRain said:**
> I think they misunderstood, and thought you meant the location of the interpreter was not needed.

Maybe. I really wanted to encourage OP to learn and use *shebang*. That's why I provided a proper example. It's just the right thing to do, at least on Ubuntu.

---

### Post by fdrake on 2011-12-13
> **Telengard C64 said:**
> That works 100% of the time, assuming you really know the location of the interpreter (not hard to discover).

I'm interested to know why you disagree with my use of *shebang* in my scripts. Care to elaborate?let's say someone writes a script for you for to execute some kind of processing data.. instead of just running the script and get the process running you first have to open the script find out what kind of language is it and then use the interpreter to run the data. There are some langages that they look just the some.... 

of course this example and other involving "bash" scripts maybe left aside but you always have to take for granted that the users login shell is/bin/bash.. which may not be always the case.... in the end it's the prefered thing to do even nobody will die because of it...

---

### Post by Telengard C64 on 2011-12-13
> **Bachstelze said:**
> Uh, no.

When is it not a good idea to include a *shebang*? Care to explain?

---

### Post by Telengard C64 on 2011-12-13
> **sisco311 said:**
> If the shebang is not present, the OS will try to run the script (any executable plain text file) in the invoking user's default login shell. Ergo the shebang is not mandatory, and the script will work if it's written in the user's login shell.

Exactly this. The *shebang* is not strictly required. When you include a properly written *shebang* it is used to run the appropriate interpreter.

I'm still waiting to learn why one would not use *shebang*.

---

### Post by Telengard C64 on 2011-12-13
> **fdrake said:**
> let's say someone writes a script for you for to execute some kind of processing data.. instead of just running the script and get the process running you first have to open the script find out what kind of language is it and then use the interpreter to run the data. There are some langages that they look just the some.... 

of course this example and other involving "bash" scripts maybe left aside but you always have to take for granted that the users login shell is/bin/bash.. which may not be always the case.... in the end it's the prefered thing to do even nobody will die because of it...

Sounds like you are making the case in favor of *shebang*. So what is your disagreement?

---

### Post by fdrake on 2011-12-13
> Strictly speaking the shebang line isn't required, but it is a good idea to always include it.
it should be "Strictly speaking the shebang line [COLOR="Red"] in this case[/COLOR](bacaue your login shell is /bin/bash and because you are running a bash script) isn't required, but it is a good idea to always include it."

the first one to a new user may sound like "it's not really neccessary but you can put it once in a while...."

the second one explain exactly why is not required because of the previous reasons

i know what you mean in your sentence but to a new user may soud a little confusing also I know this is a forum not a court of sentence-structure-nazies...  :D

edit:
so I will end my post by saying that I am glad the OP solved the problem but even more because he learned a lot of new stuff from our discussion.

---

### Post by Arndt on 2011-12-13
> **sisco311 said:**
> If the shebang is not present, the OS will try to run the script (any executable plain text file) in the invoking user's default login shell. Ergo the shebang is not mandatory, and the script will work if it's written in the user's login shell.

No. From "man execve":

```
      execve() executes the program pointed to by filename.  filename must be
       either a binary executable, or a script starting with  a  line  of  the
       form:

           #! interpreter [optional-arg]

```

What the shell does when asked to execute a file without a #! line is something else, defined by the shell, not by the OS.

---

### Post by Arndt on 2011-12-13
> **CoffeeRain said:**
> My computer must be configured differently or something. It gets confused without it.

In what way does it get confused?

---

### Post by fdrake on 2011-12-13
> **Arndt said:**
> No. From "man execve":

```
      execve() executes the program pointed to by filename.  filename must be
       either a binary executable, or a script starting with  a  line  of  the
       form:

           #! interpreter [optional-arg]

```

What the shell does when asked to execute a file without a #! line is something else, defined by the shell, not by the OS.

the os defines users shell> the shell defines how to run a script > and so on.. 

actually i would agree with both of you because when you configure the OS and the users ( in /etc/passwd) you are assigning them to the desidered shell. but you can also assign a /bin/nothin or any file you want even /bin/shutdown

---

### Post by Telengard C64 on 2011-12-13
> **fdrake said:**
> i know what you mean in your sentence but to a new user may soud a little confusing

Ah, so I failed to make my case strongly enough, and therefore my statement should be disregarded. Is that it?

**_For the record_**

On existing Ubuntu installations in the default configuration, BASH is the interpreter of choice for any script invoked as **./script**, but only when said script does not contain an interpreter specifier in the form of **#! interpreter [option]** (known colloquially as *shebang*) as the first line of the script. Therefore, although not strictly required, you are encouraged to always include *shebang* in your shell scripts to avoid any possible ambiguity as to which interpreter is the intended target for the script. Whereas multiple interpreters may coexist on GNU/Linux systems, including Ubuntu, and Ubuntu includes an additional interpreter for *Bourne-style* shell scripts named **dash**, the intended interpreter for any particular shell script can not be always assumed to be BASH, but rather should specified with a *shebang*.

Does that cover it? Did I miss some loopholes?

---

### Post by Arndt on 2011-12-14
> **fdrake said:**
> the os defines users shell> the shell defines how to run a script > and so on.. 



The shell 'bash' comes with the OS, but you can use any shell you want; you can even write your own.

---

### Post by sisco311 on 2011-12-15
> **Arndt said:**
> No. From "man execve":

```
      execve() executes the program pointed to by filename.  filename must be
       either a binary executable, or a script starting with  a  line  of  the
       form:

           #! interpreter [optional-arg]

```

What the shell does when asked to execute a file without a #! line is something else, defined by the shell, not by the OS.

I stand corrected. Thanks.

---

