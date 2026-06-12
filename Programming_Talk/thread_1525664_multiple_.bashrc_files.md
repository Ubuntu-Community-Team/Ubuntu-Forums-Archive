---
title: "multiple .bashrc files"
date: 2010-07-07
forum: Programming Talk
---

### Post by esedizzle on 2010-07-07
Recently after typing:
```
locate .bashrc
```
i found several answers: 
```
/etc/bash.bashrc
/etc/skel/.bashrc
/home/matias/.bashrc
/root/.bashrc
/usr/share/base-files/dot.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/bash.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bashrc
```
I want to modify one of the .bashrc files.  Which one is the right one to add too?  If i add to one will it transfer to the others.  How do i transfer to the others?

---

### Post by Lampi on 2010-07-07
I don't think they transfer

bashrc in $HOME will always  be checked first hand, if it's not available the system wide /etc/bash.bashrc will be used (if sourced in /etc/profiles)

So you need to change bashrc in /home/matias/ and /root or you can rename/delete those files and use /etc/bash.bashrc instead - this one will be valid for every user in the system

---

### Post by esedizzle on 2010-07-11
Ok that makes sense.  could you point me to an article that explains this?

---

### Post by soltanis on 2010-07-11
From the manpage:

```

**BASH(1)**                                                                

**NAME**
       bash - GNU Bourne-Again SHell
...

**INVOCATION**
...

       When bash is invoked as an interactive login shell, or as a  non-inter&#8208;
       active  shell with the --login option, it first reads and executes com&#8208;
       mands from the file */etc/profile*, if that file exists.   After  reading
       that file, it looks for *~/.bash_profile*, *~/.bash_login*, and *~/.profile*,
       in that order, and reads and executes commands from the first one  that
       exists  and  is  readable.  The --noprofile option may be used when the
       shell is started to inhibit this behavior.

       When a login shell exits, bash reads and  executes  commands  from  the
       file *~/.bash_logout*, if it exists.

       When  an  interactive  shell that is not a login shell is started, bash
       reads and executes commands from  */etc/bash.bashrc*  and  *~/.bashrc*,  if
       these  files  exist.  This may be inhibited by using the --norc option.
       The --rcfile file option will force bash to read and  execute  commands
       from file instead of */etc/bash.bashrc* and *~/.bashrc*.

       If bash is invoked with the name sh, it  tries  to  mimic  the  startup
       behavior  of  historical  versions  of sh as closely as possible, while
       conforming to the POSIX standard as well.  When invoked as an  interac&#8208;
       tive  login  shell, or a non-interactive shell with the --login option,
       it first attempts to read and execute commands  from  */etc/profile*  and
       *~/.profile*,  in  that  order.   The  --noprofile  option may be used to
       inhibit this behavior.  When invoked as an interactive shell  with  the
       name  sh,  bash  looks for the variable ENV, expands its value if it is
       defined, and uses the expanded value as the name of a file to read  and
       execute.  Since a shell invoked as sh does not attempt to read and exe&#8208;
       cute commands from any other startup files, the --rcfile option has  no
       effect.   A  non-interactive  shell  invoked  with the name sh does not
       attempt to read any other startup files.   When  invoked  as  sh,  bash
       enters posix mode after the startup files are read.

       When  bash  is  started in posix mode, as with the --posix command line
       option, it follows the POSIX standard for startup files.  In this mode,
       interactive  shells  expand  the ENV variable and commands are read and
       executed from the file whose name is  the  expanded  value.   No  other
       startup files are read.

```

---

### Post by iMisspell on 2010-07-11
Dont know if this will help you any, but...

Files found in /etc/skel/ are used when making a new user account. These files are copied over to the new account. If you edit the /etc/skel/.bashrc file, it will not effect any of your current users, but, the edits you make will be present in all *new* user accounts you make. 

/home/matias/.bashrc
Is the .bashrc file which the user 'matias' uses. So if you are user matias, that is the file you want to edit.

/root/.bashrc
Is for your root account.

/usr/share/doc/adduser/examples/adduser.local.conf.examples/bash.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bashrc
Are examples (just like the file path says)

/etc/bash.bashrc
/usr/share/base-files/dot.bashrc
Dont know about those two...

---

### Post by esedizzle on 2010-07-13
thank you that does help alot.  Just one more stupid question.  If I type .bashrc into the command line it will open the home/matias/.bashrc right?

---

### Post by Ibidem on 2010-07-13
Not quite if I understand you properly:
.bashrc: command not found
It is not present in the "path", so that won't work.
. ~/.bashrc
 may work, and 
~/.bashrc 
may work. But the preferred method is just starting bash.


Now, if you mean "Does 'gedit .bashrc' open the right file?" the answer is, it depends on your folder.  Ordinarily it will work.  gedit ~/.bashrc should work anywhere.

---

