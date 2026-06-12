---
title: "[SOLVED] Default display manager isn't set"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by suprfish on 2008-08-12
When I boot up my computer it finishes the boot splash but then drops a terminal for me to log into. I can start GDM by cd-ing to /etc/init.d/ and then "sudo gdm start"; if I try to start GDM just by "sudo /etc/init.d/gdm start" it says "Not starting GDM: it is not the default display manager." I think KDM might be set to default or it might not be set at all, I dunno. How can I set it?

---

### Post by asmoore82 on 2008-08-12
run this

```
cat /etc/X11/default-display-manager
```

mine looks like this:
```
~$ cat /etc/X11/default-display-manager 
/usr/sbin/gdm
```

you could set yours back to gdm like this:
```
which gdm | sudo tee /etc/X11/default-display-manager
```

---

### Post by suprfish on 2008-08-12
Thanks, it was KDM.

---

