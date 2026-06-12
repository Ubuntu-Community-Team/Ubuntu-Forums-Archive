---
title: "Just a question about terminal emulator"
date: 2019-05-10
forum: New to Ubuntu
---

### Post by josephfg on 2019-05-10
I am wondering why it is called an emulator (Disco Dingo).  That reminds me of Windows and the "command prompt emulator."  In Linux, are we not actually interacting directly with the OS through command lines in terminal?

Obviously this is not a crucial question but I figure this is the best place to ask it.

---

### Post by The Cog on 2019-05-10
It emulates a real, physical terminal such as a DEC VT100 or VT220 (google it for images). The emulation includes having the same character set, and obeying the same command sequences for features like bold, underline, blink etc.

---

### Post by josephfg on 2019-05-10
Thank you.

---

### Post by The Cog on 2019-05-11
You're welcome. 
Just a note - I just discovered that xfce4-terminal (I use Xubuntu) claims to be (and therefore is emulating) xterm:
```
~$ echo $TERM
xterm-256color
```
but xterm is a VT220 emulator: [https://invisible-island.net/xterm/](https://invisible-island.net/xterm/)
So strictly speaking, it is a terminal emulator emulator. What a tangled web we weave!

---

### Post by ajgreeny on 2019-05-11
And perhaps not surprisingly, if you move to a tty command line terminal display with Ctrl+Alt+F2, ie, out of your DE, whatever that is, and run command **echo $TERM** again you will get the output **linux**.

---

