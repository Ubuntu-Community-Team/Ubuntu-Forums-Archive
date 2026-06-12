---
title: "Running csh commands in a bash script"
date: 2008-11-14
forum: Programming Talk
---

### Post by orlox on 2008-11-14
I want to pass a howto that consists in a series of commands to be put in a console into a bash script, but I'm having issueas at a point. I need to create a user (called iraf) that instead of bash, uses csh command interpreter.

There's no problem at this point. But then, I need to initiate a session with this user, use the csh command setenv, and run a script as that user:

```

sudo su iraf
setenv iraf /iraf/iraf
cd $iraf/unix/hlib/
source irafuser.csh
./install

```
How can I do this with a bash script???

---

### Post by dwhitney67 on 2008-11-14
> **orlox said:**
> I want to pass a howto that consists in a series of commands to be put in a console into a bash script, but I'm having issueas at a point. I need to create a user (called iraf) that instead of bash, uses csh command interpreter.

There's no problem at this point. But then, I need to initiate a session with this user, use the csh command setenv, and run a script as that user:

```

sudo su iraf
setenv iraf /iraf/iraf
cd $iraf/unix/hlib/
source irafuser.csh
./install

```
How can I do this with a bash script???

Is it possible to create a wrapper script (in csh or tcsh) that accomplishes the steps you require?  If so, then you should be able to run that script using something like:
```

su -s /bin/tcsh - iraf /home/iraf/script.tcsh

```
This command instructs 'su' to use the tcsh shell, to run as user 'iraf' (which will prompt for a password), and then run the script.tcsh, which presumably has its mode set properly so that it is an executable.

I tested with a script that had this in it:
```

#!/bin/tcsh

setenv FOO foobar

echo $FOO

```

---

