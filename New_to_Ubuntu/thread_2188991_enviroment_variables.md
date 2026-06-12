---
title: "enviroment variables"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by mikel2 on 2013-11-20
im very confused about enviroment variables there is shell variables enviroment variables and modified enviroments.... pls i need example of what unique in any of those

---

### Post by Lars Noodén on 2013-11-20
You can see what is in use in your current shell using *set*.

```

set | less

```

---

### Post by Impavidus on 2013-11-20
Shell variables just exist in the shell. They are commonly used in shell scripts. Environment variables are inherited by the process started by any process where they already exist. If an environment variable exists in your shell, it's also known to the programs you start from that shell. You usually define them in .bashrc or a similar file.

---

