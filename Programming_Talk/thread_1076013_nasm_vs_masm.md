---
title: "nasm vs masm"
date: 2009-02-20
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-02-20
I have read many tutorials on the usage of nasm in comparison to masm.

But i have one problem. Is nasm always 32 bit compatable. Is there any directive that makes it work like an 8086 only. Meaning i will have only ax and not eax etc.

I have never found a tutorial on that, but non the less when i trued replacing eax with ax in some instructions it worked.

---

### Post by Zugzwang on 2009-02-21
See here:

[http://www.nasm.us/doc/nasmdoc6.html#section-6.1.1](http://www.nasm.us/doc/nasmdoc6.html#section-6.1.1)

Try "USE16" to switch to 16-bit mode. See section 6.8 for restricting the available commands to those available for your machine.

---

### Post by Frank Kotler on 2009-02-21
To expand on what Zugzwang said... Nasm defaults to 32-bit code in "-f elf" (aka "-f elf32") output mode (it differs in different output formats). You could use use "use16" or "bits 16" in the middle of ELF code, but you almost certainly don't want to. You can use ax, and other 16-bit registers freely. This will require an "operand size override prefix" - 0x66 - which Nasm will provide (so you probably don't want to use 16-bit registers unless you need 'em - it will not be faster!). You can use 32-bit registers in 16-bit code, too - sometimes useful in DOS... not-so-much in Linux :)

Best,
Frank

---

