---
title: "Condition if &lt;program x is running&gt;"
date: 2007-04-20
forum: Programming Talk
---

### Post by eentonig on 2007-04-20
I know it's a stupid questions and the answer will be extremely easy. But for the hell of it, I can't find the answer. and I want to do this, because I really need to devellop my scripting skill.

I want to create a little script that stops Beryl when I want to watch a movie (or whatever program).

The logic would be to write a function that

If Beryl is running >> kill Beryl and start Metacity.
If Beryl is not running >> Do nothing.
...
run program X

So I need an If statement that checks if Beryl is currently running or not. But what is the easiest/most common way of determining if a program is running or not?


PS. I tried using the script in [this topic]("http://ubuntuforums.org/showthread.php?t=338873"), but it fails on this condition.

---

### Post by rjack on 2007-04-20
There are many ways.

If the program uses a pid file in /var/run you can check if the pid file exists. This is simple, but if the program crashes and do not clear its pidfile your script will act as it would be still running.

Example:
```
if [[ -f /var/run/$PIDFILE ]]
then kill  $(cat /var/run/$PIDFILE)
```

Another way it's to use pidof

```

if pidof $program_name
then kill $(pidof $program_name)
```

[More on file test operators]("http://tldp.org/LDP/abs/html/fto.html")
More on pidof: man pidof

---

