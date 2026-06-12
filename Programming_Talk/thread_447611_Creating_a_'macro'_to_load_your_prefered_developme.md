---
title: "Creating a 'macro' to load your prefered development enviroment"
date: 2007-05-18
forum: Programming Talk
---

### Post by chamstar on 2007-05-18
Hi, I was wondering if there is anything in Ubuntu like a macro recorder. When programming I have my IDE open and three terminals each running a different command (eg. tail -f development.log).

Ideally I'd like to just click something or issue one command and all those windows are 'made' and positioned (I have dual screen). 

Any ideas would be more than welcome.

Cheers Cham.

---

### Post by FuturePast on 2007-05-18
In Ubuntu a macro is called a shell script.
There are many ways to accomplish what you are attempting.

---

### Post by chamstar on 2007-05-21
But can one shell script actually open separate terminals and run commands on those terminals?
And position those and other windows?

Many thanks for your reply :)

---

### Post by cwaldbieser on 2007-05-24
> **chamstar said:**
> But can one shell script actually open separate terminals and run commands on those terminals?
And position those and other windows?

Many thanks for your reply :)

Yes.
```

#! /bin/bash
xterm -geometry '+0+100' -e 'ls -l $HOME | less' & 
xterm -geometry '+500+300' &

```

This is just with a simple xterm.  Look at the man pages for "gnome-terminal" or "konsole" if you want to get fancy.

---

### Post by chamstar on 2007-05-24
That is great thanks. I use gnome-terminal so I'll check its options out.

---

### Post by kobewan on 2007-05-24
You could also take a look at a program called "wmctrl" if you want to position etc. windows.

---

