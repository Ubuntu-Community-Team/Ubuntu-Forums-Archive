---
title: "emacs and terminal help"
date: 2013-03-12
forum: Programming Talk
---

### Post by pramitkumarpal on 2013-03-12
i have created hw.java file using vi.
opened it using emacs in text mode in terminal.edited something and quit it using C-x-C-c(without saving).
emacs asked me that it has some modified buffers ..so ignored that and quit emacs . 
now i have file #hw.java# in the same directory.
how to delete this file using rm command as i am unable to delete the file from terminal using rm -f #hw.java#(did not help).


Help

---

### Post by r-senior on 2013-03-12
Just put quotes around it (single or double does not matter in this case) so that the '#' character is not interpreted by the shell:

```
rm '#hw.java#'
```

---

### Post by pramitkumarpal on 2013-03-13
later i experimented and found out a new command that worked 
the code rm ./#hw.java#

---

