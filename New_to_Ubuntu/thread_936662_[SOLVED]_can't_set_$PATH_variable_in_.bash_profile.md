---
title: "[SOLVED] can't set $PATH variable in .bash_profile"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by r3bol on 2008-10-03
Hi, I can't seem to setup my own $PATH variable. I read it was to be set in ~/.bash_profile and to use PATH=$PATH:/home/leke/dev/bin
This doesn't seem to work though. Stranger still, if I put it in .bashrc it works, but I heard thats bad because it will multiply when you call bash within the gnome terminal (which it does).

So what am I doing wrong?
Thanks.

---

### Post by jamesrl on 2008-10-03
Instead of editing ~/.bash_profile
use ~/.profile
e.g.:
```

#!/bin/bash
PATH=$PATH:$HOME/local/bin

```
This gets run whenever you login by the script: /etc/gdm/Xsession as well as get logged when you login starting up bash (see INVOCATION section of 'man bash').

EDIT: Removed almost everything, because some of it didn't work properly when adding directories relative to the local path. (e.g. editing /etc/environment doesn't work in both bash/dash if it is a local path.  Original Below:

[I]I'd recommend setting $PATH system wide in /etc/environment ;
e.g.:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:~/local/bin"
```
(note can't use $HOME for ~ as it doesn't work in /etc/environment).
If you want to use .bash_profile when starting an X session, you have to source it by adding the following lines to ~/.xsession 
```

#!/bin/bash

if [ -f $HOME/.bash_profile ]; then
  source $HOME/.bash_profile
fi

```
and .bash_profile:
```

#!/bin/bash
$PATH=$PATH:$HOME/local/bin

```

When you login without X, (e.g. via ssh or after Ctrl-Alt-F[1-6] (use Ctrl-Alt-F7 to get back)), your .bash_profile is auto-loaded.
[/I]

---

### Post by r3bol on 2008-10-03
Thanks, I added my PATH to /etc/environment. I thought it wasn't working at first, but then I realised that I has to logout and back in.

---

