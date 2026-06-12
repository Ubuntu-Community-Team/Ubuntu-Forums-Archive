---
title: "My own log"
date: 2011-03-27
forum: Programming Talk
---

### Post by Acruax on 2011-03-27
Hello, I need to make my own log file:

date - time
commands
date - time
commands

When I start new working session in terminal it must append new 'date - time' line to log file. Each command must be written to log file.

Can you help me with this?

---

### Post by nice_like_rice on 2011-03-27
Probably not the best forum for this ;)

Try using "script".

```
script mylog.log
```

I guess you could add this to .bashrc to run when opening a shell, and use the -a option to append instead of replacing.

---

### Post by slavik on 2011-03-27
and configure logrotate to rotate/compress the log.

---

### Post by Acruax on 2011-04-03
It is a task for Lab at the university. I need to use ~/.bashrc file. I think that I can use this string in the ~/.bashrc to start session in log file: date +%D >> mylog.log

After this I think I need to catch every command and append it to the mylog.log. But how can I catch commands after I type Enter?

I have tried to use "script" but I need to log only commands without output.

---

### Post by slavik on 2011-04-04
> **Acruax said:**
> It is a task for Lab at the university. I need to use ~/.bashrc file. I think that I can use this string in the ~/.bashrc to start session in log file: date +%D >> mylog.log

After this I think I need to catch every command and append it to the mylog.log. But how can I catch commands after I type Enter?

I have tried to use "script" but I need to log only commands without output.
write your own shell.

---

