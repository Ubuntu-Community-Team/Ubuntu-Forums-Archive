---
title: "Viewing LF CR in Text Editor"
date: 2009-10-07
forum: Programming Talk
---

### Post by moffa on 2009-10-07
Hello,

I was wondering if were possible to turn on an option in nano/pico or less/more to view newline/LF/CR characters as a symbol.

Edit: I am using putty to connect to the server from a Windows machine.

Thanks,

---

### Post by unutbu on 2009-10-07
The command
```

cat -A file
```

will spit out the contents of file with a $ displayed for each LF.
If file has DOS-style CR/LF pairs, then ^M$ is displayed.

---

### Post by jpkotta on 2009-10-07
[QUOTE=man nano]
       -N (--noconvert)
              Disable automatic conversion of files from DOS/Mac format.
[/QUOTE]

Works like unutbu's solution, but in nano.

---

