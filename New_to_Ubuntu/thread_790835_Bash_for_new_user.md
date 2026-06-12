---
title: "Bash for new user"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Accinson on 2008-05-11
Hi,
i have added a new user from the terminal (with useradd -m).
When i launch the terminal for this user,it seems like i'm not using bash:the prompt is different(just the $ sign),and i have to explicitly run bash.
Why?How can i "fix" this?

Thanks in advance :)

---

### Post by Monicker on 2008-05-11
sudo usermod -s /bin/bash username

---

### Post by Accinson on 2008-05-19
Hi,
sorry for the delay of the answer...
I tried the command (and reading its man page it does seem to be what i am looking for) but it doesn't work...

In the meanwhile i installed csh,and (i dont know why) it has become my default shell.Now,after i run the terminal,in order to use bash, i always have to run:
```
% bash
bash: setenv: command not found
bash: setenv: command not found
nuovo@ace5720g-laptop:~$ 

```
Any clue?

---

