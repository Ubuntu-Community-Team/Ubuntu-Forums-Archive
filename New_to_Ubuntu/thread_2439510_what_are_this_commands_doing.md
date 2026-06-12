---
title: "what are this commands doing ?"
date: 2020-03-28
forum: New to Ubuntu
---

### Post by janvi2 on 2020-03-28
an installation readme instructs following steps:

$ BUILD_SRC=$(pwd)
$ mkdir -p ~/tmp/build
$ cd ~/tmp/build
$ cmake ${BUILD_SRC}
$ make install
$ cd ..

First line is unknown. Is pwd a placeholder for another name ?
Then a build dir is created and changed to. 
CMAKE then generates a makefile and yes, there is a cmakelists.txt in current directory
new makefile is then executed with make install
but what is BUILD_SRC ?

---

### Post by Holger_Gehrke on 2020-03-28
'$(...)' is a command line substitution - execute the command and replace it in the command line with it's output. 'pwd' is a command to print the working directory. So "BUILD_SRC=$(pwd)" assigns the current directory as value to the variable BUILD_SRC.

Holger

---

### Post by janvi2 on 2020-03-29
understand,** BUILD_SRC** is a variable and[B]

jv@JamesWebb:~/dirname$ pwd

[/B]reports correct directory
/home/jv/dirname

Why is then consequence, [B]
$ BUILD_SRC=$(pwd)
[/B][B][B]$ BUILD_SRC
[/B][/B]or[B][B][B][B]$ {BUILD_SRC}
[/B][/B]
[/B][/B]always reports Instruction not found instead of dirname ?
Is this a diffrent thing if used as  cmake ${BUILD_SRC} instead of invoking by hand ?
Possibly $(...) is something diffrent than ${...} ?

Assume this variable is used by CMAKE as it is passed as a parameter 
there is probably more use why it is not directly invoked by cmake $(pwd)

---

### Post by Impavidus on 2020-03-29
> **janvi2 said:**
> understand,** BUILD_SRC** is a variable and[B]

jv@JamesWebb:~/dirname$ pwd

[/B]reports correct directory
/home/jv/dirname

Why is then consequence, [B]
$ BUILD_SRC=$(pwd)
[/B][B][B]$ BUILD_SRC
[/B][/B]or[B][B][B][B]$ {BUILD_SRC}
[/B][/B]
[/B][/B]always reports Instruction not found instead of dirname ?
Because the current working directory isn't a command.
**BUILD_SRC** is the name of the variable. The shell will use it literally, which will give an error, as the command BUILD_SRC doesn't exist.
**$BUILD_SRC** (note: there's no space after the $) refers to the contents of the variable. If you put it like that on the command line, the shell will replace it by the contents of the variable. If it's the first thing on the command line, it will be interpreted as a command. Which will fail, as the contents are (in this case) not a valid command.
If you want to see the contents of the variable, use **echo $BUILD_SRC**. The **echo** command prints its arguments.
**$BUILD_SRC** and **${Build_SRC}** are mostly equivalent, but there are cases when you need the {}, like when that's the only way how the shell can see where your variable name ends:```
a=foo
echo $abar
echo ${a}bar
```> 
Is this a diffrent thing if used as  cmake ${BUILD_SRC} instead of invoking by hand ?
Possibly $(...) is something diffrent than ${...} ?By hand or by variable substitution is the same, except that you cannot automate the former. $(...) is different from ${...}. $(...) will run a command and substitute the output, ${...} will take a variable and substitute the contents.

> Assume this variable is used by CMAKE as it is passed as a parameter 
there is probably more use why it is not directly invoked by cmake $(pwd)
**cmake $(pwd)** will give cmake the present working directory at the time when cmake is called, not when you set the BUILD_SRC variable. In between you changed to a different directory.

If you want to learn more about bash scripting, ask your favourite search engine for a guide. There are excellent guides freely available.

---

### Post by Holger_Gehrke on 2020-03-29
Yes, there is a difference between '$(x)', '${x}', $x and x.

'$(x)' executes x as a command and replaces $(x) in the command with the standard output of x. This could also be written as '`x`' (enclosing the command in backticks). This is the older way of writing a command substitution. It's somewhat frowned on because the new way is easier to read.

'${x}' and '$x' will get substituted with the value of the variable x. The latter variant is shorter but won't always work as expected if used to construct some kind of string; there needs to be a space or a newline after $x so the shell can recognize the end of the variable name, with ${x} that's not necessary. To check the value of a variable enter something like "echo ${BUILD_SRC}".

And if you look at the commands given in those build instructions, you can tell why they are doing it this way: they store the current working directory in BUILD_SRC and then they are changing directory. The value of BUILD_SRC keeps the **old** working directory.

```

$ BUILD_SRC=$(pwd)
$ BUILD_SRC # execute literal 'BUILD_SRC'; there's no such command ...
BUILD_SRC : command not found
$ {BUILD_SRC} # the same; in both cases there's a '$' missing; if it was there you'd get a different error
BUILD_SRC : command not found
$ ${BUILD_SRC} # actually substituting the variable value for it's name
bash:  /home/jv/dirname is a directory

but:
$ a="echo x" # assign a string that is a valid command to a variable
$ $a # the value of $a is substituted and executed
x

```

Holger

Edit: Slow typists get ninja'd. Hi, Impavidus !

---

### Post by The Cog on 2020-03-29
It is worth using "set -x" when trying these things out to see what commands are actually doing. It prints a + in front of each command it actually executes. Here's a short example. The command pwd just executes pwd and prints the working directory. When setting BUILD_SRC, it calls pwd and then places that command's output in the next command:
```
steve@StevesPC:~$ set -x
steve@StevesPC:~$ pwd
+ pwd
/home/steve
steve@StevesPC:~$ BUILD_SRC=$(pwd)
++ pwd
+ BUILD_SRC=/home/steve
```

The reason it sets BUILD_SRC is that the next thing it does is to change its working directory with a cd command. But it uses BUILD_SRC to remember where it came from, which it then tells to cmake.

---

### Post by janvi2 on 2020-03-29
Many thanks to shed some light on the lines. I have O-Reily "Linux in a Nutshell" and found the pwd command in the meantime but $ is only explained in context of regex. This way your explanations were helpfull as Google for $ also do not return any usefull results.

---

### Post by Holger_Gehrke on 2020-03-29
The use of '$' for variable or parameter substitution is a feature of the shell. In my "Linux in a Nutshell" (4th Edition, 2003) it can be found in chapters 6 (The Linux Shells) especially 6.3 (common Features) and chapter 7 (bash: The Bourne-Again Shell) specifically 7.3 (Variables).

Holger

---

