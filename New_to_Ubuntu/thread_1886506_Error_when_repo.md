---
title: "Error when: repo?"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by gannon5197 on 2011-11-25
You may have seen my earlier post, but I have come across a new problem. I try to set up with the Cyanogenmod tree by putting this: ```
repo init -u git://github.com/CyanogenMod/android.git -b gingerbread
``` in the terminal. But all I get is an error code like: ```

No command 'repo' found, did you mean:
  Command 'rep' from package 'rep' (universe)
  Command 'repl' from package 'nmh' (universe)
  Command 'repl' from package 'mailutils-mh' (universe)
repo: command not found
```

---

### Post by mlentink on 2011-11-25
Well afaik 'repo' is not a bash command, so obviously bash would tell you it can't find the command. I am not familiar with Android development, but perhaps you need that command in the IDE or someting (or on a rooted Android-device?)

---

### Post by lolpenguin on 2011-11-25
WAIT!!!!!!
repo IS A BASH COMMAND but you have to install it. I have recently (failed due to a lack of disk space) compiled the source code of android.
BUT...repo seems to have disappeared...:(

---

### Post by mlentink on 2011-11-25
If you have to install it, it's a program

---

### Post by gannon5197 on 2011-11-25
I might need a little more information here guys. What do I install?

---

### Post by lolpenguin on 2011-11-25
I REMEMBER NOW!
```
cd (directory where you downloaded repo)
```
In the example on the android website:
```
cd ~/bin
```(/home/USER/bin)

---

