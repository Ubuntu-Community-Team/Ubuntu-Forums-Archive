---
title: "How to distinguish nix from windows?"
date: 2008-06-05
forum: Programming Talk
---

### Post by shoaibi on 2008-06-05
I am connected to a remote system using ssh...
how can i tell if that is a windows based system or nix by running some command?
in other words:

Using a terminal, is there a way I can distinguish from the output of the command that whether it's a nix system or windows?

oh and dont tell me its uname, coz uname gives different output on unices and linux.. :P :D

thanks for reading the post..

---

### Post by az on 2008-06-05
> **shoaibi said:**
> I am connected to a remote system using ssh...
how can i tell if that is a windows based system or nix by running some command?
in other words:

Using a terminal, is there a way I can distinguish from the output of the command that whether it's a nix system or windows?

oh and dont tell me its uname, coz uname gives different output on unices and linux.. :P :D

thanks for reading the post..

uname -a

---

### Post by Martin Witte on 2008-06-05
I would go for an approach where you test the result of command 'uname -a', exists on Unix, not on windows , then test for the result of command 'ver' - this exists on Windows, not on Unix

---

### Post by slavik on 2008-06-05
if you can, get to the root of the file system and look at the structure.

---

### Post by rikxik on 2008-06-06
Use echo - same command for both OS and check the output to decide.

On Windows:
```

C:\>echo %OS%
Windows_NT

```

On Unix/Linux:
```

$ echo %OS%
%OS%

```

HTH

---

### Post by geirha on 2008-06-06
```
import sys
sys.platform == 'win32'

```

---

