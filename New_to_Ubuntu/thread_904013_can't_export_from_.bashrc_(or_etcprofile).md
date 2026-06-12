---
title: "can't export from .bashrc (or /etc/profile)"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by ZiVvmO on 2008-08-28
I am trying to install a program (GEMS simulator for anyone who's in computer architecture).  I'm following a setup guide and it says:

Then we add lines to $HOME/.profile
   export*GEMS=$HOME/gems
   export*SIMICS_INSTALL=$GEMS/simics*3.0.30
   export*SIMICS_EXTRA_LIB=./modules
   export*PYTHONPATH=./modules

Now, since I'm using bash (obviously), I went ahead and put these into my .bashrc.  When I start a new shell, I get:

bash: export GEMS=/home/pj/gems: No such file or directory
bash: export SIMICS_INSTALL=/home/pj/gems/simics*3.0.30: No such file or directory
bash: export SIMICS_EXTRA_LIB=./modules: No such file or directory
bash: export PYTHONPATH=./modules: No such file or directory

So, I tried putting it in /etc/profile.  I get the same errors.  So, I tried writing a script "gems.script".  I get the same errors.  Now, I can assure you that these directories do in fact exist.

Anyone know what the deal is?

---

### Post by ZiVvmO on 2008-08-28
Okay, I figured it out.  When you copy text from KPDF to the clipboard, it copies spaces as hex C2A0 not C2.  I don't get it.

---

