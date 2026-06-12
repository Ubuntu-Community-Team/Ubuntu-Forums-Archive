---
title: "stop signal???"
date: 2010-04-06
forum: Programming Talk
---

### Post by norseman-has-a-laptop on 2010-04-06
ok so  need a stop signal for this project im working on anyone have one i can use???

---

### Post by Zugzwang on 2010-04-06
You need to give for details for helpful answer. "Stop signals" could be pretty much anything. 

[LIST]
[*]Which platform/development environment/programming langauge/whatever are you using?
[*]How do you want a "stop signal" to be processed? / What is it supposed to to be used for?
[*]How can/should a stop signal be issued?
[/LIST]

---

### Post by norseman-has-a-laptop on 2010-04-06
a stop signal for a ibook g4 for a monitoring program i have to find out witch language the program is first so yeah

---

### Post by Reiger on 2010-04-06
Well you know: [http://en.wikipedia.org/wiki/SIGSTOP](http://en.wikipedia.org/wiki/SIGSTOP)

[http://en.wikipedia.org/wiki/Pkill](http://en.wikipedia.org/wiki/Pkill)

So I guess pkill -STOP <process_name> from the shell ought to work; and kill -9 (pkill -KILL) will force the process to stop.

---

### Post by norseman-has-a-laptop on 2010-04-06
> **Reiger said:**
> Well you know: [http://en.wikipedia.org/wiki/SIGSTOP](http://en.wikipedia.org/wiki/SIGSTOP)

[http://en.wikipedia.org/wiki/Pkill](http://en.wikipedia.org/wiki/Pkill)

So I guess pkill -STOP <process_name> from the shell ought to work; and kill -9 (pkill -KILL) will force the process to stop. awesome i will look into it right now

---

