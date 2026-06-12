---
title: "LD Create symbols during link"
date: 2009-10-07
forum: Programming Talk
---

### Post by Jeremywilms on 2009-10-07
I was wondering how how can create symbols in the linking process of a project's object files.

Ie, in head.h I may have

extern void* g_pProjEnd;

And when using the link command(pseudo)
ld myFile.c -o out -DEFINE_SYMBOL g_pProjEnd AtTheEndOfTheLinkedFile

-DEFINE_SYMBOL symbolName value(not a valid command btw)
Where AtTheEndOfTheLinkedFile is a pointer to the end of the linked file.

I'm looking for something like that, as I am writing a kernel and I need to pass to the kernel it's size, and where it is loaded in memory(which is defined in the shell script) so it knows which regions to protect from memory allocation. Not sure how I can do this. Another problem is that after the file is linked, I use the objcpy command to strip the file of unneeded sections, resulting in a smaller size then it was when linked.

---

