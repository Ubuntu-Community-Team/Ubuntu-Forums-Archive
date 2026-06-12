---
title: "[Common Lisp] Creating modules"
date: 2009-11-20
forum: Programming Talk
---

### Post by nvteighen on 2009-11-20
Hi! I hope there's somebody here that can help me with a little deployment question I have about Common Lisp. For your interest, I use SBCL, but I think this is a standard-defined thing.

I don't quite understand how the usage of packages can lead to create reusable libraries or "modules" if one's forced to do the annoying technique of having a load.lisp file that preloads everything so that if I happen to compile, macros are correctly expanded and the FASL files include the already macroexpanded code.

Isn't there a way to do something like Python's import or PLT-Scheme's require? Something that makes the package not only just a namespace-interface, but also a way to load it in a sane way without recurring to a interpreter trick (because that's what you do when creating load.lisp)...

Thanks!

---

### Post by CptPicard on 2009-11-20
Why aren't you on #ubuntu-programming asking lnostdal already? :)

Hmm anyway... haven't really thought of that properly... you mean "systems" and (require 'something) don't work for that?

---

### Post by mmix on 2009-11-21
you mean asdf?

[http://www.cliki.net/asdf](http://www.cliki.net/asdf)

---

### Post by nvteighen on 2009-11-21
What I **exactly** want is something that, during **compiling**, resolves all dependencies exactly as load does during interpreting in order to have all macros and all references resolved in the resulting FASL file. load, when compiling, has no effect and all references become stubs, leading to an inconvenient "dynamic linked" code where it wasn't intended.

ASDF seems to help on this... I haven't read on systems, but it could be what I want. I'll check it out.

---

### Post by maximinus_uk on 2009-11-21
Whilst not being terribly helpful, probably posting this to comp.lang.lisp rather than the ubuntu forums might help.

Like I said, not terribly helpful, just got to know your target audience ;)

---

### Post by nvteighen on 2009-11-21
> **maximinus_uk said:**
> Whilst not being terribly helpful, probably posting this to comp.lang.lisp rather than the ubuntu forums might help.

Like I said, not terribly helpful, just got to know your target audience ;)

Or asking at #lisp... :p

---

