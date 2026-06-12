---
title: "&quot;test&quot; command in shell"
date: 2010-02-08
forum: Programming Talk
---

### Post by piyush.neo on 2010-02-08
Plateform-Ubuntu 9.10
test is a shell built in command in /usr/bin/test..
when i am making a executable file named test in my current directory its not working but if i change its name to some thing else it works....
here is series of command
```
Piyush@piyush-machine:~$ echo 'echo hello' >test
piyush@piyush-machine:~$ cat test
echo hello
piyush@piyush-machine:~$ chmod +x test
piyush@piyush-machine:~$ ls -l test
-rwxr-xr-x 1 piyush piyush 12 2010-02-08 14:02 test
piyush@piyush-machine:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
Piyush@piyush-machine:~$ PATH=:.:$PATH #include current dir 
piyush@piyush-machine:~$ echo $PATH
:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
piyush@piyush-machine:~$ test
piyush@piyush-machine:~$ cp test nottest
piyush@piyush-machine:~$ nottest
hello
piyush@piyush-machine:~$ which test
./test

```

why test command is not executing inspite the shell is using the test of my present dir?

---

### Post by Some Penguin on 2010-02-08
'test' is an inbuilt shell command, too.

---

### Post by MadCow108 on 2010-02-08
builtins are not called from the PATH variable and have preference

its similar with time
there is an time in /usr/bin but its not called when you type time into bash
instead it calls its builtin

---

### Post by piyush.neo on 2010-02-08
how to know if a command is shell built in??
Apart from it why
> which test 
is giving output ./test ?
:confused:

---

### Post by Rany Albeg on 2010-02-08
All shells have a number of built-in commands which are executed in the shell's own process. When you enter a command, the shell checks to see if it is a built-in command, and if so it executes it. If it is not a built-in the shell forks a new process in which to execute the command.

---

### Post by MadCow108 on 2010-02-08
> **piyush.neo said:**
> how to know if a command is shell built in??
Apart from it why

is giving output ./test ?
:confused:

>type command

example:
>type test
test is a shell builtin

---

### Post by geirha on 2010-02-08
```
type -a test
``` will show you all commands, functions and aliases named test. The first one listed is the one that will be executed when you run just "test". The reason "which" is not telling you about the builtin, is because "which" is an external command. The "type" command is builtin to the shell, and you'll be best served just forgetting about which and use type instead.

The only way to run your test script is to provide the path (either relative, ./test, or absolute, ~/test). In the future just refrain from naming your script the same as a builtin. You can get a list of builtins and keywords by running "help".

EDIT: Actually, that's not entirely true. You can disable builtins with the enable command. Run "help enable" to see the syntax.

Oh, btw. You should never add . to your PATH. Just create ~/bin/ and put your scripts in there. The default .profile script will add it to PATH automatically if that dir exists. Do not that .profile is only sourced during login, so you'll have to log out and back in again after you've created the dir.

---

### Post by meastwood on 2010-02-08
You could also just source the file - do not make it executable.

```
mark@ub-desktop:~$ echo "echo hello" >test
mark@ub-desktop:~$ test
mark@ub-desktop:~$ . ./test
hello
```

---

### Post by piyush.neo on 2010-02-08
thank guys..:guitar:

---

