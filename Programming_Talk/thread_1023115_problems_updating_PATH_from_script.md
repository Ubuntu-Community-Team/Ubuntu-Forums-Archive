---
title: "problems updating PATH from script"
date: 2008-12-27
forum: Programming Talk
---

### Post by monkeyking on 2008-12-27
I have problems updating my PATH from a script,
so that my PATH is updated after I've run my script.

This is a small example that shows the problem.

I'm in a subdir of my home called bins.
I've created a small executable script call prog that looks like

[PHP]
#!/bin/bash
echo "in my prog"
[/PHP]
this is executable and if i type ./prog i get
[PHP]
:~/bins$ ./prog
in my prog
[/PHP]
So that works

Now If I update my path from command line like
[PHP]
PATH="~/bins:${PATH}"
export PATH
[/PHP]
I can just type prog everywhere and it works.

But I can't do it from a bashscript, I've created the following script called envs.sh, that looks like

[PHP]
if [ -z "${PATH}" ]
then
    PATH="~/bins"; export PATH
else
    echo path exists will append
    PATH="~/bins:${PATH}"; export PATH
fi
[/PHP]

When I run this I get

```
./bins/envs.sh
path exists will append

```

So the code is run but the PATH isn't being updated.
This is very puzzling.

thanks in advance

---

### Post by lensman3 on 2008-12-27
When you run a script you spawn another shell.  That new shell inherents the older shell's environment but the new shell can't change the original shells environment.  This is also known as: "You can't teach an old dog new tricks". 

Do do what you want to do you need the "source" command.  Below is the source command for bash.  I think the the sh-shell uses ". filename" to do the same thing.

From the bash man page:  (The key words are "in the current shell environment").

source filename [arguments]
              Read and execute commands from filename in the current shell environment and return the exit status of the last command executed from filename.  If filename  does  not contain a slash, file names in PATH are used to find the directory containing filename.  The file searched for in PATH need not be executable.  When bash is not in posix mode, the current directory is searched if no file is found in PATH.  If the  sourcepath  option  to  the  shopt  builtin command is turned off, the PATH is not searched.  If any arguments are supplied, they become the positional parameters when filename is executed.  Otherwise the positional parameters are unchanged.  The return status is the status of the last command exited within the  script  (if no commands are executed), and false if filename is not found or cannot be read.

---

### Post by Cracauer on 2008-12-28
Use 

`. myscript.sh`

instead of

`sh myscript.sh` or `./myscript.sh`

What you are trying to do there looks like you should slam it into your dotfiles anyway.

---

### Post by monkeyking on 2008-12-29
Thanks source og the dot space filename command will update the path.

But my problem is somewhat more awkward.

from the promt I call a script call choosepath.sh

And from the argument I give to choosepath.sh this script
will choose another script to use for updating the paths.

choosepath.sh
[PHP]
#!/bin/bash
case "$1" in
  ia32)
      if [ -e /bins/iccvars_ia32.sh ]; then
         . /bins/iccvars_ia32.sh 
      fi
      ;;
  intel64)
      if [ -e /bins/intel64/iccvars_intel64.sh ]; then
         . /bins/intel64/iccvars_intel64.sh 
      fi
      ;;
esac
[/PHP]

if I source iccvars_is32.sh or iccvars_intel64 it works,
but not If I choose which one, from another script.

thanks again

---

### Post by Cracauer on 2008-12-29
OK, 3 solutions, your pick:

1) Of course the whole chain of scripts right to the front, your interactive shell, has to be "." called.

2) You should seriously think about making all these things functions in your shell dotfile instead of standalone scripts. That's what I do to switch between different /usr/local, /opt/cvsversions etc trees.

3) An alternative is to do what we do around ssh-agent, which is
```

echo PATH=blah:fasel:blubb

```
in the script

and then
```

eval `myscript`

```

In your interactive shell.

But then you have to keep stdout printing absolutely clean.

---

