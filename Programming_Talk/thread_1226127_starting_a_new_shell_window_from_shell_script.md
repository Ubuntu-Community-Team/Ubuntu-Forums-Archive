---
title: "starting a new shell window from shell script"
date: 2009-07-29
forum: Programming Talk
---

### Post by akimatsu123 on 2009-07-29
hi,

I am writing a shell script where I want 2 programs to run simultaneously, and I need to see both programs visually, so running one in the background isn't an option. Is there any way to start a new shell window from a bash script, so I can have 2 simultaneously running shells executing 2 different programs at once??

thanks

---

### Post by hyperAura on 2009-07-30
well u can open a new shell but i dont know if u can actually run another program in that 1 as ur running the other shell.. maybe u can call another script through the 1st one, which is going to open another shell and execute in there..

---

### Post by Dill on 2009-07-30
On Ubuntu, at least (and perhaps on other distributions running GNOME):

```
#!/bin/bash

gnome-terminal

exit 0
```

If you have xterm installed, I'd imagine you could also start another instance of that in a similar manner.

As far as running two programs simultaneously in different windows, I'm not sure how you would fork a process into a different shell window... but I'll try to find out!

Cheers,
Dill

---

### Post by kornyam on 2009-07-30
Depending on which terminal you use, just run the command to open the terminal with the option "-e", and then the command. For example, if I wanted to ping google in a new terminal, I would use:

```
gnome-terminal -e "ping -c3 google.ca"
```

Replace "gnome-terminal" with xterm, etc.

This will, however, close the new terminal after the command ends. I'm not sure how you would keep it open indefinitely.

---

### Post by Dill on 2009-07-30
Ah, I should have read the man page first...

```
gnome-terminal -e [command]
```

Will execute **command** in the new terminal.

Cheers,
Dill

---

### Post by stroyan on 2009-07-30
How to start another terminal will vary from one distribution to the next.
On debian based distributions you can use x-terminal-emulator.
See section 11.8.3 at
[http://www.debian.org/doc/debian-policy/ch-customized-programs.html](http://www.debian.org/doc/debian-policy/ch-customized-programs.html)
```
x-terminal-emulator -e 'script_you_want_to_run arg1 arg2' &
```

---

