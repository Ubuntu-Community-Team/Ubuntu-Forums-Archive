---
title: "Piping commands is causing &quot;command not found&quot; error"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by vnuckcha on 2008-08-28
Hello,

I have just installed Ubuntu 8.04 LTS and i am encountering the following problem:
```

$ history | grep lib
bash: grep: command not found
```

However, grep exists. Running 
```
$ which grep
/bin/grep
```

The same problem exists when i run for example,
```
$ history | less
bash: less: command not found
```

Would someone have an explanation and a solution ?

Kind Regards

---

### Post by iaculallad on 2008-08-28
What displays when your issue the command below on your terminal:

```
echo $PATH
```

---

### Post by ingeva on 2008-08-28
> **vnuckcha said:**
> Hello,

I have just installed Ubuntu 8.04 LTS and i am encountering the following problem:
```

$ history | grep lib
bash: grep: command not found
```However, grep exists. Running 
```
$ which grep
/bin/grep
```The same problem exists when i run for example,
```
$ history | less
bash: less: command not found
```Would someone have an explanation and a solution ?

Kind Regards

grep doesn't find "lib".
less doesn't find its command. I don't remember less much, but it's probably missing a parameter. Try less --help and grep --help.

Probably nothing wrong with grep or less. They both give you some feedback.

---

### Post by vnuckcha on 2008-08-28
Hello,

This is the output of the PATH variable:
```

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
As you can see, **/bin** is in the path.

:/

---

### Post by vnuckcha on 2008-08-28
Hi Ingeva,

The errors mean that the commands (grep and less) cannot be located on the filesystem.

The ```
$echo $PATH
``` command that iaculallad asked me to check is to verify if those commands are indeed on the system path.

Hope this helps towards your understanding of the problem.

Kind Regards

---

### Post by iaculallad on 2008-08-28
> **vnuckcha said:**
> Hello,

This is the output of the PATH variable:
```

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
As you can see, **/bin** is in the path.

:/

Could you check your /etc/profile file if we are similar with what I'm posting below:

```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022
```

Code above is from Hardy's.

---

### Post by prshah on 2008-08-28
> **vnuckcha said:**
> 
```

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```


What happens of you only use less without piping?

Can you also check your permissions for /bin and /usr/bin as well as the commands themselves?
```

ls -ld /bin
ls -ld /usr/bin
ls -l `which grep`
ls -l `which less`
```

---

### Post by wdaniels on 2008-08-28
Does:

```
history |grep lib
```

(i.e. without the space after the pipe character) work?

This can sometimes be a locale problem in that the space character sent by your locale settings in X is not interpreted as whitespace (or something like that). What are your language settings?

---

### Post by ingeva on 2008-08-28
> **vnuckcha said:**
> Hi Ingeva,
The errors mean that the commands (grep and less) cannot be located on the filesystem.


I'm sorry, you are right.
grep and less are SO standard that they should just always be installed,
so I assumed that they were just used wrongly. My mistake.

---

### Post by vnuckcha on 2008-08-28
> **iaculallad said:**
> Could you check your /etc/profile file if we are similar with what I'm posting below:

```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022
```

Code above is from Hardy's.

Hi,

There is no difference from the /etc/profile listing you gave and the one on my computer.

I did a diff and compared line by line manually 

Kind Regards

---

### Post by vnuckcha on 2008-08-28
> **prshah said:**
> What happens of you only use less without piping?

Can you also check your permissions for /bin and /usr/bin as well as the commands themselves?
```

ls -ld /bin
ls -ld /usr/bin
ls -l `which grep`
ls -l `which less`
```

Hi,

The permissions on the directories and files are ok. Here is a listing:
```
$ ls -ld /bin
drwxr-xr-x 2 root root 4096 2008-08-27 16:01 /bin
$ ls -ld /usr/bin
drwxr-xr-x 2 root root 36864 2008-08-27 17:04 /usr/bin
$ ls -l `which grep`
-rwxr-xr-x 1 root root 100536 2007-10-23 23:58 /bin/grep
$ ls -l `which less`
-rwxr-xr-x 1 root root 120884 2008-02-02 05:51 /usr/bin/less

```

Also the commands are accessible on their own. So, i can do something like ```
$ less tst.txt
``` and it works fine.

Kind Regards

---

### Post by vnuckcha on 2008-08-28
> **wdaniels said:**
> Does:

```
history |grep lib
```

(i.e. without the space after the pipe character) work?

This can sometimes be a locale problem in that the space character sent by your locale settings in X is not interpreted as whitespace (or something like that). What are your language settings?

Hi,

You are absolutely right regarding the space after the pipe. It works fine without it.

The locale is 'fi' (finnish)

Thanks a lot.

Kind Regards,
vik

---

### Post by wdaniels on 2008-08-28
> **vnuckcha said:**
> Hi,

You are absolutely right regarding the space after the pipe. It works fine without it.

The locale is 'fi' (finnish)

Thanks a lot.

Kind Regards,
vik

Unfortunately I have no idea how to fix it (I don't really understand locales well enough). You will probably find it causes all kinds of other problems, so hopefully someone can enlighten us...

---

### Post by wdaniels on 2008-08-28
It might be an idea to post about this on the [Finnish Ubuntu forums]("http://www.ubuntu-fi.org/") and if you figure it out, please post the answer back here.

Otherwise, I would suggest you try to make sure there are no mismatches between encodings or variants of the finnish locale for the shell and for X. I am completely guessing, but I would think UTF-8 is what you want to be using everywhere. Note that there is an encoding option in gnome-terminal itself (in the menu Terminal->Set Character Encoding), so check what that is set to.

Sorry I can't be of more help.

---

### Post by brian_p on 2008-08-28
> **vnuckcha said:**
> Hi,

You are absolutely right regarding the space after the pipe. It works fine without it.

The locale is 'fi' (finnish)

Maybe:

[https://bugs.launchpad.net/ubuntu/+bug/218637](https://bugs.launchpad.net/ubuntu/+bug/218637)

---

