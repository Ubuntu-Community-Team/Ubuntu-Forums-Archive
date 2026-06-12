---
title: "[Scheme Lisp] Lost in the implementation woods!"
date: 2008-08-16
forum: Programming Talk
---

### Post by nvteighen on 2008-08-16
Hi,
I've been looking at some Scheme Lisp interpreters... and I'm completely lost. I know just the very basics of the language, thanks to DrScheme pure-standard mode, but for some reason, I can't make the extensions work in it... And those interpreters that can use the extensions (usually SLIB) include them without asking if I really want them...

I want to learn the mechanics of the language using standard features and then jump into the non-standard (as I usually do with any standardized programming language). So, is there an interpreter that starts being pure R5RS Standard Scheme and to which I easily can latter add modules and implementation-specific stuff? 

Here's a list of what I tried:
PLT Scheme: DrScheme, MzScheme
MIT/GNU Scheme
Scheme48
SCM
Gambit

Thanks!

---

### Post by LaRoza on 2008-08-16
mit-scheme I think is the most used.

---

### Post by Kadrus on 2008-08-16
yeah,mit-scheme and mzscheme are the most used.

---

### Post by nvteighen on 2008-08-16
Well, I currently use mzscheme. But for some reason, I can't make it work quite properly. For example, the mzc compiler returns me a shared library by default, not an executable... and if I want to have a bytecode executable (which should be the default), I get errors.

mit-scheme has that weird bug regarding memory allocation and AppArmor. But I'm giving it a try.

BTW, the language is great... Well, it's not quite a language, more like a meta-language. It's an interesting test-bed for some linguistic experiments.

Thanks!

---

### Post by LaRoza on 2008-08-16
> **nvteighen said:**
> It's an interesting test-bed for some linguistic experiments.


Yes it is. 

I use scheme48 when I use Scheme, but I don't do much with Scheme.

---

### Post by nvteighen on 2008-08-16
Well, this thread is solved. I'll stick with those two for a while.

Thanks to you!

---

