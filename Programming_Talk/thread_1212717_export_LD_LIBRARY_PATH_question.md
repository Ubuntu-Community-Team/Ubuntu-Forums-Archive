---
title: "export LD_LIBRARY_PATH question"
date: 2009-07-14
forum: Programming Talk
---

### Post by jithin1987 on 2009-07-14
I have these in my .bash_profile

export CPPLIBS=/tmp/cpp/
export LD_LIBRARY_PATH=$CPPLIBS:$LD_LIBRARY_PATH

But only the CPPLIBS is getting set.
I still have to manually run 

export LD_LIBRARY_PATH=$CPPLIBS:$LD_LIBRARY_PATH from terminal to change LD_LIBRARY_PATH.

Can anyone please tell me why export LD_LIBRARY_PATH in bash_profile is not working as expected.

---

### Post by avsd on 2010-07-09
The same problem. All environment variables could be exported from there, except of LD_LIBRARY_PATH

Please, help

---

### Post by dwhitney67 on 2010-07-09
Are you running a login-shell?  Or a script?

Here's the different files that are referenced by bash under different circumstances:
```

FILES
       /bin/bash
              The bash executable
       /etc/profile
              The systemwide initialization file, executed for login shells
       /etc/bash.bashrc
              The systemwide per-interactive-shell startup file
       /etc/bash.bash.logout
              The systemwide login shell cleanup file, executed when a login shell exits
       ~/.bash_profile
              The personal initialization file, executed for login shells
       ~/.bashrc
              The individual per-interactive-shell startup file
       ~/.bash_logout
              The individual login shell cleanup file, executed when a login shell exits
       ~/.inputrc
              Individual readline initialization file

```

Personally, I had no trouble setting LD_LIBRARY_PATH in my .bash_profile, and having it set when I created a new login shell.  Ditto if I place the definition in .bashrc.

---

