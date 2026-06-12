---
title: "tilde filename question"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by japhyr on 2008-06-28
I saw this command in a post about configuring emacs:

```
xrdb -merge ~/.Xdefaults
```

I have read the tilde is a shortcut to the home directory.  Is this the same as writing

```
xrdb -merge /home/myusername/.Xdefaults
```

Does the tilde ever have a different meaning at the beginning of a path?  (I know it refers to backup files when it's at the end of a path/filename.)

---

### Post by pytheas22 on 2008-06-28
I'm pretty sure it's always just a shortcut for /home/username.  It makes it convenient for giving instructions or writing bash scripts without knowing a user's account name.

---

### Post by hyper_ch on 2008-06-28
the ~ means the homefolder of the current user... if you're logged in as root it will be /root instead of /home/user

---

### Post by wrtpeeps on 2008-06-28
> **japhyr said:**
> I saw this command in a post about configuring emacs:

```
xrdb -merge ~/.Xdefaults
```

I have read the tilde is a shortcut to the home directory.  Is this the same as writing

```
xrdb -merge /home/myusername/.Xdefaults
```

Does the tilde ever have a different meaning at the beginning of a path?  (I know it refers to backup files when it's at the end of a path/filename.)

I believe it is the same.

My terminal (not sure if its the terminal or ubuntu itself) will convert ~/ to /home/andy/ as soon as I type it.

---

### Post by japhyr on 2008-06-28
Thanks everyone, especially the part about writing general scripts that apply to anyone's username.

---

### Post by sdennie on 2008-06-28
You should also be aware that ~ is resolved by the shell to $HOME.  So ~ isn't always valid for a path name.  One common example of this is if you create a custom panel launcher, ~ will not resolve properly and you need to use the full path.

---

### Post by japhyr on 2008-06-28
Actually, that was a question I had around this.  What is $HOME?  What is the difference between /home/username/directory, ~/username/directory, and $HOME/username/directory?

---

### Post by dwhitney67 on 2008-06-28
Actually, I think you meant $HOME/directory.

$HOME = /home/username

$HOME is an environment variable that is initialized when you log in.  To see all environment variables, open a terminal and run this command:
```
$ env
```

---

