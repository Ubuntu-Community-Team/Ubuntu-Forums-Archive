---
title: "output of a command to a varable (bash)"
date: 2007-09-28
forum: Programming Talk
---

### Post by wiscados on 2007-09-28
How can I get the output of a command, and use it later as the input of an other command...?

---

### Post by ryanVickers on 2007-09-28
try making at the end of the command a ">> variablename" and then later do "$variablename command"

tell me if it works!  (should - it's fairly simple :))

If your interested in anything to do with RAR files, or want some examples on other stuff like this, I'm working on a little something (see signature :))

---

### Post by Nekiruhs on 2007-09-28
> **ryanVickers said:**
> try making at the end of the command a ">> variablename" and then later do "$variablename command"

tell me if it works!  (should - it's fairly simple :))

If your interested in anything to do with RAR files, or want some examples on other stuff like this, I'm working on a little something (see signature :))
That will put the output of the command into the file variablename in your home directory.
Do this:
```
Variable = $(command)
```

Or
```
Variable = `command`
```

Then just reference it like a normal variable.

---

### Post by ryanVickers on 2007-09-28
huh, maybe I've done it *slightly* differently in the past! :p  Yeah, your right, that's what it does!  oops :)

---

### Post by wiscados on 2007-09-28
nope, is says > line 4: Variable: command not found


---

### Post by Nekiruhs on 2007-09-28
> **wiscados said:**
> nope, is says
Can you post your code? Maybe then I can be of more help.

---

### Post by wiscados on 2007-09-28
```
Variable = $(head -n 2 log.txt | tail -n 1)
./mp32ogg.pl Variable
```

---

### Post by mssever on 2007-09-28
```
Variable=[COLOR=Red]"[/COLOR]$(head -n 2 log.txt | tail -n 1)[COLOR=Red]"[/COLOR]
./mp32ogg.pl [COLOR=Red]"$[/COLOR]Variable[COLOR=Red]"[/COLOR]
```

Note also that whitespace on either side of the equal sign is forbidden.

---

### Post by wiscados on 2007-09-29
Thank you, it worked!!

---

