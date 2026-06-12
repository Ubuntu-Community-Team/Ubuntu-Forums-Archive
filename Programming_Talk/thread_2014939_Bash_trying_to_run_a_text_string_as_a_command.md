---
title: "Bash: trying to run a text string as a command"
date: 2012-07-02
forum: Programming Talk
---

### Post by mringer on 2012-07-02
I am trying to write a Bash function that will assemble a text string & then run it as a command. Here is a sample:

```

#!/bin/bash 

do_command() {                # 3
    echo -e "XX $* XX \n"     # 4
    $*                        # 5
}

do_command "ls | grep t"      # 8


```

(This works if the argument of do_command is a simple command and
not a pipeline). The output is:

```

XX ls | grep t XX 
ls: cannot access |: No such file or directory
ls: cannot access grep: No such file or directory
ls: cannot access t: No such file or directory

```

I believe that the quoted string in line 8 is correctly passed to
do_command but then the  |  is interpreted as an argument to  ls 
and not a pipe. I have tried lots of workarounds, all have failed.

Please any advice? thank you

---

### Post by sisco311 on 2012-07-02
You could use the evil command. Oh, sorry, I mean eval (BashFAQ 048 - link in my signature). :)

But, what exactly are you trying to accomplish?

---

### Post by VCoolio on 2012-07-02
> **mringer said:**
> I am trying to write a Bash function that will assemble a text string & then run it as a command. Here is a sample:

```

#!/bin/bash 

do_command() {                # 3
    echo -e "XX $* XX \n"     # 4
    $*                        # 5
}

do_command "ls | grep t"      # 8


```

(This works if the argument of do_command is a simple command and
not a pipeline). The output is:

```

XX ls | grep t XX 
ls: cannot access |: No such file or directory
ls: cannot access grep: No such file or directory
ls: cannot access t: No such file or directory

```

I believe that the quoted string in line 8 is correctly passed to
do_command but then the  |  is interpreted as an argument to  ls 
and not a pipe. I have tried lots of workarounds, all have failed.

Please any advice? thank you

If you need the output of "ls | grep t" to do stuff with, then:
```
do_command $(ls | grep t)
```
This won't work I guess if the filenames have spaces. Also you don't want ls in this case, read [this](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29). so you could do: do_command *t*
or
```
for i in *t*; do do_command "$i"; done
```
This works with filenames with spaces too, if inside the do_command function you call the argument(s) quoted, like "$@" or "$1".

---

### Post by Vaphell on 2012-07-02
OP doesn't want to pass the output to do_command, but the string to be run as a command ( $(cmd1|cmd2) vs "cmd1|cmd2" ). Just like sisco said it looks like a job for eval (do_command being its functional equivalent) and it would be good to know where this is going.

as for **ls | grep t** - why not **ls *t***
ls supports globbing and you don't have to grep it.

---

### Post by mringer on 2012-07-04
Thank you very much, all who replied. eval works, everything else I tried has failed. The script I gave in my first post was nothing like what I am actually trying to do, it was merely a minimal sample to show my problem. If you want to see what I am trying to do, see:

[http://ubuntuforums.org/showthread.php?t=2011521](http://ubuntuforums.org/showthread.php?t=2011521)

which has a lot of messy programming which I hope to clean up. (This will take a long time because there is so much material in Greg's Wiki.)

I will mark this as solved if I can find out how.

---

