---
title: "running [b]source script.sh[/b] inside a C code"
date: 2013-01-23
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-23
Hello,

I understand that to run a shell-related command like **history** inside a shell script you should do either **source script.sh** or **. ./script.sh**, because otherwise it gives the history of the shell forked by the shell script, which is basically blank. 
But I would like to know how I can run this nside a **C** program. Normally I do **system("./script.sh")**. In this case I tried doing **system("source script.sh")** and **system(". ./script.sh")**. But neither of those seem to work. Please find below all the necessary files.
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

PS:
I have asked this question as a subtopic on another thread([http://ubuntuforums.org/showthread.php?t=2107346](http://ubuntuforums.org/showthread.php?t=2107346)). Sorry for posting again, but I wanted to bring it to a wider audience. Please delete the thread if this is not acceptable. I also thank **Cheesemill and papibe** from the other thread for telling me about **source script.sh** and **. ./script.sh**

---

### Post by dwhitney67 on 2013-01-23
The system() command launches a new shell.  Thus what you are attempting to do will not affect the current shell in which the C program is running.

Instead of showing us how you are trying to accomplish something, perhaps you could instead focus your efforts in telling us exactly what you want accomplished.

If it environment settings that you are attempting to adjust, then perhaps you could use setenv().

---

### Post by IAMTubby on 2013-01-23
> **dwhitney67 said:**
> 
Instead of showing us how you are trying to accomplish something, perhaps you could instead focus your efforts in telling us exactly what you want accomplished.
Absolutely sir,
I want to write something which,
**"There are 3 users(A,B,C). They access 3 systems(10.94.164.a,10.94.164.b,10.94.164.c) by ssh'ing into it as ssh A@10.94.164.a. I want to know which user has ssh'ed into which system. This is so that multiple people don't try and login into the same system"**

So I thought the best way is to run a daemon on each user's shell which captures which system he has ssh'éd into by going through his history , and write to a shared database. Later when a person tries to login, the daemon reads from the shared database and gives a prompt saying that A is using 10.94.164.a, B is using ... and so C may proceed with system C and so on.

---

### Post by dwhitney67 on 2013-01-23
I think there is a way to limit how many users may SSH into a system, providing of course that all users are within the same group.

Take a look at /etc/security/limits.conf, and experiment with adding an entry similar to the following:
```

@groupname    hard    maxlogins    1

```
Of course, replace 'groupname' with the name of the group your user's share (e.g. students, staff, users).

---

### Post by ofnuts on 2013-01-23
> **IAMTubby said:**
> Absolutely sir,
I want to write something which,
**"There are 3 users(A,B,C). They access 3 systems(10.94.164.a,10.94.164.b,10.94.164.c) by ssh'ing into it as ssh A@10.94.164.a. I want to know which user has ssh'ed into which system. This is so that multiple people don't try and login into the same system"**

So I thought the best way is to run a daemon on each user's shell which captures which system he has ssh'éd into by going through his history , and write to a shared database. Later when a person tries to login, the daemon reads from the shared database and gives a prompt saying that A is using 10.94.164.a, B is using ... and so C may proceed with system C and so on.

Why don't you fopen() the .bash_history file and read the contents?

IMHO you are on shaky ground... if I were to routinely ssh to some system I would have defined an alias or script for that, and you wouldn't see "ssh" anywhere in my history. IMHO a better approach would be to hijack the ssh command and replace it by a script that signals somewhere that it is being started by $USER and then calls the real SSH.  For the same price you'll also get the end of session.

---

### Post by IAMTubby on 2013-01-27
> **dwhitney67 said:**
> I think there is a way to limit how many users may SSH into a system, providing of course that all users are within the same group.

Take a look at /etc/security/limits.conf, and experiment with adding an entry similar to the following:

Thanks for that dwhitney :) and sorry for the late response.
This time, however I'll carry on with calling ssh as a system command. Shall keep in mind about the conf file next time.

---

### Post by IAMTubby on 2013-01-27
> **ofnuts said:**
> Why don't you fopen() the .bash_history file and read the contents?

Somehow I don't get the correct history in ~/.bash_history.
As in, I type a few commands on the terminal, go and open the ~/.bash_history file. I can't see any of the commands I typed. Am i missing out on something. Like, do we have to update the ~/.bash_history file or something ?

> 
IMHO a better approach would be to hijack the ssh command and replace it by a script that signals somewhere that it is being started by $USER and then calls the real SSH.  For the same price you'll also get the end of session.
Thanks for that ofnuts, proceeding with the method you suggested above :)

---

### Post by ofnuts on 2013-01-27
> **IAMTubby said:**
> Somehow I don't get the correct history in ~/.bash_history.
As in, I type a few commands on the terminal, go and open the ~/.bash_history file. I can't see any of the commands I typed. Am i missing out on something. Like, do we have to update the ~/.bash_history file or something ?


Thanks for that ofnuts, proceeding with the method you suggested above :)
It seems the bash_history file is updated when the bash session ends (so if you run several bash sessions in parallel, their commands aren't interleaved in the history file bu you have all the commands from the first terminated session, followed by all commands from the 2nd session... The "history" command is likely appending the commands from the current session to the history file contents.

---

