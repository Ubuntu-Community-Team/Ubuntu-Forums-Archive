---
title: "can't find user folders in /home directory"
date: 2014-12-28
forum: New to Ubuntu
---

### Post by kuperoy on 2014-12-28
Hi,

I've created several new users using the command "useradd". When I check for the defaults I get this:
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/sh
SKEL=/etc/skel
CREATE_MAIL_SPOOL=no

Yet, when I go into the /home folder I can't see the users I've created.
I am really new to linux, but I have done "su" command before I have created the new users.

Please advise,
Roy

---

### Post by Holger_Gehrke on 2014-12-28
You should have either given the option -m / --create-home or used adduser. useradd does not create home directories unless specifically told to do so.

---

### Post by claracc on 2014-12-29
Yes, you have to use -m option with useradd comand in order to create user's home directory.

From man useradd:

" -m, --create-home
           Create the user's home directory if it does not exist. The files
           and directories contained in the skeleton directory (which can be
           defined with the -k option) will be copied to the home directory.

           By default, if this option is not specified and CREATE_HOME is not
           enabled, no home directories are created."

---

### Post by sandyd on 2014-12-29
> **kuperoy said:**
> Hi,

I've created several new users using the command "useradd". When I check for the defaults I get this:
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/sh
SKEL=/etc/skel
CREATE_MAIL_SPOOL=no

Yet, when I go into the /home folder I can't see the users I've created.
I am really new to linux, but I have done "su" command before I have created the new users.

Please advise,
Roy

If you want ubuntu to create the folder automatically, either use adduser (which asks you a set of questions as well) or use the -m flag.
If you want to find out what flags can be used with a particular program, you can try running
```

*programname* --help
```
or```

man *programname*
``` which will display the documentation on the command.

---

### Post by nerdtron on 2014-12-29
> **kuperoy said:**
> Hi,

I've created several new users using the command "useradd". When I check for the defaults I get this:
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/sh
SKEL=/etc/skel
CREATE_MAIL_SPOOL=no

Yet, when I go into the /home folder I can't see the users I've created.
I am really new to linux, but I have done "su" command before I have created the new users.

Please advise,
Roy

Aside from the -m option as suggested above, Ubuntu has the "**adduser**" utility which is much friendlier when creating user accounts. It's like a frontend to the old useradd command. Give it a try like:
```
sudo adduser testuser
```

---

