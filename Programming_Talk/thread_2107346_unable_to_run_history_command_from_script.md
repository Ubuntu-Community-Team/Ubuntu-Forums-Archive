---
title: "unable to run history command from script"
date: 2013-01-21
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-21
Hello,
I tried using this script to find history.
```

#!/bin/bash
history

``` 
I then did
```

chmod +x script.sh
./script.sh

```
But I do not get any output on the terminal. I also tried printing to a file and then reading, but still doesn't work and shows a blank file.

Thanks.

---

### Post by papibe on 2013-01-21
Hi IAMTubby.

Try running it so that is executed by the current bash interpreter, instead of a new one:
```
. ./script.sh
```
or
```
source ./script.sh
```
Let us know how it goes.
Regards.

---

### Post by Cheesemill on 2013-01-21
Or just access the .bash_history file directly instead of with the history command...
```
#!/bin/sh
cat ~/.bash_history
```

---

### Post by IAMTubby on 2013-01-21
wow sir :) both of them worked.

> **papibe said:**
> 
Try running it so that is executed by the current bash interpreter, instead of a new one:
```
. ./script.sh
```

what does **. ./script.sh** mean ?

> 
```
source ./script.sh
```

google says that the function of the keyword source is to "Evaluate a file or resource as a Tcl script". I didn't get that, does it mean to update the script or something ?

Thanks a lot Sir.

---

### Post by IAMTubby on 2013-01-21
> **Cheesemill said:**
> Or just access the .bash_history file directly instead of with the history command...
```
#!/bin/sh
cat ~/.bash_history
```
Thanks a lot Sir, that worked as well :)
But I want to add some extra parameters like date, so I'm doing **HISTTIMEFORMAT="%d/%m/%y %T "** and then running the history command.

Thanks.

---

### Post by papibe on 2013-01-21
> **IAMTubby said:**
> what does **. ./script.sh** mean ?

Both, "dot space dot slash.." and "source" do the same thing.

Let me explain it.

A regular terminal is always running a bash instance (or interpreter) that reads your commands and execute them.

When you normally execute a shell script, another instance of bash is created exclusively for executing the content of the script. For instance, executing a script that starts with a:
```
#!/bin/bash
```
Would be almost the same as doing:
```
bash ./script.sh
```
If you see it like that, it is very easy to understand that another bash instance is created every time you called a script.

Now, when you use the above syntax no other instance is created, and so every command in the script is executed by the same interactive bash shell that is running in the terminal. It would be just like you were entering the commands yourself on the command line.

Does that help?
Regards.

---

### Post by tgalati4 on 2013-01-21
Every time you run a script with #!/bin/bash it has no history so you got no result.  So you have to run your script in your current bash environment that has a history--and that is accomplished with the *source* or . command.

---

### Post by IAMTubby on 2013-01-22
> **papibe said:**
> 
Does that help?

Thanks a lot Sir, yes, the explanation was very clear.

---

### Post by IAMTubby on 2013-01-22
> **tgalati4 said:**
> Every time you run a script with #!/bin/bash it has no history so you got no result.  So you have to run your script in your current bash environment that has a history--and that is accomplished with the *source* or . command.
Thanks a lot Sir.

---

### Post by IAMTubby on 2013-01-22
> **papibe said:**
> Does that help?
Regards.
> **tgalati4 said:**
> Every time you run a script with #!/bin/bash it has no history so you got no result.  So you have to run your script in your current bash environment that has a history--and that is accomplished with the *source* or . command.

Sir, but my requirement is to run this script from a c program.

**my c code**
```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
 system("chmod +x script.sh");
 system("source ./script.sh");

 return 0;
}

```

**my shell script**
```

#!/bin/bash
HISTTIMEFORMAT="%d/%m/%y %T "
history

```


**output**
```

$ ./a.out 
sh: source: not found

```

Basically, whenever this line ** system("source ./script.sh");** contains the word source, it's unable to give output. system("./script.sh"); works fine if the script.sh contains a command which does not need to run on it's shell, like say, ls.

