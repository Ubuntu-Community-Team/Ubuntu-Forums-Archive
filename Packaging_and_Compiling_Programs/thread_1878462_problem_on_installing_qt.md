---
title: "problem on installing qt"
date: 2011-11-09
forum: Packaging and Compiling Programs
---

### Post by rinosalman on 2011-11-09
hi..
i'm being installing qt on my ubuntu 10.10..
i followed this

Set some environment variables in the file .profile (or .login,
depending on your shell) in your home directory. Create the
file if it is not there already.

 In .profile (if your shell is bash, ksh, zsh or sh), add the
    following lines:

    QTDIR=/usr/local/qt
    PATH=$QTDIR/bin:$PATH
    MANPATH=$QTDIR/doc/man:$MANPATH
    LD_LIBRARY_PATH=$QTDIR/lib:$LD_LIBRARY_PATH

    export QTDIR PATH MANPATH LD_LIBRARY_PATH

i have tried...but when open my text editor and typed those, and save at home  with name .profile, appear this

Could not save the file /home/.profile.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again

help please...i appreciate any help that can be given

---

### Post by MadCow108 on 2011-11-11
your user writable home directory is
```
/home/*username*
```
not /home, which is owned by root

you can get your username with this command on the commandline:
```
whoami
```

---

### Post by Bachstelze on 2011-11-11
Your home directory is /home/*username*, so save it as /home/*username*/.profile.

---

