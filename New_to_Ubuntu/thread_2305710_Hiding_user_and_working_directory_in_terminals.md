---
title: "Hiding user and working directory in terminals"
date: 2015-12-08
forum: New to Ubuntu
---

### Post by edu-kueyar on 2015-12-08
Hi everyone!

I was wondering if I can hide my user and the current directory in the terminals I open, so that there is more space available to introduce commands (which would allow me to work with smaller terminals).
I'd bet I've seen some people with *~$* only, insted of *****@*****:~/****/***$*

I hope you understand me. Thanks in advance,

Eduardo

---

### Post by steeldriver on 2015-12-08
You can set the PS1 prompt to anything you like, really - googling "customize PS1" or "custom bash prompt" will give you many guides

You may also want to take a look at the PROMPT_DIRTRIM variable e.g.

```

PROMPT_DIRTRIM=3

```

---

### Post by edu-kueyar on 2015-12-08
Sometimes one just needs to know the exact name of what they have to google, especially if they're not native English speakers.
Thank you!

---

