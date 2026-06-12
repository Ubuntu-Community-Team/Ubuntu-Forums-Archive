---
title: "something about valgrind and sh command"
date: 2017-08-11
forum: New to Ubuntu
---

### Post by 243750496 on 2017-08-11
_____________________________________________________________________________________________________________________________________________________________________________

1:
sudo su
G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log $('/home/atc/Downloads/Compressed/Simplify3D-4.0.0-linux-x64-installer.run') ./ 
same as

2:
sudo su 
G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log $('/home/atc/Downloads/Compressed/Simplify3D-4.0.0-linux-x64-installer.run')

____________________________________________________________________________________________________________________________________________________________________________

will generate no log files

but

3:
sudo su
G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log $('/home/atc/Downloads/Compressed/Simplify3D-4.0.0-linux-x64-installer.run') sh

will generate the log


Q1:why after the no.3 command 
it will jump to a #
not 
root@ATC
so what happened ,and what's difference between "root@ATC" and "#",and how to slove the problem

Q2: Why 1st and 2nd command will not generate the log file???

Q3: can i use 


sudo G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log $('/home/atc/Downloads/Compressed/Simplify3D-4.0.0-linux-x64-installer.run') sudo sh
(becasue the .run file need super permisision but the command seems not type correctly )
and how to correct the command

Q4: what's the useage of G_SLICE=always-malloc G_DEBUG=gc-friendly
i searched from internet but found it's ubuntu wiki use this only , so is this two prefix only use in ubuntu debugging ?
if not what's the meanning of it ,
and can i remove them???

---

### Post by vocx on 2017-08-11
You don't seem to understand how the terminal runs commands in Linux. You need to understand this before trying to run "valgrind". Then you can also look into the options of "valgrind" and see what it does.

Commands in a terminal consists of words separated by whitespace. The first word is a command, the rest of the words are the arguments passed to that command.
```

valgrind myprogram word_1 option_2

```
In this code, the program is "valgrind", and the rest are options.
```

program = valgrind
argument_1 = myprogram
argument_2 = word_1
argument_3 = option_2

```

The program being run is "valgrind". It just so happens that one of its argument must also be an executable program, in this case, "myprogram".

When you use the notation $('something'), you are performing a command expansion. Those parentheses $() will return something, and that something will be run by "valgrind". This is an incorrect way of using "valgrind". You don't want to run the return value, you want to run the command itself.
```

# this is wrong
valgrind -v --tool=memcheck $('/home/atc/myprogram')

# this is right
valgrind -v --tool=memcheck /home/atc/myprogram

```
```

program = valgrind
argument_1 = -v
argument_2 = --tool=memcheck
argument_3 = /home/atc/myprogram

```
Do you see how the arguments are separated by the spaces between the words?

Additionally, in the terminal you can define "environmental variables" that can be used by programs to modify how they run. Environmental variables are defined before the program is run.
```

one_environmental_var=nothing STRANGE_NAME=blabla valgrind -v --tool=memcheck --num-callers=40 --log-file=valgrind.log /home/atc/myprogram

```
```

variable_1 = one_environmental_var=nothing
variable_2 = STRANGE_NAME=blabla
program = valgrind
argument_1 = -v
argument_2 = --tool=memcheck
argument_3 = --num-callers=40
argument_4 = --log-file=valgrind.log
argument_5 = /home/atc/myprogram

```
The environmental variables are optional. They are like arguments to a program, that is, they change the way the "valgrind" program behaves. Exactly which variables are used should be documented in the "valgrind" documentation.

In all three of these commands you are trying to run the return value of "$(Simplify3D)". This is wrong.
```

sudo su
G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log $('/home/atc/Downloads/Compressed/Simplify3D-4.0.0-linux-x64-installer.run') ./

# the arguments
argument_5 = --log-file=valgrind.log
argument_6 = $('    ')
argument_7 = ./

```

```

sudo su 
G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log $('/home/atc/Downloads/Compressed/Simplify3D-4.0.0-linux-x64-installer.run')

# the arguments
argument_5 = --log-file=valgrind.log
argument_6 = $('    ')

```

```

sudo su
G_SLICE=always-malloc G_DEBUG=gc-friendly  valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log $('/home/atc/Downloads/Compressed/Simplify3D-4.0.0-linux-x64-installer.run') sh

# the arguments
argument_5 = --log-file=valgrind.log
argument_6 = $('    ')
argument_7 = sh

```

Exactly why one produces a log file and another doesn't produce a log file is the wrong question. You are running things wrongly, so the results should be wrong.

> **243750496 said:**
> 
Q1:why after the no.3 command 
it will jump to a #
not 
root@ATC
so what happened ,and what's difference between "root@ATC" and "#",and how to slove the problem

The difference is that the last argument is "sh". This is the command to start a new shell, so a new shell is started and waits for input, which is probably not what you want.

> 
Q2: Why 1st and 2nd command will not generate the log file???

Because the execution is all wrong.

> 
Q4: what's the useage of G_SLICE=always-malloc G_DEBUG=gc-friendly
i searched from internet but found it's ubuntu wiki use this only , so is this two prefix only use in ubuntu debugging ?
if not what's the meanning of it ,
and can i remove them???
They are environmental variables. What do they do? I don't know. The explanation of what they do should be in the "manual". Which manual? Well, I don't know either. Maybe in the "valgrind" manual, maybe in the "gdb" manual, maybe in the "malloc" manual, maybe in the Linux kernel manual, maybe in that Ubuntu wiki, etc. They should be documented somewhere.

Can you remove them? Of course you can. However, how does this affect the execution of the program? I wouldn't know. You should consult the "manual" to see exactly what they affect.

Final remarks. What are you trying to do exactly? It seems to me you are trying to install this "Simplify3D" program. Why are you running it through "valgrind"? Valgrind is a utility used to check for memory leaks in compiled C and C++ programs that you create yourself, and whose source code you have at hand. It seems that you are running "valgrind" on an executable installer. Why? Do you want to check for memory leaks in the installer? Why?

So, overall, what you are attempting to do is pretty weird. You don't know how to use the terminal, and you seem to be following some instructions, but you don't really know what you are doing. I suggest you explain your ultimate objective, so that people can have a better idea of what you are really trying to do, and suggest real solutions.

---

