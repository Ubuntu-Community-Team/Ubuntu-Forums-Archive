---
title: "bash timer"
date: 2011-07-11
forum: Programming Talk
---

### Post by Drenriza on 2011-07-11
Is it possible in bash scripting to say. That if a specific command is executed, then the script should wait X seconds or X minutes before executing the next command in-line?

I thought about doing this with the at command.
For example
"if a specific command is executed at 08:30:10 (hour:minutes:seconds) then create an **at** entry to execute at +5 minutes 08:35:10." but how to tackle this "problem"?
EDIT: thought about using the command ```
date +"%H%M%S"
``` but is it then possible to add 300 seconds or 5 minuts. And then create a **at** entry of this?

Any input would be appreciated.

Kind regards.

---

### Post by ziekfiguur on 2011-07-11
The sleep command does what you need.

---

### Post by Drenriza on 2011-07-11
Thanks :p

Are their any downside effects to this command?

---

### Post by ajgreeny on 2011-07-11
There shouldn't be any problems.
```
command1 && sleep 300; command2
```should work for your 300 second delay.

---

### Post by ziekfiguur on 2011-07-11
You can also use a floating point argument if you want a delay with less that a second. However, there is a limit to the accuracy.

---

