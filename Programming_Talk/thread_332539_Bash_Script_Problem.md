---
title: "Bash Script Problem"
date: 2007-01-06
forum: Programming Talk
---

### Post by petros-nu2lnx on 2007-01-06
I'm tryin' to run in terminal a bash script which starts with this
#!/bin/sh 
and i get the message
bash: /bin/sh^M: bad interpreter: No such file or directory.
Does someone know what's wrong?Also what is the "^M"?

---

### Post by ghostdog74 on 2007-01-06
you can try

```

dos2unix yourscript.sh yourscript.sh 

```

the ^M is control character for Enter key.

---

### Post by petros-nu2lnx on 2007-01-06
it didn't work.it said command not found.Is it maybe necessary any package ?

---

### Post by ghostdog74 on 2007-01-06
can you try any of these:

```

which sh

```

```

ls -l /bin/sh

```

also, check the permissions of the file.

---

### Post by po0f on 2007-01-06
petros-nu2lnx,

Did you mean to say that the dos2unix command wasn't found?  It's part of the [tofrodos](http://packages.ubuntu.com/edgy/utils/tofrodos) package.  Install it, run the command ghostdog74 posted above and you should be fine.

Oh yeah, and stop downloading your scripts onto a Windows box to transfer them to your Linux box.  ;)

---

### Post by gpolo on 2007-01-06
just use sed,

sed -e 's/[\r\n]//g' ms_script.sh > unix_script.sh

---

