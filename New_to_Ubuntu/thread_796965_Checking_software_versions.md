---
title: "Checking software versions"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by jerzydirtracer on 2008-05-16
Hello, how do I check the versions of installed applications?

Thanks

---

### Post by amingv on 2008-05-16
Help > About <program>

Or in the console:
```
<program> --version #in some it could be -v or -V
```

---

### Post by jerzydirtracer on 2008-05-16
Thanks

---

### Post by forrestcupp on 2008-05-16
You can also look it up in Synaptic where it gives the version.

---

### Post by PinkFloyd102489 on 2008-05-16
And also check inside of the program if it is a GUI and it has an About section.

---

### Post by sdennie on 2008-05-16
For applications that don't support -v or --version, you can also get this information out of dpkg.  For example, to figure out what package the file /usr/bin/firefox belongs to you can say:

```

dpkg -l `dpkg -S /usr/bin/firefox | cut -f1 -d":"`

```

---

