---
title: "bash variabel outside the script"
date: 2007-03-06
forum: Programming Talk
---

### Post by Onbeperkt on 2007-03-06
Hi guys,

I have a script that keep track of line counts in a certain file whenever i login to a terminal. The count is stored in a file with other data from the script.

i rather don't want this line count between my data. Is their a way so i could make an variabel on the system so i don't have to write it to a file.


kind regards,

---

### Post by Ramses de Norre on 2007-03-06
You can export it, it will then be available to all subshells of the one the script runs in.
You can't make a variable accessible to supershells though...
To export a variable (eg var) you do:```
export var
```

---

