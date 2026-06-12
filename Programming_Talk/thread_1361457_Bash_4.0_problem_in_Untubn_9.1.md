---
title: "Bash 4.0 problem in Untubn 9.1"
date: 2009-12-22
forum: Programming Talk
---

### Post by flyingwave on 2009-12-22
Hi, I was hit by a Bash 4.0 problem when upgrading to Ubuntu 9.1. When I ran the script below, Bash 4.0 reported that .gen_funcs can't be found and the following funcitons defined in this file. Seems Bash 4.0 has different option setting with Bash 3.2.48 in Ubuntu 9.04. (the system defualt shell has already been changed to from dash to bash.)
 
I tried to add set +o posix and set -s dotglob here, then it works. However, this way is not a good solution, because there are many other script files which need to work. Then I added a ENV setting in .bashrc: export ENV=/home/song/tmp. But it only works in the bash terminal (can display with set -o and shopt). It doesn't work for script like ./setup.sh.
 
Is there any other way to control the the execution for srcipts (/bin/sh)? Thanks for your help.
 
//tmp file
set +o posix
shopt -s dotglob
 
// script in setup.sh
#!/bin/sh
// bin/sh are symbol link to /bin/bash
//When adding set +o posix and set -s dotglob here, then it works.
 
if [ -e ./.config ]; then
. ./.config
else
. .gen_funcs
fi
......// the functions are defined in .gen_funcs
tools_setup "$1"
env_setup
 
 
// bash 4.0.33 in Ubuntu9.1
song@ubuntu: ~$ bash --version
GNU bash, version 4.0.33(1)-release (i486-pc-linux-gnu)
 
//bash 3.2.48 in Ubuntu9.04
song@song-Ubuntu: ~$ sh --version
GNU bash, version 3.2.48(1)-release (i486-pc-linux-gnu)

---

### Post by Arndt on 2009-12-22
> **flyingwave said:**
> Hi, I was hit by a Bash 4.0 problem when upgrading to Untubn 9.1. When I ran the script below, Bash 4.0 reported that .gen_funcs can't be found and the following funcitons defined in this file. Seems Bash 4.0 has different option setting with Bash 3.2.48 in Untubn 9.04. (the system defualt shell has already been changed to from dash to bash.)

I tried to add set +o posix and set -s dotglob here, then it works. However, this way is not a good solution, because there are many other script files which need to work. Then I added a ENV setting in .bashrc: export ENV=/home/song/tmp. But it only works in the bash terminal (can display with set -o and shopt). It doesn't work for script like ./setup.sh.

Is there any other way to control the the execution for srcipts (/bin/sh)? Thanks for your help.

//tmp file
set +o posix
shopt -s dotglob

// script in setup.sh
#!/bin/sh
// bin/sh are symbol link to /bin/bash
//When adding set +o posix and set -s dotglob here, then it works.

if [ -e ./.config ]; then
. ./.config
else
. .gen_funcs
fi
......// the functions are defined in .gen_funcs
tools_setup "$1"
env_setup


// bash 4.0.33 in Untubn 9.1
song@ubuntu: ~$ bash --version
GNU bash, version 4.0.33(1)-release (i486-pc-linux-gnu)

//bash 3.2.48 in Untunbn 9.04
song@song-Ubuntu: ~$ sh --version
GNU bash, version 3.2.48(1)-release (i486-pc-linux-gnu)

I'm not sure what it is that doesn't work for you. I can use '.' to include a file beginning with a period, without changing any options. Globbing shouldn't have to do with this - you're specifying an explicit filename.

