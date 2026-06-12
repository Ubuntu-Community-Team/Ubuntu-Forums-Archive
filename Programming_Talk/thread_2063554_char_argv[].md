---
title: "char* argv[]"
date: 2012-09-27
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-27
Hey,
Is it possible to get the arguments in argv[], even when instead of <Enter>, some other key, say tab is pressed ?

What I want is
```

$Name_Of_ObjectFile ubu<tab>

```

This should run the object file, with the argument as ubu.
Please advise.
Thanks.

---

### Post by Bachstelze on 2012-09-27
Short answer: no.

1) You can't run an object file, you probably meant "executable".
2) Unless you modify your shell, the program is not run until the Enter key is pressed.

---

### Post by MadCow108 on 2012-09-27
> **Bachstelze said:**
> 
2) Unless you modify your shell, the program is not run until the Enter key is pressed.

no need to modify the shell for that, every more advanced shell has this feature builtin. tab completions can perform arbitrary tasks, also stuff not related to the completion (though it might get a little tricky to clear the prompt after the execution)
But it is a very bad idea! it totally goes against what users expect from completions

there are plenty guides found with google, search for bash tab completion or programmable completion

---

### Post by Bachstelze on 2012-09-27
> **MadCow108 said:**
> no need to modify the shell for that, every shell has this feature builtin.

on default ubuntu systems google for bash completion

Excuse me? Shell completion does not run the program...

{i]EDIT:[/i] Well, sure, it can be programmed to. But for crying out loud, why whould anyone want to do that?

---

### Post by MadCow108 on 2012-09-27
normally not, but it can.
advanced bash completion beyond the default just execute bashscripts which agian can execute whatevery they want.
E.g. scp completions can query file listing on the remote machine you want to scp from provided the authentification is passwordless (e.g. via keys), very useful!
git completions complete tag and branch names by executing git itself to get them (so its even aware of our aliases)
probably what op wants to do is very similar to what git does.

look at the stuff in the bash-completion package, there is a lot interesting stuff in there.

---

### Post by IAMTubby on 2012-09-28
> **Bachstelze said:**
> 
1) You can't run an object file, you probably meant "executable".

Bachstelze, sorry for that. Googled up the difference, and I now understand that in an object file, linking is not done with the libraries, and so, it cannot be executed. Thanks for that.

Please look below for my queries on Tab Completion. Not mixing with this post as it is slightly off-topic with respect to the original post.
Thanks.

---

### Post by IAMTubby on 2012-09-28
> **MadCow108 said:**
> 
there are plenty guides found with google, search for bash tab completion or programmable completion
> **Bachstelze said:**
> Shell completion does not run the program...

Thanks for the response MadCow108,Bachstelze. I googled for some of those, but most info I found like complete and compgen don't allow to run an executable. They only allow to write your custom string to tab-complete. Am I reading the wrong documents? 

> **MadCow108 said:**
> normally not, but it can.
advanced bash completion beyond the default just execute bashscripts which again can execute whatever they want.

This would be wonderful if it works! Can you provide me some info on how to get started with this.




My approaches:
--------------
1)Download the bash code, I downloaded bash-2.0.tar.gz and try and figure out how the tab-complete works. Haven't gone through the code yet.

2)Look in the ls/cat/cd code, to see how it handles tab-complete.(But I could be wrong and **by the time control comes to ls/cat/cd, the tab-complete part is already done by bash.**
I have downloaded coreutils-5.0.tar.bz2. Haven't gone through the code yet.

3)Download kernel source code and see where tab-complete comes. I don't think this is a right approach. It's not the kernel that takes care of tab-complete.

4)compgen . As Bachstelze mentioned above, I don't think this can be used to execute a program.

Will you be able to tell me if I'm missing the right approach, and/or which of these approaches is correct. I think 1) is the right approach.
Please advise.
Thank you MadCow108, Bachstelze.

---

### Post by IAMTubby on 2012-09-28
Can I add 1 more approach?
5) Is it possible to trick both the shell/bash and the user such that,
**Let the user enter <Tab>, but the shell thinks that <Enter> is entered** and so, responds by running the executable. Is it possible to do some ascii-value aliasing or something of that sort ?

Sorry for the newbie ideas. But really excited to find a solution to this problem.

Thanks.

---

### Post by IAMTubby on 2012-09-28
Just an additional info, my shell is 
```

# echo $0
-sh

```
It doesn't have tab-complete for anything, be it ls/cd etc.

