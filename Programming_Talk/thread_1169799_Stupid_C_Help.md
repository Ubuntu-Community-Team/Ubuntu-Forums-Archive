---
title: "Stupid C Help"
date: 2009-05-25
forum: Programming Talk
---

### Post by Syndacate on 2009-05-25
Hey,

I took some C in school and am trying to follow some of the kernel source (I know it's not exactly the simplest project, and this probably won't help me much, but when I open random files in the source they all have variables 'n such that I haven't seen yet - and I don't feel like chasing all the #includes).  

I know this is a stupid question, but the way I see it, the kernel, at heart, in the end, is simply a big C program, right?  If so, it should have a main method, right?  Which file is this method in?

Or is it so much lower level that it doesn't have it?

I've did programming in ASM and I'm not entirely sure how you can execute a C program, but I'm sure you can.

Can anybody provide more insight on this?  I realize this is probably a bit off topic, but I can't feel a more relative forum and I can't figure it out :(.

Any help is greatly appreciated.

---

### Post by stefangr1 on 2009-05-25
Have you already installed the manpages? They have a lot of explanation on kernel functions and it's use.

---

### Post by soltanis on 2009-05-25
Uh yeah, sort of. It doesn't have a main() function per se; what actually happens is the kernel is "run" by the bootloader (probably GRUB, or on older systems LILO). The bootloader is loaded from the disk into memory by the BIOS of your computer; it then reads some files on your disk (the menu.lst files), and based on some logic (or user input) decides to load a "kernel image", which is a compressed object file representation of a kernel loaded into memory.

As its final act, the bootloader picks an address in that loaded kernel image to jump to, and points the Instruction Pointer to that address. This is the entry point to the kernel.

If you are curious about how the kernel starts, you should take a look at some GRUB code (a lot of what I described is in asm, though).

---

### Post by Syndacate on 2009-05-25
> **soltanis said:**
> Uh yeah, sort of. It doesn't have a main() function per se; what actually happens is the kernel is "run" by the bootloader (probably GRUB, or on older systems LILO). The bootloader is loaded from the disk into memory by the BIOS of your computer; it then reads some files on your disk (the menu.lst files), and based on some logic (or user input) decides to load a "kernel image", which is a compressed object file representation of a kernel loaded into memory.

As its final act, the bootloader picks an address in that loaded kernel image to jump to, and points the Instruction Pointer to that address. This is the entry point to the kernel.

If you are curious about how the kernel starts, you should take a look at some GRUB code (a lot of what I described is in asm, though).

Ah, okay, I'll check out GRUB, I don't mind reading asm code.  That makes sense, though.  Thank you.

[quote=stefangr1]Have you already installed the manpages? They have a lot of explanation on kernel functions and it's use.[/quote]

No, I haven't, I didn't think the kernel's man pages would have what I was looking for.  I'll look at them.

Thank you all.

/thread

---

