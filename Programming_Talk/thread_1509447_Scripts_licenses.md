---
title: "Scripts licenses"
date: 2010-06-14
forum: Programming Talk
---

### Post by j_arquimbau on 2010-06-14
Is it neccesary to license a bash script? I mean, as it's just a sequence of commands to use some programs, would it make any sense to license it? What about the copyright?
In case I had to, how am I suposed to do it? Including the text of the license in the script, linking it to a spare document or mentioning people where to read the license (which would be GPL)?
Thanks for the answers!

---

### Post by nvteighen on 2010-06-14
> **j_arquimbau said:**
> Is it neccesary to license a bash script? I mean, as it's just a sequence of commands to use some programs, would it make any sense to license it? What about the copyright?
In case I had to, how am I suposed to do it? Including the text of the license in the script, linking it to a spare document or mentioning people where to read the license (which would be GPL)?
Thanks for the answers!

In most parts of the world, full copyright is automatically assigned to the author. So, even by not placing anything, your script is licensed according to what Copyright Law in your country provides as default (usually, author's exclusive rights for distribution and modification, though granting the users the right to use your work).

To license something under other terms than the default ones derived from Law, you usually just have to tell people what are your terms in some reasonable way. The common way is to place a notice in the script as a comment telling who the author is, year(s) of publication and then, some notice about what license you're using and where to find it or, if small enough (like BSD-like licenses), the license itself.

Anyway, the FSF has a "standard" license notice that you might use for their licenses. It's not required, but people are used to it and it tells the reader fairly all he wants to know. Look at [http://www.gnu.org/licenses](http://www.gnu.org/licenses)

---

### Post by Bachstelze on 2010-06-14
> **nvteighen said:**
> 
To license something under other terms than the default ones derived from Law, you usually just have to tell people what are your terms in some reasonable way. The common way is to place a notice in the script as a comment telling who the author is, year(s) of publication and then, some notice about what license you're using and where to find it or, if small enough (like BSD-like licenses), the license itself.

No. The *full text* of the license must *always* be distributed alongside the source code. Otherwise, the license is void. A link (for example an URL) is not sufficient, because if the link becomes broken, a person who receives the code would have no way to know what he may and may not do with it.

---

### Post by Zugzwang on 2010-06-14
> **Bachstelze said:**
> Otherwise, the license is void.

It appears to me as if this is really a detail that depends on the laws in the respective countries.

Even if the license is void, what would it mean? That everyone can do what with the work what she/he wants? Probably not. It appears to be more logical that then either:
[LIST]
[*]the "default" license according to the law is used, which as nvteighen already said, is often quite restrictive
[*]the user may only perform actions with the work that she/he can be sure of to be allowed
[*]the user must request (and obtain) a copy of the license before she/he is allowed to do anything for which the allowance is not obvious from the context
[/LIST]

---

### Post by Bachstelze on 2010-06-14
Yes, what I meant by "the license is void" was that the terms of the license do not applay, so that leaves us with the "default" copyright terms (remember that the license is not a substitute for copyright law, it only grants additional rights).

Of course, the user can request a copy of the license, but I believe (not 100% sure) that he must obtain it from the copyright holder, not a third-party. If he is unable to do so, he is left once again with the "default".

---

### Post by juancarlospaco on 2010-06-14
**Use WTFPL**

---

### Post by soltanis on 2010-06-14
This really depends on your local copyright laws. I'm pretty sure in the United States if you want to specifically license your code you must include a notice under all your documents with a copyright notice and the full text of the license, or barring that you must distribute the document with the text of the license in a file packaged with it.

You'll notice that the GNU GPL text on most documents, for example, places a notice (a fairly long one too) at the front of code saying "if you did not receive a copy of the GPL with this code, write to...".

I personally suggest public domain'ing your code. Avoids all these "license issues." Of course, that means you forfeit copyright, but as a bonus, no one else can copyright it (it seems a fair trade to me).

To do that, you need only include a notice at the front of your document clearly stating that it is entirely in the public domain.

---

### Post by trent.josephsen on 2010-06-14
> **soltanis said:**
> I personally suggest public domain'ing your code. Avoids all these "license issues." Of course, that means you forfeit copyright, but as a bonus, no one else can copyright it (it seems a fair trade to me).

To do that, you need only include a notice at the front of your document clearly stating that it is entirely in the public domain.

Bad idea, for multiple reasons discussed ad nauseam elsewhere.  Use a permissive license if you so desire, but don't abuse the public domain to do what it was never intended to.

---

### Post by soltanis on 2010-06-14
> **trent.josephsen said:**
> Bad idea, for multiple reasons discussed ad nauseam elsewhere.  Use a permissive license if you so desire, but don't abuse the public domain to do what it was never intended to.

[QUOTE="Free Software Foundation"]
_Public Domain_
Being in the public domain is not a license; rather, it means the material is not copyrighted and no license is needed. Practically speaking, though, if a work is in the public domain, it might as well have an all-permissive non-copyleft free software license. Public domain material is compatible with the GNU GPL.
[/QUOTE]

The public domain is not "intended" to do anything. It is a legal state of non-copyright. Since programs are copyrighted (by default), placing source code in the public domain is simply disclaiming your control over it -- completely.

If you wish to assert that the public domain isn't "intended" to cover software, then by association you must also be asserting that copyright isn't "intended" to cover software either, because they're simply two states of being that source code can be in.

EDIT -- and if the OP's original point is to make a program available for anyone to use it as they see fit, without worrying about who owns what rights to what, the public domain is an excellent way to indicate that in a single sentence. If he wishes to retain attribution for the code, he should look into a different permissive license, or if he wants to force everyone who uses the code to contribute their changes back to the community, he can use a strong copyleft license such as the GPL.

---

### Post by trent.josephsen on 2010-06-16
Allow me to point out that "public domain" is a nebulous legal construct which has been interpreted in many different ways over the years and in different locations.  Some countries do not allow an author to place his work in the public domain.  Some countries don't recognize the concept at all.

---