My intention is to give it tab-complete option for my application alone and not for the entire shell(not really required).
Please refer my first post, if I'm not clear replacing the word ObjectFile with executable(thanks to Bachstelze).

Thanks.

---

### Post by trent.josephsen on 2012-09-28
Why would you do that? Are you going to distribute this modified shell with your program?

It sounds like you're trying to make the shell itself part of the user interface to your program. This is a Bad Idea. It runs contrary to the [principle of least surprise](http://en.wikipedia.org/wiki/Principle_of_least_astonishment) and violates modularity on several levels. It's also contrary to the [Unix philosophy](http://en.wikipedia.org/wiki/Unix_philosophy), if you're into that kind of thing.

If this tab-to-run thing is an essential part of your program, then you shouldn't be abusing a shell to make it happen -- it should be part of your program's UI code.

If, on the other hand, this is just a convenience feature for you, and you have some odd reason for not wanting to press Enter (amputated right pinky?) then feel free to do it any way you can figure out.

N.B. /bin/sh is a very simple shell. If I wanted this feature, and my primary concern was that it run programs, I'd probably just write my own shell. Even with a rudimentary command history buffer, it would probably take less time than figuring out how to make bash do it without odd side effects. Obviously this isn't an option if the shell needs support for control structures like for, while, if etc.

---

### Post by IAMTubby on 2012-09-28
> **trent.josephsen said:**
> 
(amputated right pinky?)
:lolflag:

> 
Why would you do that?

The whole application is a CLI.
I, at any point, do not know if the user wants to enter a shell command like cd/ls etc or a command from the application.
So, I cannot make it a part of the UI, because once I enter the UI, I won't be able to come out of it to process a shell command.

So, I basically need something sitting 1 level over the bash.

---

### Post by trent.josephsen on 2012-09-28
> **IAMTubby said:**
> The whole application is a CLI.
I, at any point, do not know if the user wants to enter a shell command like cd/ls etc or a command from the application.
Easy. If they're running your program, they want to control your program. If they want to run cd or whatever, they can do that from a real shell.

If you want to allow the user to run commands from within your program, keep reading...

> So, I cannot make it a part of the UI, because once I enter the UI, I won't be able to come out of it to process a shell command.
No, but if you want your users to be able to invoke shell commands from inside your application, what's stopping you from just invoking a shell inside the program, with system() or its equivalent? Or, if you don't need the features of a shell, execve()?

---

### Post by IAMTubby on 2012-10-02
> **Bachstelze said:**
> Short answer: no.

1) You can't run an object file, you probably meant "executable".

Bachstelze, I had understood the difference between object file and executable(In an object file, linking is still not done) a few days back, thanks to you. But now I have a doubt again.

