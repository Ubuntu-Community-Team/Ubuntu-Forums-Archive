---
title: "Sorry but i really need help with the cd command"
date: 2021-01-11
forum: New to Ubuntu
---

### Post by mhumphreys1952 on 2021-01-11
I feel really stupid asking this question but here goes,

I cant figure out why my cd command doesn't work. I have read about it on line,  I have tried everything I can think of and to no good avail. Just can't make it work. So here are some screen shots of what I'm doing and hopefully someone will take pity on this poor soul and turn me in the right direction.

First: I am a new user and not very experienced. I have a working relationship with terminal. I'm good at copy and past and know a few commands. Honesty is the best policy I always say. 

Secondly I am using Ubuntu 20.10 "Groovy G."

I know this is really a lame question but i am really stuck...

[ATTACH=CONFIG]287730[/ATTACH]

---

### Post by Perfect Storm on 2021-01-11
> **mhumphreys1952 said:**
> I feel really stupid asking this question but here goes,

I cant figure out why my cd command doesn't work. I have read about it on line,  I have tried everything I can think of and to no good avail. Just can't make it work. So here are some screen shots of what I'm doing and hopefully someone will take pity on this poor soul and turn me in the right direction.

First: I am a new user and not very experienced. I have a working relationship with terminal. I'm good at copy and past and know a few commands. Honesty is the best policy I always say. 

Secondly I am using Ubuntu 20.10 "Groovy G."

I know this is really a lame question but i am really stuck...

[ATTACH=CONFIG]287730[/ATTACH]


Just use
```
cd
```

to go back to home.

Or
```
cd  /home/<username>
```

---

### Post by Skaperen on 2021-01-11
it is telling you that **/michael** does not exist.  are you trying to change to a local directory?  the / starts you all the way at the top.  leave off the / and try again.

---

### Post by TheFu on 2021-01-11
-    HOME directory, $HOME, ~/ - all the same thing
-    root directory, / - top level of all files and directories
-    root HOME directory - /root - on Linux systems.
-    /tmp - a temporary directory. Anyone/nobody can write there. Wiped    at reboot
-    /bin, /usr/bin - where more programs are installed
-    /etc - where most system and package manager settings are stored
-    /usr/local/ - where non-package managed, but system-wide programs    belong

**cd relative and absolute paths**

Relative paths don't begin with a /. They are relative to the pwd/cwd.
Absolute paths ALWAYS begn with a /.  ALWAYS.

These are all the same,  on a normal Linux system.
[B]cd ~  
cd  
cd $HOME  
cd /home/{your-userid} 
cd ~/[/B]

A different example:

    cd
    pwd
    cd /etc
    cd
    cd etc
    cd ../../etc

which are relative and which are absolute?

BTW, /home/{your-userid}  is nothing special. HOME can be any directory that the /etc/passwd file says.  /home/ is not required. It is not hard coded anywhere .... well - except in the snap-constraints code, but no place else that I'm aware.

---

### Post by wildmanne39 on 2021-01-11
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by HermanAB on 2021-01-12
OK, your problem is with the "/".

The slash "/" is either a subdirectory separator, or it indicates the very bottom of the file tree (the root of the tree).

Assuming that michael is your user name, then your home directory is usually /home/michael.

The tilde character "~" is a short form for the home directory, so you can list the contents of your home directory with:
$ ls ~

You can also change diretory to your home directory with:
$ cd ~

You can then see where you are with the present working directory command "pwd":
$ pwd

You can navigate to any home subdirectory with for example:
$ cd ~/Desktop
$ pwd

As mentioned before, the /home directory is not magical and can be anything at all depending on your system setup, but it is almost always /home.  The above commands will show you what is going on.  

Note that spaces are delimeters.  If a space occurs in a file name, then you have to quote the whole string.

---

### Post by ActionParsnip on 2021-01-12
The Linux file system starts at "/" so when you ran:
```

cd /michael

```
it was looking for the folder named **michael **in the root of the file system, not in the **/home** folder

If you'd ran
```

cd ./michael

```

the **./ **part of the command means "look in the current directory" and would have worked. Otherwise it was all ok.

---

### Post by TheFu on 2021-01-12
Good added explanations.

