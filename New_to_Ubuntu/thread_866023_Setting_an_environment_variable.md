---
title: "Setting an environment variable"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by MaeseFernando on 2008-07-21
Hi,

I nee to permanently modify an environment variable called PYTHONPATH.  I added the following to .bashrc and .profile:

#PythonPath
PYTHONPATH=/home/fernando/django/:$PYTHONPATH
export PYTHONPATH

So far this environment variable is available to all processes started from a terminal, but not to those started through the GUI.

What am I doing wrong?  Isn't there an easier way to do this?

Thanks in advance.

---

### Post by aashay on 2008-07-21
Try the same lines in /etc/rc.local
See here: [http://www.linuxquestions.org/questions/linux-newbie-8/set-an-environment-variable-45870/](http://www.linuxquestions.org/questions/linux-newbie-8/set-an-environment-variable-45870/)

---

### Post by sdennie on 2008-07-21
Did you logout and then log back in?  The changes won't be reflected in the initial login shell until you do that.

---

### Post by ibutho on 2008-07-21
> **MaeseFernando said:**
> Hi,

I nee to permanently modify an environment variable called PYTHONPATH.  I added the following to .bashrc and .profile:

#PythonPath
PYTHONPATH=/home/fernando/django/:$PYTHONPATH
export PYTHONPATH

So far this environment variable is available to all processes started from a terminal, but not to those started through the GUI.

What am I doing wrong?  Isn't there an easier way to do this?

Thanks in advance.
If you are using bash, have you tried exporting the variable in ~/.bash_profile instead of ~/.bashrc and then logout and back in again?

---

### Post by MaeseFernando on 2008-07-22
> **vor said:**
> Did you logout and then log back in?  The changes won't be reflected in the initial login shell until you do that.

Yes, I did just that and according the Ubuntu documentation it should have worked, but it didn't. :-?

---

### Post by MaeseFernando on 2008-07-23
> **aashay said:**
> Try the same lines in /etc/rc.local
See here: [http://www.linuxquestions.org/questions/linux-newbie-8/set-an-environment-variable-45870/](http://www.linuxquestions.org/questions/linux-newbie-8/set-an-environment-variable-45870/)

I just tried this, and it still doesn't work. :-(  Any other suggestions?

---

