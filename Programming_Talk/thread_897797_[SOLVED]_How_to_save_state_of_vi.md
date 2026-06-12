---
title: "[SOLVED] How to save state of vi"
date: 2008-08-22
forum: Programming Talk
---

### Post by shankhs on 2008-08-22
I use vim only for programming purposes, so I want to open vim with a few include statements and ":set nu" and ":set ai". Is there any way to do so???

---

### Post by dwhitney67 on 2008-08-22
Insert those very same statements into a file called **.vimrc **in your home directory.  I also like to include the following statement so that the cursor jumps to the last place I was at when I re-open a file.
```
if has("autocmd")
  au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
    \| exe "normal g'\"" | endif
endif

```
P.S.  The statement above is commented out in /etc/vim/vimrc.  I would recommend commenting it in, thus obviating the need to include it in ~/.vimrc.

---

### Post by drubin on 2008-08-22
> **dwhitney67 said:**
> 
P.S.  The statement above is commented out in /etc/vim/vimrc.  I would recommend commenting it in, thus obviating the need to include it in ~/.vimrc.

Values in the /etc/vim/vimrc are used by ALL users on the system.  the ~/.vimrc is for personal preferences. 

Normally it would not be a good idea to just over write default values for all users on a specific system. Even if you  do not have multiple users on your system it is good practice.

---

### Post by dwhitney67 on 2008-08-22
> **rubinboy said:**
> ...
Normally it would not be a good idea to just over write default values for all users on a specific system. Even if you  do not have multiple users on your system it is good practice.
What??  If it's my personal system, I should be able to do whatever I please.

Now, if someone doesn't have a clue what they are doing, then you are probably right; the should not be doing admin work on their system without first employing some careful thought as to what they are doing, and more importantly, why they are doing it.

---

### Post by drubin on 2008-08-22
> **dwhitney67 said:**
> What??  If it's my personal system, I should be able to do whatever I please. 
The OP's system is not yours and was clearly asking for help. I was just giving them all the formation to make an informed decision.

> **dwhitney67 said:**
> 
Now, if someone doesn't have a clue what they are doing, then you are probably right; the should not be doing admin work on their system without first employing some careful thought as to what they are doing, and more importantly, why they are doing it.

editing /etc/* files generally is doing some sort of admin work. So Why suggest doing more admin work then is needed, This would be a personal preference.

---

### Post by shankhs on 2008-08-23
Sorry for late reply , Thanx everybody for helping!!!

---

### Post by shankhs on 2008-08-23
As instructed by dwhitney67 I tried to find .vimrc but I was unable to get it
```

root@shankhs:/home# ls -la
total 12304
drwxr-xr-x  6 root    root        4096 2008-08-24 01:20 .
drwxr-xr-x 22 root    root        4096 2008-08-18 16:22 ..
drwxr-xr-x  2 ftp     nogroup     4096 2008-08-17 01:22 ftp
drwxr-xr-x  4 root    root        4096 2008-08-17 01:25 FTP-shared
-rw-r--r--  1 root    root    12555519 2008-08-18 05:21 Mac4Lin_Wallpapers_Part3_v0.4.tar.gz
drwxrwxrwx  5 root    root        4096 2008-08-18 05:53 Mac_files
drwxr-xr-x 56 shankhs shankhs     4096 2008-08-24 01:17 shankhs

```
Then I created one .vimrc in my home directory and put
```

#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<malloc.h>

:set ai
:set nu

```
Then I created a file foo.c using vim but it was same as before no change.
Am I missing something???? or doing something dumb????
Plz help me!!!

---

### Post by dribeas on 2008-08-23
> **dwhitney67 said:**
> What??  If it's my personal system, I should be able to do whatever I please.

:) I've runned into this at work. Each one of us runs and admins their own one-user system. A couple of times I've had to help solving an specific problem in a project I am not working on, and using their systems with all vi colors changed was confusing the least... 

   David

---

### Post by mike2357 on 2008-08-23
The way I get vi settings to persist is with the following line in my .bashrc file:

export EXINIT='set ai ts=4 sw=4 window=23 report=1 ws nu shell=/bin/bash scroll=11 noerrorbells'

The settings are up to you, but the syntax works.  In order for the command to take effect, you'll either have to open a new command window, or "source" the revised .bashrc file, as follows:

. ~/.bashrc

---

### Post by dwhitney67 on 2008-08-23
> **shankhs said:**
> ...
Then I created one .vimrc in my home directory and put
```

#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<malloc.h>

:set ai
:set nu

```
Then I created a file foo.c using vim but it was same as before no change.
Am I missing something???? or doing something dumb????
Plz help me!!!
Umm, yes...

The .vimrc is used to specify your "vim" (vi) preferences.  Including C headers will cause errors.  "vim" is not an editor for C/C++ code... it is just an editor... period.  It can be used to edit C/C++ code, shell script code, even text files (oh yeah, and Python scripts/gibberish).

P.S.  The last part of the previous statement was intentional... I WANT TO START A FLAME WAR!!!!!

---

### Post by shankhs on 2008-08-24
Can somebody plz explain this:

export EXINIT='set ai ts=4 sw=4 window=23 report=1 ws nu shell=/bin/bash scroll=11 noerrorbells'

Thanx

---

### Post by shankhs on 2008-08-24
I was only able to identify 2 keywords ai and nu.

---

### Post by drubin on 2008-08-24
Give it a little bit of time. Some one will explain it.  :)

---

### Post by mike2357 on 2008-08-24
EXINIT is a shell variable used for vi and other text editors based on "ex".

The following link explains each of the options that I set.

[http://unix.t-a-y-l-o-r.com/VRoptions.html]("http://unix.t-a-y-l-o-r.com/VRoptions.html")

Your options will differ from mine.  I wanted to show how to save vi / vim settings.

---

### Post by shankhs on 2008-08-24
The link given by mike2537 is wonderful,all issues resolved.

Now I think I should mark this thread as solved but I have 2 problems:

1.What does window=23 report=1 and scroll=11 mean,these were not explained in that link.
2.How to mark threads as solved????:confused:
Thanx everybody for your valuable suggestions....
:popcorn:

I got the answer to my second question its right there in the drop down menu by clicking thread tools....

---

### Post by mike2357 on 2008-08-24
report=1          is explained in the link
scroll=11         how many lines to scroll up or down when <CTRL>-D or <CTRL>-U are pressed
window=23         number of lines in the window, exclusive of the one at the bottom for commands

---

### Post by shankhs on 2008-08-26
I think the thread is now solved...

---

