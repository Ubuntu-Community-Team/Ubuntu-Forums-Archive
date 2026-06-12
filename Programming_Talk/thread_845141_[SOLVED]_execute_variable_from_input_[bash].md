---
title: "[SOLVED] execute variable from input [bash]"
date: 2008-06-30
forum: Programming Talk
---

### Post by Dr Small on 2008-06-30
In my bash script, I have a few lines that look like this:
```
a="-f $freq -l $dit -D $breaker -n -f $freq -l $dah"
b="-f $freq -l $dah -D $breaker -n -f $freq -l $dit -r 3"
```

The script name is "cw". When I execute it, I wish to run it like this:
```
cw ab
```

The "ab" part would be the input, to execute the variables in my script. How would I get the input to be passed as variables?

At the bottom of the script I have:
```
beep $($*)
```

But that isn't working. Basically, I want it to play the variables that I have predefined in my script, from the input. The input is a single character (or two) and I need to get it read as a variable (such as $b).

Any help would be much appreciated!
Thanks,
Dr Small

---

### Post by ghostdog74 on 2008-06-30
by running your script this way : cw ab
ab would be stored in $1 variable. you can use that.

---

### Post by Dr Small on 2008-06-30
> **ghostdog74 said:**
> by running your script this way : cw ab
ab would be stored in $1 variable. you can use that.
Thanks for the help, but I have tried that too. I then get an error stating:
```
a: command not found
```

Because it is trying to run "a" not, "$a", which is the variable. Having this would really help with my script, because otherwise, I have to go in and change the variable each time, and that is no fun. :D

Dr Small

---

### Post by geirha on 2008-06-30
Why not use regular option parsing?

Anyway, something like this might work
```
eval beep \$$1
```

---

### Post by Dr Small on 2008-06-30
> **geirha said:**
> Why not use regular option parsing?

Anyway, something like this might work
```
eval beep \$$1
```
Thanks! That worked perfect :D

---

