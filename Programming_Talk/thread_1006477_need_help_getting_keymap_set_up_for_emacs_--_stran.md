---
title: "need help getting keymap set up for emacs -- strange syntax error"
date: 2008-12-09
forum: Programming Talk
---

### Post by laptoplinux on 2008-12-09
I'm trying to get a keymap set up on a remote machine so that I can get nice things like shift+home, shift+end highlighting working over a remote terminal.  I found this on the EmacsWiki page:

```

 keycode 103 = Up
  Shift keycode 103 = F49
 keycode 108 = Down
  Shift keycode 108 = F50
 keycode 106 = Right
  Shift keycode 106 = F51
  Control keycode 106 = F53
  Control Shift keycode 106 = F55
 keycode 105 = Left
  Shift keycode 105 = F52
  Control keycode 105 = F54
  Control Shift keycode 105 = F56
 keycode 102 = Find
  Shift keycode 102 = F57
  Control keycode 102 = F59
  Control Shift keycode 102 = F61
 keycode 107 = Select
  Shift keycode 107 = F58
  Control keycode 107 = F60
  Control Shift keycode 107 = F62
 string F49 = "\033O2A"
 string F50 = "\033O2B"
 string F51 = "\033O2C"
 string F52 = "\033O2D"
 string F53 = "\033O5C"
 string F54 = "\033O5D"
 string F55 = "\033O6C"
 string F56 = "\033O6D"
 string F57 = "\033O2H"
 string F58 = "\033O2F"
 string F59 = "\033O5H"
 string F60 = "\033O5F"
 string F61 = "\033O6H"
 string F62 = "\033O6F"

```

Yet, when I try to load the keymap, I get the following error:

```

.keymap:1: syntax error
syntax error in map file
key bindings not changed

```

Does anyone know what the problem might be?  If that isn't the correct syntax, then what is?

(This isn't strictly a programming question, but hopefully some programmers have tried to do something similar before to get their editors set up and can help)

---

