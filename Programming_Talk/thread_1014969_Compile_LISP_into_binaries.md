---
title: "Compile LISP into binaries"
date: 2008-12-18
forum: Programming Talk
---

### Post by thorN on 2008-12-18
Hi,

I'd like to compile some simple LISP code so that I can run it from the shell. What are the general steps I have to take?

I'm using SLIME in EMACS.

Thank you.
- Joe

---

### Post by CptPicard on 2008-12-18
[http://djkthx.blogspot.com/2007/10/distributing-common-lisp-code.html](http://djkthx.blogspot.com/2007/10/distributing-common-lisp-code.html)

---

### Post by Cracauer on 2008-12-18
> **thorN said:**
> Hi,

I'd like to compile some simple LISP code so that I can run it from the shell. What are the general steps I have to take?

I'm using SLIME in EMACS.

Thank you.
- Joe

What Lisp are you using, that's the question.

In SBCL:
```

(sb-ext:save-lisp-and-die "myapp-executable" :executable t :purify t)

```

---

### Post by LinuxGuy1234 on 2008-12-19
> **Cracauer said:**
> What Lisp are you using, that's the question.

In SBCL:
```

(sb-ext:save-lisp-and-die "myapp-executable" :executable t :purify t)

```

He's using the Lisp implementation in Emacs with the SLIME plug-in, Cracauer.

---

