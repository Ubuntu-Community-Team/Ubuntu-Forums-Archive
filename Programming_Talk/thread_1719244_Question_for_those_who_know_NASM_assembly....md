---
title: "Question for those who know NASM assembly..."
date: 2011-04-01
forum: Programming Talk
---

### Post by ownaginatious on 2011-04-01
So I have a class on Intel x86 assembly using NASM, and I'm wondering why this is a bad idea.

Say I have a function that I know is going to be using two 1 byte variables, and a 4 byte variable.

I make space for it on my stack like this:

```

enter 6,0
; [ebp - 6] is space for my first byte variable
; [ebp - 5] is space for my second byte variable
; [ebp - 4] is space for my four byte variable

```

My professor says I should be doing this:

```

enter 12,0
; [ebp - 12] is space for my first byte variable
; [ebp - 8] is space for my second byte variable
; [ebp - 4] is space for my four byte variable

```

I figured that it's better to try and save space... but my professor says this is a **very bad** idea.

Can anyone experts out there explain why? My professors explanation was more or less "just don't do it".

Thanks.

---

### Post by lloyd_b on 2011-04-01
It's a matter of "alignment". In this case, your prof wants everything aligned to a 32 bit boundary (i.e. all data addresses will be an even multiple of 4), which is reasonable for almost all modern processors.

Note that some processors flat out won't work if data isn't aligned to a particular boundary - they'll throw an exception if you try it.  On others, accessing data that isn't aligned will still work, but can incur a substantial performance penalty.

So it's a good idea to always align data to the proper boundary for the processor you are programming for.  Compilers for higher-level languages typically handle this for you, but when working at the assembly level you have to be aware of such issues and handle the alignment yourself.

Lloyd B.

---

### Post by jwbrase on 2011-04-02
For more information see: [http://en.wikipedia.org/wiki/Data_alignment](http://en.wikipedia.org/wiki/Data_alignment)

---