The "~" causes a getent() call to the OS to look up in the passwd database for either the current or specified userid'd HOME.
Here's a few password entries:
```
tf:x:1000:1000:TheFu,,,:/home/tf:/bin/bash
michael:x:1001:1003:Michael,,,:/home/michael:/bin/bash

```
It is colon separated, so a ":" separates each field.  Order matters. Empty fields aren't allowed. We usually don't need to look that close to figure out what the main fields are:
Only the first field, the userid, must be unique. It is common for the uid (1000 or 1001) and the home directories (/home/tf or /home/michael) to be unique, but not mandatory. On some systems, I've seen thousands of users with the same HOME specified. These systems were to run specific programs only, not general purpose systems.  That last field is the login shell for the userid.  A normal user can change the last field between approved shells, as setup either by the system defaults or an admin.  sh, ksh, zsh, fish, psh, tcsh are common, but bash is the default on most Unix systems the last 10 yrs.

Anyways - I digress - using ~tf will look up the tf password entry (same result as running **getent passwd tf**) and provide that as the answer. Similarly, using ~michael will do the same, just **getent passwd michael** instead.  On most Unix systems, looking in the /etc/passwd file is the same, but passwords and userids can be stored on the network using a number of other tools - LDAP, NIS+, and x.500 are used in companies. The call using getent knows about those configured systems and does a network call if there isn't a result in the local /etc/passwd file.  I've seen x.500 systems with over 40K users.

The fields involved are part of the POSIX standard, so if we want to use some other tool, we'd need to ensure that POSIX fields and POSIX calls are supported.

cd ~michael

And don't forget to use {tab} completion. ;)  Save you typing too much, it will. ;)

---

### Post by mhumphreys1952 on 2021-01-12
Thanks so much for all the responses. Such an easy fix as leaving off the /. Or adding a dot. I go forth wiser and humble. Thanks again.

---

### Post by TheFu on 2021-01-12
> **mhumphreys1952 said:**
> Thanks so much for all the responses. Such an easy fix as leaving off the /. Or adding a dot. I go forth wiser and humble. Thanks again.

I'm curious. Which of the statements in the responses helped you the most with understanding?  For example, my post is from a class I teach to beginners. Is it too much too soon?  Plus, we do interactive teaching, so each student can run the commands and is told exactly which keys to press for {tab} completion.  It prevents wrong answers for all existing filenames and directories when used correctly.

---

### Post by HermanAB on 2021-01-12
Note that a simple little dot “.” also has two (or three) meanings.  

A file name starting with a dot is a hidden file that doesn’t show when you do a normal “ls” command.

A dot used with ls or cd indicates the current directory and two dots indicate the previous directory.

UNIX is not unfriendly. It is just very choosy about who exactly its friends are...

---

### Post by CatKiller on 2021-01-13
> **HermanAB said:**
> A file name starting with a dot is a hidden file that doesn’t show when you do a normal “ls” command. 

Fun fact: that was a bug that turned into a feature. Because

> A dot used with ls or cd indicates the current directory and two dots indicate the previous directory.

they didn't want ls to show . or .. and their first implementation just hid anything that started with a . rather than just those two. That behavior turned out to be useful, so they kept it.

---

### Post by The Cog on 2021-01-13
> **TheFu said:**
> Good added explanations.

The "~" causes a getent() call to the OS to look up in the passwd database for either the current or specified userid'd HOME.
 ~tf will look up the tf password entry
Well, after 25+ years using Linux, I'm obviously still a beginner. I just had to try that to see if it was true. It is.
<Shuffles away shaking his head and mumbling...>

---

### Post by TheFu on 2021-01-13
> **The Cog said:**
> Well, after 25+ years using Linux, I'm obviously still a beginner. I just had to try that to see if it was true. It is.
<Shuffles away shaking his head and mumbling...>

If your experience is on single-user, not on team, systems, this wouldn't be important. Of course, just saw that 21.04 HOME directories will get 750 permissions by default.
[https://discourse.ubuntu.com/t/private-home-directories-for-ubuntu-21-04-onwards/19533](https://discourse.ubuntu.com/t/private-home-directories-for-ubuntu-21-04-onwards/19533)

That will force users to learn about group membership.  In the old days, accounts wouldn't get their own group created. This always bothered me. Put users into the 'users' group and every different team would get a different group to control access to group-specific files.  Home Linux users miss out on the group stuff.

---

