---
title: "How to create a backup in github that i can run in any ubuntu"
date: 2020-04-02
forum: New to Ubuntu
---

### Post by napa2 on 2020-04-02
I want to back up the packages I installed in my system in the github in such way that I can restore the backup in any ubuntu based operating system.
It is like maybe making a script that will automatically install all the software I installed and backed up earlier from my parent ubuntu Pc.

Any idea how can I do that?

Thank you.

---

### Post by kevdog on 2020-04-02
@napa2

You mean like keep a list of installed packages with apt?  This has been discussed here many times I believe -- just have to search for it.

---

### Post by TheFu on 2020-04-02
```
sudo apt-mark showmanual
sudo apt-mark showauto
```

Probably only want the manually installed list, since dependencies can change.

---

