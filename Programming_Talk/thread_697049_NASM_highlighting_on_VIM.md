---
title: "NASM highlighting on VIM"
date: 2008-02-14
forum: Programming Talk
---

### Post by rmx on 2008-02-14
Hello 

I have installed vim-full on  7.10.

I uncomment the line syntax on and it is working.

However, the highlighting is not set to NASM.

Anyone know how to set?

thanks

rmx

---

### Post by lloyd_b on 2008-02-14
> **rmx said:**
> Hello 

I have installed vim-full on  7.10.

I uncomment the line syntax on and it is working.

However, the highlighting is not set to NASM.

Anyone know how to set?

thanks

rmx

Unfortunately, it looks like vim's file type detector won't automatically select the NASM syntax regardless of file extension.  You can probably change this by copying the file "nasm.vim" to "asm.vim" in the directory "/usr/share/vim/vim70/syntax" (assuming that the files have a ".asm" extension).

You can also manually set it by using the following command:
```
:set syn=nasm
```
but it would be nicer to have it done automagically...

Lloyd B

---

