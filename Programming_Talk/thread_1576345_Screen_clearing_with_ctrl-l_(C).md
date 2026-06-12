---
title: "Screen clearing with ctrl-l (C)"
date: 2010-09-17
forum: Programming Talk
---

### Post by pswoo on 2010-09-17
I'm aware that there are various methods for clearing the terminal (e.g. system("clear")), but how can I get this to happen precisely when Ctrl-L is hit?

Many interactive programs are capable of clearing the screen upon such an action -- irb, clisp, gdb, etc. -- others (like ghci) cannot. I think the GNU readline library offers such a capability, but is there a way of getting that behavior without it?

It's really just for convenience, but I'd really like to figure out how to get it done... Ctrl-L is not a signal, and it doesn't seem to be like Ctrl-D where a character is immediately sent to stdin. Googling around for a solution, some other people have been referred to the tcsetattr and termios documentation -- I looked into this but didn't really understand much of it :\. Any suggestions would be appreciated.

---

