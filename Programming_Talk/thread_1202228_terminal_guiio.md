---
title: "terminal gui/io"
date: 2009-07-02
forum: Programming Talk
---

### Post by ooobooontooo on 2009-07-02
Hi,

I'm trying to build an application that is terminal-based (like mutt and vim), so I need the libraries to do some terminal gui/io. I've googled and I found termcap, terminfo, termios, curses, and ncurses. Which library do you recommend? Frankly, I can't really tell the differences between the term*. (I know terminfo is supposed to be the new termcap...but I can find termcap.h but not terminfo.h...and then there's termios....) I know the term* are supposedly for lower level operations while the *curses are for higher level operation, but it seems that *curses aren't as widespread as term*. I want my application to be relatively universal in the *nix world, so would like to know if basing my application on *curses would hinder me from exporting it to other *nix boxes. Thanks in advance.

P.S. Also, if you recommend term*, could you refer a tutorial/guide/howto? I've found guides for *curses but not term*.
P.P.S. It seems ubuntu comes with libncurses5 but not libncurses5-dev. Does this mean, I can run compiled programs which depend on ncurses but cannot compile programs that need the ncurses library? Thanks again.

---

### Post by escapee on 2009-07-02
Nowadays ncurses is pretty much the de facto standard, I recommend using that.  There is also a Python wrapper and I *think* a Ruby wrapper for ncurses if you didn't want to use C (not sure which language you want, but assuming C).

---

### Post by pbrane on 2009-07-02
You can install libncurses5-dev from the repos.

---

### Post by ooobooontooo on 2009-07-02
Thanks for the advice. I did mean C; my mistake for not mentioning it.

---

