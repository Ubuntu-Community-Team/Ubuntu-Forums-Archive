---
title: "couple of questions"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-04-22
1. Where are programs installed?

2. Using CompizConfig i select something like rotate cube but nothing happens!

What am i missing?

Thanks

---

### Post by Joeb454 on 2008-04-22
1) Usually somewhere in /usr/bin, if you are trying to install something, use Add/Remove or Synaptic

2) You need to be running compiz, and to enable the effects etc. before making them work (also check the key bindings etc. :))

---

### Post by ruy_lopez on 2008-04-22
> **iwannalearn said:**
> 1. Where are programs installed?

Programs are installed in a number of places. "/usr/bin", "/usr/sbin", "/bin", "/sbin" are common places for programs.

If you want to know where an individual program is located you can use 'which' or 'whereis' on the command line:

e.g.: looking for 'echo' program
```

$ whereis echo
echo: /bin/echo /usr/share/man/man1/echo.1.gz /usr/share/man/man3/echo.3ncurses.gz
$ which echo
/bin/echo

```

To see where the command line looks for programs:
```

echo $PATH

```

---

