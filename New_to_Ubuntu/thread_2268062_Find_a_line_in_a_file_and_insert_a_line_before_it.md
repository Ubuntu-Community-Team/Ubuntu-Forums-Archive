---
title: "Find a line in a file and insert a line before it"
date: 2015-03-05
forum: New to Ubuntu
---

### Post by Delco on 2015-03-05
How would I find a line in a file using a bash script and then insert a pre-prepared line before it? The file is rc.local in and I want to insert commands before the exit0 line. Is there a way to do this with regex?

---

### Post by steeldriver on 2015-03-05
You should be able to use sed's insert (i) command

```

sed '/^exit 0/ i\
some stuff\
more stuff
' /etc/rc.local

```

You will need to use the -i (in place) switch as well to actually modify the file on the fly, e.g.

```

sed **-i.bak** '/^exit 0/ i\
some stuff\
more stuff
' /etc/rc.local

```

---

### Post by ian-weisser on 2015-03-05
I think that writing a program to edit /etc/rc.local usually isn't the best solution.
If you are editing once, you don't need the program.
If you are editing repeatedly or programmatically, you should use etc/rc*.d/ or Upstart (12.04/14.04) or systemd(15.04+) to create/remove/start/stop init jobs.

---

### Post by Delco on 2015-03-06
@steel driver thanks for the code samples, they were helpful to get me started.
@ian-weisser - I will look into those, thanks.

---

