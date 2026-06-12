---
title: "edit environment variables"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by melrokz on 2008-12-02
Which is the environment variable config file?
Use of env command with examples?
How to edit this env variable file?

---

### Post by __Ryan__ on 2008-12-02
Environment variables are handled by the shell, usually BASH inUbuntu's case.  You can set an environment variable like so:

```
$ MYVAR=hello
$ echo $MYVAR
hello
```

Permanently set it for all programs launched in the shell by putting **export** keyword in front of it.

```
$ export MYVAR=hello 
```

Make changes permanent by placing them in your **~/.bashrc** file. It is executed and every time you open a new shell.

---

### Post by caljohnsmith on 2008-12-02
To see what the environmental variables are, you can do:
```
env
```
And then to set the variables, just do like __Ryan__ suggested and use "export".

---

### Post by Jermcb on 2008-12-07
I was told to add the following "/usr/share/pk2" to PATH in my enviroment variables... I typed in "env" and found PATH listed there. But when I tried to edit  ~/.bashrc I could not find PATH.

How do I add to the PATH without deleting any other data from its line?

I am new to Ubuntu, so please could you explain in a simple manner...

Thank you

---

### Post by caljohnsmith on 2008-12-07
> **Jermcb said:**
> I was told to add the following "/usr/share/pk2" to PATH in my enviroment variables... I typed in "env" and found PATH listed there. But when I tried to edit  ~/.bashrc I could not find PATH.

How do I add to the PATH without deleting any other data from its line?

I am new to Ubuntu, so please could you explain in a simple manner...

Thank you
Take a look in your .profile instead of .bashrc, and I think you will find PATH there. You can add the new path by doing:
```
PATH="/usr/share/pk2:$PATH"
```
How about trying that and let me know how it goes.

---

### Post by Jermcb on 2008-12-12
Thank you!!!

It worked. I just typed in what you listed above in Terminal and it added it to the PATH.

---

