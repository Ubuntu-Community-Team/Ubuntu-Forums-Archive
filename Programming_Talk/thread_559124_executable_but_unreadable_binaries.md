---
title: "executable but unreadable binaries"
date: 2007-09-24
forum: Programming Talk
---

### Post by rut216 on 2007-09-24
Is there a known method to extract the source or machine code of a binary which has execute permissions but no read permissions?

---

### Post by Carl Hamlin on 2007-09-25
> **rut216 said:**
> Is there a known method to extract the source or machine code of a binary which has execute permissions but no read permissions?

Yessir. Get read permissions.

---

### Post by lisati on 2007-09-25
> **Carl Hamlin said:**
> Yessir. Get read permissions.
But would it make sense without major reverse engineering efforts?

---

### Post by Carl Hamlin on 2007-09-25
> **lisati said:**
> But would it make sense without major reverse engineering efforts?

Depends on one's knowledge of assembly language. However, the OP asked about extraction of machine code:

---

### Post by lisati on 2007-09-25
If I were design a tool to recover source code from an executable binary file (I've seen it done for assembler programs under MS-DOS but haven't tried it myself, I don't have the patience or skills) I imagine that it would be much easier to have the output in assembly language than in a HLL such as C/C++

---

### Post by rut216 on 2007-09-25
Im just curious if this is possible and im not so clear on the benefits of setting only execute permissions on binary programs. During execution the kernel loads the instructions into memory, so would somehow causing a memory dump while the program is in memory allow one to examine the contents of the program in question?

---

### Post by lisati on 2007-09-25
> **rut216 said:**
> Im just curious if this is possible and im not so clear on the benefits of setting only execute permissions on binary programs. During execution the kernel loads the instructions into memory, so would somehow causing a memory dump while the program is in memory allow one to examine the contents of the program in question?

If you know what you're doing, you might be able to browse it and learn something. For myself, I'm usually content to run the program, and try tweaking its settings if something goes wrong.

---

### Post by Lux Perpetua on 2007-09-26
> **rut216 said:**
> Im just curious if this is possible and im not so clear on the benefits of setting only execute permissions on binary programs. During execution the kernel loads the instructions into memory, so would somehow causing a memory dump while the program is in memory allow one to examine the contents of the program in question?I think so, but the author of a program can limit the size of core dumps, even to zero, so this type of attack can be prevented.

---

