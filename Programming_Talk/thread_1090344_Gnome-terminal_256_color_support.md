---
title: "Gnome-terminal 256 color support"
date: 2009-03-08
forum: Programming Talk
---

### Post by Pedro Borges on 2009-03-08
Hi, is there  a way to enable 256 colors support in the terminal?

Thanks

---

### Post by Holy Cheater on 2009-03-11
```
export TERM="xterm-256color"
```
There is no much use of it. But, for example, you can use 256-color vim color-schemes within terminal.

---

### Post by Stearns on 2013-01-23
Is there any way to set the terminal of choice (In my case, Terminator) to launch with support for 256 colors rather than having to type in that command each time I reboot the computer?

-Stearns.

---

### Post by Stearns on 2013-01-27
Adding a few lines to ~/.bashrc seemed to do the trick:

```
if [ "$TERM" == "xterm" ]; then
    export TERM=xterm-256color
fi
```

Although some menu shortcuts to in-terminal applications default back to 8 colors. Went around this by using the following example:

```
terminator -e "TERM=xterm-256color mutt"
```

Hope this helps anyone who come across this thread for the same reason I did.

-Stearns.

---

