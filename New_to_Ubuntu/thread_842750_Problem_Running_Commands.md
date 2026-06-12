---
title: "Problem Running Commands"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by JPtux on 2008-06-27
Hello, I'm relatively new to Linux, therefore I'm not really confident to log on as super user. Every time I type a sudo apt-get command the terminal gives me this error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```
Whenever I run dkpg --configure -a, the terminal gives me this output:
```
dpkg: requested operation requires superuser privilege

```
Is this the only way to fix this problem? How do you log on as super user?

---

### Post by wrtpeeps on 2008-06-27
TO run the command as superuser: 

```
sudo dpkg --configure -a
```

---

### Post by ConMan318 on 2008-06-27
Typing
```

sudo "command name here"

```

executes the command as superuser.  So you could try running:
```

sudo dpkg --configure -a

```

---

### Post by JPtux on 2008-06-27
Thanks! Sorry for my ignorance. :(

---