I also have Ubuntu 9.10 (as you do, it's not called Untubn 9.1).

Can you show a really small file that behaves differently in 9.04 and 9.10?

---

### Post by geirha on 2009-12-22
When you invoke bash as /bin/sh, it starts in posix compatible mode, which disables some, but not all, features of bash. If it is a bash-script, use #!/bin/bash as the she-bang. If it's a posix script, use #!/bin/sh.

The posix dot command is defined as follows: ([http://www.opengroup.org/onlinepubs/7990989775/xcu/chap2.html](http://www.opengroup.org/onlinepubs/7990989775/xcu/chap2.html))
```

 dot - Execute Commands in Current Environment
 SYNOPSIS



. file
 DESCRIPTION
The shell will execute commands from the file in the current environment.

If file does not contain a slash, the shell will use the search path specified by 
PATH to find the directory containing file. Unlike normal command search, however, 
the file searched for by the dot utility need not be executable. If no readable 
file is found, a non-interactive shell will abort; an interactive shell will write 
a diagnostic message to standard error, but this condition will not be considered 
a syntax error. 

```

In other words, ```
. .gen_funcs
``` will search for .gen_funcs in PATH, not in the current directory. If you provide the path though, ```
. ./.gen_funcs
``` it will find it and source it. 

Bash in non-posix mode will look for the file in the current directory in addition to PATH.

---

### Post by flyingwave on 2009-12-22
Hi Arndt & Geirha,
 
Thanks for your input. 
 
Hi Arndt, You're right that the option dotglob do nothing with my problem.
 
Here I attached two small sample script files including setup.sh and .gen_func. You could try in your system. Please note that these two files should be in the same directory.
 
Hi Geirha, You are correct too. If I changed the start line to #!/bin/bash, then the posix option was closed. So this way works indeed.
 
However, the fact is, I'm compiling a big embeded project in which contains many scripts. All these scripts start with #!/bin/sh. It's not good way to change all of them. Do you know if there any good solution?
 
BTW, I'm still wondering the difference between #!/bin/bash and #!/bin/sh. You know, I have changed /bin/sh with 'ln -sf /bin/bash /bin/sh'. So by my understanding, they should have the same behavior. Could you please give me some point? Thanks a lot.
 
Maybe you should pay attenation to the difference between in Ubuntu 9.10 and 9.04. As you can see in the screen shots, the difference is obvious. For Ubuntu 9.04, both #!/bin/bash and #!/bin/sh can work normally. But in 9.10, only the latter works. (Please ingnore the warning in red in the screen shots, becasue they are caused by the other part of the script.) 
 
Regards,
Henry

---

### Post by v8YKxgHe on 2009-12-22
It is '**Ubuntu**' not 'Untubn'. Sorry, I just had to - it was annoying me.

---

### Post by geirha on 2009-12-23
Well, if all the scripts are sourcing .gen_funcs like that, they are all bugged and should be fixed. The proper way would of course be to adhere to the posix standard, which means you'll have to manually fix every one of them. You could possibly save some time by doing a search and replace on all files in question, but you still have to check every file manually to ensure that you didn't break anything.

There is a way to hack around it, but it's not the best solution. You can add the directory containing .gen_funcs to the PATH and export PATH so all scripts started from your interactive one will inherit it.

---

### Post by flyingwave on 2009-12-23
Forgive me for the typo error. I could understand your feeling and would like to pay attention to this.
 
For the way by adding the file folder to PATH env, I don't think it's good also, becuase usually different script has differnet sub-script call and they are in different folders.
 
I'm still wondering why the behavior for #!/bin/bash and #!/bin/sh are different. Could you please tell me something about it? Thanks.
 
And how to explain the version difference between 9.10 & 9.04? Anything wrong in bash 4.0.33 or somthing else like libncurse etc. wrong? I'll do some tests when I have more free time. But would you please give me some hint about the direction.

---

### Post by geirha on 2009-12-23
It's in the man-page:
```

       If bash is invoked with the name sh, it  tries  to  mimic  the  startup
       behavior  of  historical  versions  of sh as closely as possible, while
       conforming to the POSIX standard as well.  When invoked as an  interac&#8208;
       tive  login  shell, or a non-interactive shell with the --login option,
       it first attempts to read and execute commands  from  /etc/profile  and
       ~/.profile,  in  that  order.   The  --noprofile  option may be used to
       inhibit this behavior.  When invoked as an interactive shell  with  the
       name  sh,  bash  looks for the variable ENV, expands its value if it is
       defined, and uses the expanded value as the name of a file to read  and
       execute.  Since a shell invoked as sh does not attempt to read and exe&#8208;
       cute commands from any other startup files, the --rcfile option has  no
       effect.   A  non-interactive  shell  invoked  with the name sh does not
       attempt to read any other startup files.   When  invoked  as  sh,  bash
       enters posix mode after the startup files are read.

```

Just search for posix mode and read on.

As for changes between 3.2.x and 4.0.x, check the changelog [http://tiswww.case.edu/php/chet/bash/CHANGES](http://tiswww.case.edu/php/chet/bash/CHANGES). I don't know what difference you are talking about though.

---

