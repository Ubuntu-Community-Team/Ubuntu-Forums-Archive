---
title: "selection search with xsel"
date: 2007-08-12
forum: Programming Talk
---

### Post by adam_r on 2007-08-12
hi, i've tried to make my mouse search key search the selected mouse text when i press it, anyway i made this script:

#!/bin/bash
firefox -search `xsel -p -o`

which works great.. for one word only:

firefox -search bla (works)
firefox -search 'bla bla' (works)
firefox -search bla bla (DONT work)

all i need is if somebody knows how do i add the ' ' to the script?

thanks

[Solved]: Got it with "  "  !!! :)

---

### Post by light50 on 2008-12-30
[http://ubuntuforums.org/showthread.php?p=4551978]("http://ubuntuforums.org/showthread.php?p=4551978")

---

