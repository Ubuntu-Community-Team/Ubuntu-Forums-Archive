---
title: "Screen and sending commands to sessions"
date: 2011-09-10
forum: Programming Talk
---

### Post by Fenlig on 2011-09-10
Hey Guys,

Okay so Im writing a script in bash which will send a command to a detached session named mine_server, but when ever I run the command it sends it to the session but does not execute it.

Command I run: minecraft@Servertron:~$ screen -S mine-server -X stuff hello

And this is what I see on the session: minecraft@Servertron:~$ hello

I've looking over this tutorial and cannot see where I am going wrong:
[http://www.jerri.de/blog/archives/2006/05/02/scripting_screen_for_fun_and_profit/](http://www.jerri.de/blog/archives/2006/05/02/scripting_screen_for_fun_and_profit/)

Any Ideas?

---

### Post by Toz on 2011-09-10
Try this:
```
screen -S mine-server -X stuff hello$'\n'
```

The $'\n' will send the return sequence as well.

---