Please advise.

---

### Post by IAMTubby on 2013-01-22
> **Cheesemill said:**
> Or just access the .bash_history file directly instead of with the history command...
```
#!/bin/sh
cat ~/.bash_history
```
Cheesemill, I was trying to do this, but I don't think this is the correct history. I entered far more commands that those shown in ~/.bash_history.

The history command gives me the correct output, but it comes with the added strain of having to execute it as either **. ./script.sh** or **source ./script.sh**, both of which I'm not able to do through a C program using system("source ./script.sh"); or system(". ./script.sh");

Please advise.

---

### Post by spjackson on 2013-01-23
I'm not sufficiently *au fait* with some bash intricacies to be able to tell you the right answer, but I can explain the error you are getting and provide some pointers which may or may not be helpful.

As you can see from your output, system() calls /bin/sh not bash. If you run your script, that's OK because your shebang sees to it that it is intrepreted by /bin/bash.

If you source it, then you are having it interpreted by /bin/sh not /bin/bash.

"source" is not a sh command, only the "." form can be used.

The solutions you have found so far involve source into your current bash. As soon as you call your C program, you have a new process, a child of your current bash but separate from it. You then call system which starts a child /bin/sh process, and from there you might start a bash process. However, there's no way from there to poke commands back into your top level bash.

If what you want to do is use the history command to show and format the content of ~/.bash_history, this may be achievable, but I don't know the details. If you want it to show history from your top-level bash that hasn't yet been written to ~/.bash_history, then you are snookered from the moment the C program is invoked.

---

### Post by IAMTubby on 2013-01-23
> **spjackson said:**
> 
If what you want to do is use the history command to show and format the content of ~/.bash_history, this may be achievable.
spjackson, thanks for the clear explanation.
My only requirement is to have something through which I can save the output of "history" command into a text file regularly, and see if a particular command has been entered by the user.

ie,
```

$pwd
$cd 
$clear
$ssh root@10.94.164.115 - **whenever the user enters the ssh command, I want to record the timestamp and ip**

```

So i thought of writing a daemon, which keeps looking at the output of history for "ssh" once the daemon has been triggered.

How do I do the **see if "ssh" is typed by user** part ?

Please advise.
Thanks.

---

### Post by spjackson on 2013-01-23
Is this for your own user for your own purposes, or is it for some sort of audit purpose?

If you want auditing, then you get some by default on the target machine in /var/logs. I think this will give you the originating IP but not user. If you want to capture outgoing ssh on the originating machine, then I'd have a look to see whether this can be turned on via /etc/ssh/ssh_config or something like that. History won't help because a) a user might run a script that runs ssh, b) a user might turn off history or use a shell that doesn't provide it.

If it's just for you, then a script that logs and wraps the ssh call is probably your best bet.

---

### Post by IAMTubby on 2013-01-23
> **spjackson said:**
> 
If it's just for you,
yes spjackson, it's for me. 

> 
 a script that logs and wraps the ssh call is probably your best bet.

please can you explain ? I would like to do exactly this, but how do I do this without using the history command. That's the only thing that can tell me which commands were entered by me, right ?

---

### Post by spjackson on 2013-01-23
I mean, create a script called myssh
```

#!/bin/bash

echo TODO logging here
ssh "$*"
echo TODO more logging if required

```
Then type:
```

myssh root@10.94.164.115

```

You could even call your script ssh if its location is higher up the path than the system one, but then you would need to put the full path in the script to avoid recursive calls to the script!

---

### Post by Cheesemill on 2013-01-23
You don't need to set the HISTTIMEFORMAT variable every time you run the history command, it only has to be done once when the shell is first started. The easiest way to do this is just to add the following to your ~/.bashrc
```
export HISTTIMEFORMAT="%d/%m/%y %T "
```

Then to see what times you used the ssh command you can simply type...
```
history | grep " ssh "
```

---

