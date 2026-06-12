---
title: "Pythonhome"
date: 2013-07-05
forum: Programming Talk
---

### Post by MikeCyber on 2013-07-05
Hi
How to set pythonhome? I need it for blender.
Many thanks
--------
michael@michael-Ubuntu:/media/michael/DATA2/home/blender-2.49b-linux-glibc236-py26-x86_64$ ./blender
Compiled with Python version 2.6.2.
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Checking for installed Python... No installed Python found.
Only built-in modules are available.  Some scripts may not run.
Continuing happily.

Blender quit
michael@michael-Ubuntu:/media/michael/DATA2/home/blender-2.49b-linux-glibc236-py26-x86_64$ python --version
Python 2.6.2
michael@michael-Ubuntu:/media/michael/DATA2/home/blender-2.49b-linux-glibc236-py26-x86_64$ which python
/usr/local/bin/python
michael@michael-Ubuntu:/media/michael/DATA2/home/blender-2.49b-linux-glibc236-py26-x86_64$ export $PYTHONHOME=/usr/local/bin/python
bash: export: `=/usr/local/bin/python': not a valid identifier
michael@michael-Ubuntu:/media/michael/DATA2/home/blender-2.49b-linux-glibc236-py26-x86_64$

---

### Post by The Cog on 2013-07-05
Get rid of the dollar sign - that is used when recalling the variable, not when setting it:
```
PYTHONHOME=/usr/local/bin/python
```

---

### Post by MikeCyber on 2013-07-06
Still the same:

michael@michael-Ubuntu:/media/michael/DATA2/home/blender-2.49b-linux-glibc236-py26-x86_64$ export PYTHONHOME=/usr/local/bin/python
michael@michael-Ubuntu:/media/michael/DATA2/home/blender-2.49b-linux-glibc236-py26-x86_64$ ./blender
Compiled with Python version 2.6.2.
'import site' failed; use -v for traceback
Checking for installed Python... No installed Python found.
Only built-in modules are available.  Some scripts may not run.

---

### Post by MikeCyber on 2013-07-06
It even got worse. Trying to reinstall default python I get tons of errors. Any help?

---

### Post by nvteighen on 2013-07-06
> **MikeCyber said:**
> It even got worse. Trying to reinstall default python I get tons of errors. Any help?

Where did you install Python and how? Did you use the repos? I'm asking this because it's nearly impossible that exporting a variable could harm a Python installation like that (exported variables that are not saved into .bashrc do not live outside the shell session).

Moreover, how did you install Blender? Blender is in the repos and if you wanted a newer version, you could have got it from testing or unstable without the hassle of configuring everything by yourself... this, unless you're on Slackware.

---

