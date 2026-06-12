---
title: "Re: make: *** No rule to make target `install'.  Stop."
date: 2013-03-01
forum: Programming Talk
---

### Post by checoimg on 2013-03-01
When I make "sudo checkinstall" I get the same error.

---

### Post by matt_symes on 2013-03-01
@cheoimg

Please do not resurrect a thread from late 2008.

Start a new thread and reference the old thread like so.

Reference from old thread.

[http://ubuntuforums.org/showthread.php?t=995168](http://ubuntuforums.org/showthread.php?t=995168)

---

### Post by Bachstelze on 2013-03-01
> **checoimg said:**
> When I make "sudo checkinstall" I get the same error.

checkinstall runs *make install* "behind the scenes", but it seems that whatever you are trying to install is not supposed to be installed that way, so chances are checkinstall will not work on it.

---