### Post by IAMTubby on 2013-01-23
> **spjackson said:**
> I mean, create a script called myssh
```

#!/bin/bash

echo TODO logging here
ssh "$*"
echo TODO more logging if required

```
Then type:
```

myssh root@10.94.164.115

```

You could even call your script ssh if its location is higher up the path than the system one, but then you would need to put the full path in the script to avoid recursive calls to the script!
spjackson , wow :D
I completely get what you said.

Solution1:
Make a script which does the processing part and then calls the original ssh executable. I can even take the ip to ssh into and give that as argument to the original ssh call. I'll google that up.

Solution2:
Do the same as above, but call this script as ssh itself. And make sure **my executable** gets executed by placing it higher in the PATH. Got this to work. Thanks a lot spjackson.
```

$ ssh root@10.94.164.115
ha ha . tricked you :)

```

I placed my ssh executable in /usr/sbin, the original ssh was in /usr/bin. Just deleting it.

---

### Post by Bachstelze on 2013-01-24
Just for kicks, why is it that running "history" from a shell script doesn't work but this does ?

```
firas@ichiyoh ~ % bash
[firas@ichiyoh ~]$ echo foo
foo
[firas@ichiyoh ~]$ exit
firas@ichiyoh ~ % bash
[firas@ichiyoh ~]$ history
    1  echo foo
    2  history
[firas@ichiyoh ~]$ 

```

The second bash is "new", why does it have the history of the first, but a bash run form a script doesn't?

