---
title: "chmod"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by TheLittleNapoleon on 2012-06-07
check the following response after i tried to run the command. Can somebody tell me what am i doing wrong here:

cliet@ubuntu:~$ echo echo Hellow World > bin/hw
cliet@ubuntu:~$ bash bin/hw
Hellow World
cliet@ubuntu:~$ chmod +x bin/how
chmod: cannot access `bin/how': No such file or directory
cliet@ubuntu:~$ chmod +x bin/hw
cliet@ubuntu:~$ hw
hw: command not found

---

### Post by nothingspecial on 2012-06-07
Assuming you have just created the ~/bin directory you need to log back in so that it is included in your path.

Or you can type ```
. .profile
```

---

### Post by Lars Noodén on 2012-06-07
That's because **.** is not in your path.

```

echo $PATH

```

It is excluded for sound security reasons. I'm not finding any good articles explaining it, but by excluding the current directory prevents the possibility of sprinkling directories with malicious scripts with the same name as legitimate programs. 

If you want to run 'hw', you'll have to include the full path or a relative path.  e.g. ./bin/hw, or ~/bin/ht, or /home/thelittlenapoleon/bin/hw

However, if 'bin' is in your home directory, Ubuntu should add it to the path.  If you recently created the directory, try logging out and then back in again.  The login scripts should then find 'bin' for you and add it to your path automatically.

---

### Post by cortman on 2012-06-07
Or if it doesn't automatically find it, you can always set it with

```
PATH=$PATH:/home/username/bin
```

---

### Post by nothingspecial on 2012-06-07
```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
[COLOR="Red"]if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi[/COLOR]

```

It's in the default .profile file which is read when you log in. Which is why you have to log back in or source .profile

---

### Post by TheLittleNapoleon on 2012-06-07
Thank you so much. i realised using tty1 executes the command bt i cannot do it with bash 1. Why is it that way, whats the reason.

---

