---
title: "Multiple input for exec in bourne shell script -How?"
date: 2008-03-09
forum: Programming Talk
---

### Post by canakas on 2008-03-09
Dear all,

I want to execute a command I use in terminal from a bourne shell script, preferrably closing the shell as the other program starts.

I can run this from the command line:

GTK2_RC_FILES=/home/username/.themes/theme1/gtk-2.0/gtkrc programtoexecute

but if I stick this behind exec in a #!/bin/sh-script like this

exec GTK2_RC_FILES=/home/username/.themes/theme1/gtk-2.0/gtkrc programtoexecute

it assumes the arguments as ran in /home/username/ and I get this error message:

./myscript.sh: line 4: /home/username/GTK2_RC_FILES=/home/username/.themes/theme1/gtk-2.0/gtkrc programtoexecute: No such file or directory


How to I make it not consider the GTK-argument as part of a path?

thanks a bunch
canakas

---

### Post by ruy_lopez on 2008-03-09
Have you tried using backquotes ``.

ie
```

#!/bin/sh

`GTK2_RC_FILES=/home/username/.themes/theme1/gtk-2.0/gtkrc programtoexecute`

```

---

### Post by canakas on 2008-03-09
Ah. Thanks very much
I was trying before with ' and '' and " but not `

:lolflag:

thanks again

---

