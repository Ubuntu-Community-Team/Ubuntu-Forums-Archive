---
title: "Netbeans Eating Signals"
date: 2008-10-24
forum: Programming Talk
---

### Post by Xeio on 2008-10-24
Ok, I'm using Netbeans with the C/C++ plug in. My code runs fine if I just use the normal 'run' command, but if I attempt to debug the code, Netbeans eats all the signals sent to the terminal, (such as ctrl+z) or forces them to be taken by the terminal itself, rather than handled by it (ctrl-c closes the terminal, rather than letting the terminal handle it).

Is there a way to configure the debugger to not eat any signals it recieves? It seems strange that it would even try this, since it works fine in 'run' mode.

---

