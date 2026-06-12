---
title: "dh_make without prompt"
date: 2011-06-01
forum: Packaging and Compiling Programs
---

### Post by scott-ian on 2011-06-01
I am working on a program to make the creation of .deb packages easier.  The dh_make command must be run automaticly by it, but it prompts for you to hit enter to  accept the settings.  How can I make it automatic?  I am using the following command:
```
dh_make -e $email -f ../orig.tar.gz -$type
```

---

### Post by gmargo on 2011-06-02
Typically one would use the **yes(1)** command through a pipe to satisfy annoying prompts like that.
```

yes | dh_make....

```

---

### Post by scott-ian on 2011-06-02
Thanks, that solved my problem.

---