(I don't know the answer either, by the way.)

---

### Post by steeldriver on 2013-01-24
maybe the decider is whether it is considered an interactive or non-interactive shell?

> **6.3.3 Interactive Shell Behavior**

  When the shell is running interactively, it changes its behavior in several ways. 
 
[LIST=1]
[*] Startup files are read and executed as described in [Bash Startup Files]("http://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html#Bash-Startup-Files").
[*] Job Control (see [Job Control]("http://www.gnu.org/software/bash/manual/html_node/Job-Control.html#Job-Control")) is enabled by default.  When job control is in effect, Bash ignores the keyboard-generated job control signals SIGTTIN, SIGTTOU, and SIGTSTP.
[*] Bash expands and displays PS1 before reading the first line of a command, and expands and displays PS2 before reading the second and subsequent lines of a multi-line command.
[*] Bash executes the value of the PROMPT_COMMAND variable as a command before printing the primary prompt, $PS1 (see [Bash Variables]("http://www.gnu.org/software/bash/manual/html_node/Bash-Variables.html#Bash-Variables")).
[*] Readline (see [Command Line Editing]("http://www.gnu.org/software/bash/manual/html_node/Command-Line-Editing.html#Command-Line-Editing")) is used to read commands from the user’s terminal.
[*] Bash inspects the value of the ignoreeof option to set -o instead of exiting immediately when it receives an EOF on its standard input when reading a command (see [The Set Builtin]("http://www.gnu.org/software/bash/manual/html_node/The-Set-Builtin.html#The-Set-Builtin")).
[*] **Command history (see [Bash History Facilities]("http://www.gnu.org/software/bash/manual/html_node/Bash-History-Facilities.html#Bash-History-Facilities")) and history expansion (see [History Interaction]("http://www.gnu.org/software/bash/manual/html_node/History-Interaction.html#History-Interaction")) are enabled by default. Bash will save the command history to the file named by $HISTFILE when an interactive shell exits.  **
[*] Alias expansion (see [Aliases]("http://www.gnu.org/software/bash/manual/html_node/Aliases.html#Aliases")) is performed by default.
[*] In the absence of any traps, Bash ignores SIGTERM (see [Signals]("http://www.gnu.org/software/bash/manual/html_node/Signals.html#Signals")).
[*] In the absence of any traps, SIGINT is caught and handled ((see [Signals]("http://www.gnu.org/software/bash/manual/html_node/Signals.html#Signals")). SIGINT will interrupt some shell builtins.
[*] An interactive login shell sends a SIGHUP to all jobs on exit if the huponexit shell option has been enabled (see [Signals]("http://www.gnu.org/software/bash/manual/html_node/Signals.html#Signals")).
[*] The -n invocation option is ignored, and ‘set -n’ has no effect (see [The Set Builtin]("http://www.gnu.org/software/bash/manual/html_node/The-Set-Builtin.html#The-Set-Builtin")).
[*] Bash will check for mail periodically, depending on the values of the MAIL, MAILPATH, and MAILCHECK shell variables (see [Bash Variables]("http://www.gnu.org/software/bash/manual/html_node/Bash-Variables.html#Bash-Variables")).
[*] Expansion errors due to references to unbound shell variables after ‘set -u’ has been enabled will not cause the shell to exit (see [The Set Builtin]("http://www.gnu.org/software/bash/manual/html_node/The-Set-Builtin.html#The-Set-Builtin")).
[*] The shell will not exit on expansion errors caused by var being unset or null in ${var:?word} expansions (see [Shell Parameter Expansion]("http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html#Shell-Parameter-Expansion")).
[*] Redirection errors encountered by shell builtins will not cause the shell to exit.
[*] When running in POSIX mode, a special builtin returning an error status will not cause the shell to exit (see [Bash POSIX Mode]("http://www.gnu.org/software/bash/manual/html_node/Bash-POSIX-Mode.html#Bash-POSIX-Mode")).
[*] A failed exec will not cause the shell to exit (see [Bourne Shell Builtins]("http://www.gnu.org/software/bash/manual/html_node/Bourne-Shell-Builtins.html#Bourne-Shell-Builtins")).
[*] Parser syntax errors will not cause the shell to exit.
[*] Simple spelling correction for directory arguments to the cd builtin is enabled by default (see the description of the cdspell option to the shopt builtin in [The Shopt Builtin]("http://www.gnu.org/software/bash/manual/html_node/The-Shopt-Builtin.html#The-Shopt-Builtin")).
[*] The shell will check the value of the TMOUT variable and exit if a command is not read within the specified number of seconds after printing $PS1 (see [Bash Variables]("http://www.gnu.org/software/bash/manual/html_node/Bash-Variables.html#Bash-Variables")).
[/LIST]
[http://www.gnu.org/software/bash/manual/html_node/Interactive-Shell-Behavior.html](http://www.gnu.org/software/bash/manual/html_node/Interactive-Shell-Behavior.html)

---

### Post by Bachstelze on 2013-01-24
Indeed, not sure how I could have missed that... Then, since the history is not read automatically, one way to achieve the desired result is to force it. This will work:

```
#!/bin/bash

history -r ~/.bash_history
history

```

---

### Post by IAMTubby on 2013-01-26
> **Cheesemill said:**
> You don't need to set the HISTTIMEFORMAT variable every time you run the history command, it only has to be done once when the shell is first started. The easiest way to do this is just to add the following to your ~/.bashrc
```
export HISTTIMEFORMAT="%d/%m/%y %T "
```

Then to see what times you used the ssh command you can simply type...
```
history | grep " ssh "
```
thanks a lot Sir, shall remember that.

---

### Post by IAMTubby on 2013-01-26
> **Bachstelze said:**
> Indeed, not sure how I could have missed that... Then, since the history is not read automatically, one way to achieve the desired result is to force it. This will work:

```
#!/bin/bash

history -r ~/.bash_history
history

```
Bachstelze, works, very useful.
thanks a lot :)

---

### Post by IAMTubby on 2013-01-26
> **papibe said:**
> When you normally execute a shell script, another instance of bash is created exclusively for executing the content of the script
> **tgalati4 said:**
> Every time you run a script with #!/bin/bash it has no history so you got no result.

Sir, but I have one question.
When I run
```

#!/bin/bash
ps -p $$

```

Output
```

$ ps -p $$
  PID TTY          TIME CMD
 8860 pts/0    00:00:00 bash
```
in a script. Why does it give the same o/p as the PID of the shell where it is run from. I would have expected it to give the PID of the new instance of the shell that is created to run the shell script.

---

