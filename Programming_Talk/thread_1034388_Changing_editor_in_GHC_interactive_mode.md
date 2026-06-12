---
title: "Changing editor in GHC interactive mode"
date: 2009-01-08
forum: Programming Talk
---

### Post by meson2439 on 2009-01-08
I'm a beginner in Haskell programming and this is my first functional programming experience. Using the interactive mode in ghc I would like to know how to edit my .hs files using a preferred editor (nano in this case). I tried to do this 

```
Prelude> :!nano
Received SIGHUP or SIGTERM
Prelude> :set editor "nano %s"
Prelude> :edit jhah.hs
/bin/sh: nano %s: not found
Prelude> :set editor="nano %s"
unrecognised flags: editor=nano %s
Prelude> :set editor="/bin/nano %s"
unrecognised flags: editor=/bin/nano %s
Prelude> :set editor="/bin/nano+%s"
unrecognised flags: editor=/bin/nano+%s
Prelude> :set editor="nano"
unrecognised flags: editor=nano
Prelude> :set editor "nano"
Prelude> :edit ads.hs
Received SIGHUP or SIGTERM
```

Can someone tell me what I'm doing wrong. I also won't mind using emacs but I'm not yet acquainted with vi or vim. Thanks.

---

### Post by Reiger on 2009-01-08
Hmm odd. Anyway the :set editor command works fine with vim, kate and gedit...

---

### Post by meson2439 on 2009-01-08
Thanks. I also found out that setting the editor to emacs also work. I also found that setting the editor to nano also fails in Octave. Does anybody knows why?

---

### Post by jpkotta on 2009-01-09
nano is clearly doing something weird.  It seems to work if you start a terminal running nano.
```
:!xterm -e nano
```

---

### Post by jpkotta on 2009-01-09
In octave, set the mode to async (-nw emacs doesn't work without that either).  This is basically like appending a '&' to the editor command.

```
edit mode async
```

---

