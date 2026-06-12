---
title: "How to get root access from a gui?"
date: 2009-02-06
forum: Programming Talk
---

### Post by christoforever on 2009-02-06
So I'm writing a java app to (rid some personal annoyances)/(set some personal variables) on some things in ubuntu that either frustrate me or simply I want set to something else...either way.. what I need to do is get root privileges to do some of these things. The idea is to pop up gnome's password screen, like if you were to open synaptic, and ask for the users root password before continuing with the program. I'm not entirely sure on how to do this, so any ideas?

Sincerely,
Christopher Dancy

---

### Post by Tibuda on 2009-02-06
gksudo

---

### Post by SuperSonic4 on 2009-02-06
```
gksudo <command>
``` or ```
sudo command
``` 

The latter would be for a terminal script

---

### Post by christoforever on 2009-02-06
yup that worked. Thanks guys.

---

