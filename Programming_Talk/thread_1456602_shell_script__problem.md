---
title: "shell script  problem"
date: 2010-04-17
forum: Programming Talk
---

### Post by vksingh on 2010-04-17
Hi Friends,

Can some body tell me the following:

echo $?

when I type on terminal, I get 0.

Please help.

Thanks,

Vivek

---

### Post by falconindy on 2010-04-17
What are you expecting to happen? The variable $? holds the exit code of the last run program.

---

### Post by lykeion on 2010-04-17
Well, what's your question really?

$? is a variable substitution for the exit status of the last command, and exit status 0 means success... so you get OK for your last command (which is echo $?)

---

### Post by falconindy on 2010-04-17
> **lykeion said:**
> Well, what's your question really?

$? is a variable substitution for the exit status of the last command, and exit status 0 means success... so you get OK for your last command (which is echo $?)

Running 'echo $?' twice will give you a success. The first time you run it, it really does recall the last error message. You'd be solving the chicken and the egg problem otherwise -- how can 'echo $?' know what it's going to return before it returns?

```
$ asdfj
zsh: command not found asdfj
$ echo $?
127
$ echo $?
0
```

---

