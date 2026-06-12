---
title: "[SOLVED] run bash commands from compiled C program?"
date: 2008-02-16
forum: Programming Talk
---

### Post by JPotter on 2008-02-16
just like the title: Is there a way to run a terminal command from inside a compiled C program.

Something along the lines of the windows command:
[PHP]system(call_string);[/PHP]

where call_string is a character string (obviously)

---

### Post by stroyan on 2008-02-16
That is a bit of any easy question.
The system() function is just the same in linux.
```
sudo apt-get install manpages-dev.
man system
```

---

### Post by JPotter on 2008-02-16
Wow . . .

Thanks, this fixed my problem.

Edit: Rather . . . Now I can't figure out why my code didn't work in the first place.

---

### Post by rbprogrammer on 2008-02-16
> **JPotter said:**
> Wow . . .

Thanks, this fixed my problem.

Edit: Rather . . . Now I can't figure out why my code didn't work in the first place.
as you may already know, linux commands usually differ from windows commands.... did you rmember to change the windows commands to linux commands??

posting the part of your code that does the system( .. ) can help too

---