When I say
```

$gcc -o test test.c

```,
the **test** which I get after executing this command is a ** ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.9, dynamically linked (uses shared libs), not stripped**right ?(Used the file commands's output there)

But why then do we say gcc **-o** test test.c at the time of making the executable ? **Doesn't -o stand for object file ?**

Thanks.

---

### Post by spjackson on 2012-10-03
> **IAMTubby said:**
> 
When I say
```

$gcc -o test test.c

```,
the **test** which I get after executing this command is a ** ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.9, dynamically linked (uses shared libs), not stripped**right ?(Used the file commands's output there)

But why then do we say gcc **-o** test test.c at the time of making the executable ? **Doesn't -o stand for object file ?**

No. man gcc:
> 
       -o file
           Place output in file file.  This applies regardless to whatever
           sort of output is being produced, whether it be an executable file,
           an object file, an assembler file or preprocessed C code.

This option tells gcc where to put its output, not what sort of output to produce.
> 

       -c  Compile or assemble the source files, but do not link.  The linking
           stage simply is not done.  The ultimate output is in the form of an
           object file for each source file.

By default, gcc will try to link, i.e. produce an executable as output. -c tells it to stop at the generation of an object file. There are other flags that tell it to stop at other phases too. man gcc is a good place to learn about these.

---

### Post by IAMTubby on 2012-10-03
> **spjackson said:**
> No. man gcc:
This option tells gcc where to put its output, not what sort of output to produce.
Thanks spjackson, sorry I mistook output for object file.
I have 1 more question.
To run executables, why is that for cd/ls etc, we just say
```

$ls

```
But for an executable that I have created, you say
```

$./Name_Of_Executable

```

The only reason that came to my mind is that ls executable exists in /bin which is part of the PATH. But the PATH concept only lets you run the executable from whichever location you are, does not affect how it is run, right?

Basically, my question is, why not
```

#./ls

```

when we run ```
./Name_Of_My_Executable
``` and both are executables ?

Thanks.

---

### Post by spjackson on 2012-10-03
You have partially answered this question yourself.

When you give the shell the name of a command, it needs to know where to find that program. If it didn't know, where should it look? On the whole filesytem? Including any network mounts? You'd be waiting all day to get any work done.

If you don't specify an absolute or relative file path in your command, then the shell uses the PATH environment variable to determine where to look for it. That's how "ls" is found.

For your own programs that cannot be found on PATH (well they could be on PATH if they are in ~/bin or if you customise PATH), then you need to specify where the program can be found by giving an absolute or relative path to the program.

Your current directory is not part of PATH. You can add it to PATH, but this is regarded as bad practice and a security risk.

During development, when you are compiling and running a program, you typically do this in a single directory and the shortest and simplest way to tell the shell to find the program in the current directory is to use a relative path:
./Name_Of_Executable

It doesn't have to be that way. You could type /home/myuser/path_to_program/Name_Of_Executable but during development that might get a little tedious.

Perhaps during development you might have a subdirectory "test" for testing. Then you might do
```

cd test
../Name_Of_Executable

```
This is a slightly different relative path than ./Name_Of_Executable

You might do:
```

cd ~/Documents
~/path_to_program/Name_Of_Executable

```

Or if you have finished your development, put the program in ~/bin and do
```

cd ~/Documents
Name_Of_Executable

```

Or you could create an alias which has the full path to the program.

In short, if the program does not lie on PATH, then you need to tell the shell where to find it. If it does lie on PATH then you don't.

---

### Post by IAMTubby on 2012-10-03
> **spjackson said:**
> the shortest and simplest way to tell the shell to find the program in the current directory is to use a relative path:
./Name_Of_Executable

Thanks a lot spjackson, never realized that the **./** is for telling the shell to look in the current directory. I though ./ is some syntax related to executing an executable. Quite dumb of me!

But, just for the last word, why doesn't the shell take the current directory also as one of the default paths/ append this **temporarily** to PATH, at the time of executing an executable.

Thanks.
PS : The number of beans you have is evil, get rid of it immediately :D kidding!

---

### Post by spjackson on 2012-10-03
> **IAMTubby said:**
> But, just for the last word, why doesn't the shell take the current directory also as one of the default paths/ append this **temporarily** to PATH, at the time of executing an executable.

You can do
```

PATH=.:$PATH
or
PATH=$PATH:.

```
However, this is considered bad practice and a security risk. If the shell did it without you even asking it to, this would be even worse.

If dot is prepended to the PATH and you cd to a directory that has an executable file called ls, and type the ls command, then it would run whatever happens to be in that directory. You might have gone to someone else's directory and they have a command called "ls" that just so happens to remove all your files. And even if it is harmless, you probably want the real ls every time you type ls.

If dot is appended to the PATH, then there is much less risk, because the real ls is found first. But suppose you mistype it as lss. That command isn't found in the standard path, but lo and behold there just happens to be an executable program called lss in your current directory. You really don't want that running by mistake, because again it might remove all your files or something like that.

You might be the only user on your computer and therefore trust all the programs you have. In that case you might decide to append dot to your PATH. It's better for you to take that decision than for the shell to do it without you asking. However, even if you are the only user, it is still a bad habit and one of these days it just might bite you.

> 
PS : The number of beans you have is evil, get rid of it immediately :D kidding!
Well spotted. I have one more now, phew!

---

### Post by IAMTubby on 2012-10-03
> **spjackson said:**
> You might have gone to someone else's directory and they have a command called "ls" that just so happens to remove all your files.
:) I understand now.

So, suppose I add **.** to the PATH, and I have an executable called ls in my current directory, then the choice of ls which would get executed would depend on whether . comes before or after /bin in PATH. correct ?

---

### Post by spjackson on 2012-10-03
> **IAMTubby said:**
> :) I understand now.

So, suppose I add **.** to the PATH, and I have an executable called ls in my current directory, then the choice of ls which would get executed would depend on whether . comes before or after /bin in PATH. correct ?
Yes, exactly.

---

