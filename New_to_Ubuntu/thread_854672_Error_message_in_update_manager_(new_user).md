---
title: "Error message in update manager (new user)"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Timmeh02 on 2008-07-09
Help would be appreciated with updates for Hardy Heron 8.0.4.1.  I was "trying" to follow the comprehensive multimedia & video how to and admit that I lost the plot.  I now get error messages on update manager.  I don't know how to undo anything wrong that I may have done.  Should I go back to a fresh install or something?  It's fun experimenting but I'm running into walls everywhere I go.  I tried a screne shot of the error and will try to attach it here.  Thanks, Tim

---

### Post by avtolle on 2008-07-09
From the command line, a/k/a the terminal (Applications>>Accessories>>Terminal) do ```
sudo dpkg --configure -a
```input your password when prompted, hit enter, and see if that fixes the problem.

---

### Post by Xerp on 2008-07-09
run

```
sudo dpkg --configure -a
```

manually (from Terminal).

---

