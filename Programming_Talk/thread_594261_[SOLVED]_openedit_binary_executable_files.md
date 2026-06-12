---
title: "[SOLVED] open/edit binary executable files?"
date: 2007-10-27
forum: Programming Talk
---

### Post by thelocust on 2007-10-27
I want to see and maybe edit some executable files like /sbin/fsck and others but when I open them with kate it says that it is a binary file and not to edit it and then it opens and most of it is gibberish. Do I need a special program? Thanks.

---

### Post by happysmileman on 2007-10-27
> **thelocust said:**
> I want to see and maybe edit some executable files like /sbin/fsck and others but when I open them with kate it says that it is a binary file and not to edit it and then it opens and most of it is gibberish. Do I need a special program? Thanks.

```
objdump -d /sbin/fsck
```

Will disassemble the program into AT&T syntax assembler code, but that'd be very hard to edit or even read, other than that you can't do it, though if the file is open source you can get the code in the language it was written in (much easier) and then change, build and install it yourself

---

### Post by LaRoza on 2007-10-27
Use a hex editor

---

### Post by pmasiar on 2007-10-29
I use midnight commander for these kind of low-level tasks. Among other tools, is has also hex editor.

---

### Post by Wybiral on 2007-10-29
ghex

---

