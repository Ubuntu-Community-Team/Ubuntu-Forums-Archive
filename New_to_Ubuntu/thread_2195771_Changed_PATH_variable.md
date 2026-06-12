---
title: "Changed PATH variable"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by gasior.tt on 2013-12-26
Hey, 

Im so noob. I wanted to access the folder that have a space in the name. So  I did sth like this:

I did this: 

cd Texas Instruments
bash: cd: Texas: No such file or directory

PATH="Texas Instruments"
cd "$PATH"

I made it :D but I thought it is just random variable like a b c. Well, it isn't. Now I cant do commands like ls:

Command 'ls' is available in '/bin/ls'
The command could not be located because '/bin' is not included in the PATH environment variable.
ls: command not found

Please help me restore defult PATH variable. 

Thanks in advance

---

### Post by Iowan on 2013-12-26
Have you tried logging out and back in?

For your original experiment:
Did you try **cd "Texas Instruments"** or **cd 'Texas Instruments'**?

---

### Post by gasior.tt on 2013-12-26
I prefer not to, somehow I feel it will just make things complicated even more. Firstly I'd like to restore my PATH variable. I'm sure there is a way.

---

### Post by gasior.tt on 2013-12-26
[SOLVED .. i think so] 

I did this:

export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

 it works now as it was before

---

### Post by Elfy on 2013-12-26
> **Iowan said:**
> Have you tried logging out and back in?

For your original experiment:
Did you try **cd "Texas Instruments"** or **cd 'Texas Instruments'**?

This and try tab complete too, also [http://ss64.com/nt/cd.html](http://ss64.com/nt/cd.html)

---

### Post by drmrgd on 2013-12-26
> **gasior.tt said:**
> [SOLVED .. i think so] 

I did this:

export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

 it works now as it was before

Just for future reference, a change to your PATH variable like that is good only for the session in which you are logged in.  If you want to make a permanent change, then you need to make the change in .bashrc (for example).  So, if you accidentally hose your PATH variable again by changing it from the commandline (which is what I assumed you did based on what you wrote), then all you need to do to fix it is to close that terminal session and start a new one.  If however, you do make the change in .bashrc, then it will be set every time you start a new terminal session.

---

