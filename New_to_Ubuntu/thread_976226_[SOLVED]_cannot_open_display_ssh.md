---
title: "[SOLVED] cannot open display ssh"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by antonio_ing on 2008-11-09
Hi everybody

i'm trying to use a remote desktop through ssh but every time i try to use gedit the terminal tells me

gedit U
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

how can i fix this problem?

thanks in advance

---

### Post by Jeff250 on 2008-11-09
You have to use either the -X or the -Y command line argument with ssh to enable X11 forwarding.  So if before, you said:

```
ssh user@host
```

Now say:

```
ssh -X user@host
```

Note that that is a capitalized X!

---

### Post by antonio_ing on 2008-11-09
i have tried -X already and did not work. it is working fine with -Y

thanks

---

