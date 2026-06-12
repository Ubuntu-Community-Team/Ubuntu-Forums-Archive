---
title: "CMD for Ubuntu Lucid"
date: 2010-05-07
forum: Programming Talk
---

### Post by Hosmion on 2010-05-07
Hello everyone.  I am coding a couple of batch files to make it easier to start up programs but I can't find a program like cmd.exe for Windows that executes the command.  Does anyone have any things similar to it so I can execute my commands? 

Thanks, 
~ToM
Back on Linux :)

---

### Post by Tony Flury on 2010-05-07
what you are looking for is the Bash shell.

add this line :
```

#! /bin/sh

```

at the top of your "batch" file (they are called scripts in Linux), and then do 
```

chmod +x <filename>

```

your file is now automatically be interpreted correctly by the right shell, and is executable - so you can run it from your command line :

```

./<filename>

```
If the file is in your currently directory

---

### Post by MadCow108 on 2010-05-07
wine has a cmd which should be able to execute many bat files (~/.win/drive_c/windows/system32/cmd.exe)

but if you are writing new ones stick to the by far more versatile linux or posix shells.
ubuntu comes with bash and dash by default.
using bash is recommended (/bin/bash) as it has more features and it is very widely used.

if you need better portability to other unix system use dash (/bin/sh) as what runs in dash runs on every posix conforming shell (but that does not include window's cmd).

you'll find many many tutorials with google

---

### Post by Lux Perpetua on 2010-05-07
> **Hosmion said:**
> Hello everyone.  I am coding a couple of batch files to make it easier to start up programs but I can't find a program like cmd.exe for Windows that executes the command.  Does anyone have any things similar to it so I can execute my commands? 

Thanks, 
~ToM
Back on Linux :)Welcome to Linux! :-) Indeed, the shell (the Linux/Unix equivalent of Windows' command prompt) is a much more essential part of Linux than the fancy GUI.

---

