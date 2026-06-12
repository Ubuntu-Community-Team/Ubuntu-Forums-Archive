---
title: "how do I invoke a bespoke extrinsic script language?"
date: 2008-03-16
forum: Programming Talk
---

### Post by ibuclaw on 2008-03-16
Hi all, I've got a program that I'd like to incorporate a scripting language into. But instead of building one from scratch, I've decided that using bash could be a hell of a lot easier (at least I hope).

But excluding the general commands to get round,  update, mount and symlink the filesystem (the bare neccesities). I don't really know much else!
But I am getting through prereqs such as "man bash"

I've come across the word "alias", describes a way of creating extrinsic commands to automate a sometimes complex intrinsic function.
For example, I could implement
```
 upvar 
```
as a command to create a link to a variable in a different stack frame.

I presume that these sorts of details are cached away somewhere in one file. But I'd rather that I'd have mine in it's own folder that can be called using a command.

ie:
```
 define? myscriptname = "#!/bin/bash {CODE TO LOAD MY ALIAS FILE}" 
```

As you see I'm a bit in the dark, but any help would be greatly appreciated.

Thanks in advance.

Iain

---

### Post by LaRoza on 2008-03-16
You can put them in .bashrc, or in a separate file

---

### Post by ibuclaw on 2008-03-16
Hey,
Thanks for the info.

It was a bit vague, but I think I've found my answer... (from reading the .bashrc file)

```
 alias myalias='echo "This is my alias" ' 
```
is how to define one?

and
```
 alias loadmyalias='. /path/to/my/alias/file' 
```
adds my list of commands into bash when I need them? (not when the session starts immediately).

Need confirmation, but if so, I can give this a start tonight.

Iain

---

### Post by slavik on 2008-03-16
stick the aliases into a file that looks similar to this:

alias a=ls
alias ls='ls -l'

then you can do something like this:

while line in readline FILE
do
 $line
done

---

### Post by ibuclaw on 2008-03-16
> **slavik said:**
> 
while line in readline FILE
do
 $line
done

Okay, I understand that, but its not the desired effect I'm looking for?
In other words, this looks more like a batch way of doing things.

But I understand the purpose of it, though as I said, this for a **program** I'm writing (Uses mainly C, mixture of other scraps). Sorry for the boldness. But I can do this in C easily, something in the likes of:
```

file = fopen(str_fpath, "r");
run_script = popen(str_xpath -x file);

```

I'm sure something is wrong with it, but I'll find out when I come to testing.

Anyway, I think it's solved.

The way I explained my previous post had the desired effect I wanted.

```

iain@fredbuntu:~$ hellomsl
bash: hellomsl: command not found
iain@fredbuntu:~$ msl_init
iain@fredbuntu:~$ hellomsl
HELLO MY SCRIPTING LANGUAGE!
iain@fredbuntu:~$

```

Brilliant!

Iain

---

### Post by ibuclaw on 2008-03-16
Hi all, sorry to bother again, but I've hit a rock.

I've only just started to implement this, and the implementations work fine!

But when I try to execute it in a script, it doesn't seem to work.

for example, here I've typed in the command in the terminal, followed by executing the command in a script.

```

iain@fredbuntu:~/$ hellomsl
bash: hellomsl: command not found
iain@fredbuntu:~/$ msl_init
iain@fredbuntu:~/$ hellomsl
HELLO MY SCRIPT LANGUAGE!
iain@fredbuntu:~/$ display "This Works..."
This Works...
iain@fredbuntu:~/$ ./test
./test: line 1: hellomsl: command not found
./test: line 2: msl_init: command not found
./test: line 3: hellomsl: command not found
display: Unable to open file (This Works...) [No such file or directory].

```
And GraphicsMagick opens too...

I've tried it on other commands such as ls; which in ubuntu shows blue for directories and green for executable files.
Through scripts, alas, this shows just grayness, as if it ignores the "~/.bashrc" file altogether.

I've even tried your way slavik, it proved very helpful in the end. along with "cat $filename"
But alas, the same problem of not reading the "~/.bashrc" file.

Before I posted this, I also tried to embed the alias.
ie:
alias hello='echo "hello" '
hello

But still not getting it.

So the million dollar question, I suppose is how do I execute scripts with alias'?

Iain

---

### Post by ibuclaw on 2008-03-16
```

shopt -s expand_aliases
cat alias_list | while read line; do $line; done

```

That was difficult to figure out.

Oh well, thank you all for your help anyway,
 I wish I knew more about shell script...

---

### Post by mssever on 2008-03-16
I'd like to open a can of worms and suggest that there are better alternatives to an embedded scripting language than Bash. Bash was made for command line use, and it's great at that. But for interacting with another program, there are several other languages which provide greater power and flexibility without all of Bash's quirks.

---

