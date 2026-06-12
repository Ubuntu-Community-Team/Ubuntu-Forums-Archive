---
title: "Apache and GPL licenses"
date: 2010-08-04
forum: Programming Talk
---

### Post by rigao on 2010-08-04
I've got a piece of code which is released under GPLv2 and a piece of code released under Apache v2.

I want to put them together in the same application. ¿How am I supposed to do it?

I think I can't just release it together, so I need to pack each thing separately, but it would be great if there is a way to pack it together even if I keep the two licenses making clear what is released under each one.

---

### Post by Bachstelze on 2010-08-04
According to the FSF, the Apache license is not compatible with the GPLv2, so assuming the GPL software is v2-only (and not v2-or-later), you may not distribute a piece of software that contains code covered by both licenses.  Once again this is all according to the FSF, it has not AFAIK been tested in court.

---

### Post by rigao on 2010-08-04
I thought it was the other way around, that Apache v2 didn't allow its code to be mixed with GPL, but GPL would not have any problem.

Anyhow, I must (I mean, I know nobody will sue me, because it is a very very little project and the author of the GPLv2 piece is unknown (to me at least), but I mean I must morally) then release two pieces of code, the one with the GPL code and the other one with the apache code, and then a help file with instructions in how to unite it, isn't it?

That's a mess, but it is what I'm doing atm.

---

### Post by Bachstelze on 2010-08-04
> **rigao said:**
> I thought it was the other way around, that Apache v2 didn't allow its code to be mixed with GPL, but GPL would not have any problem.

It doesn't really matter who "started it", the fact is that you can't mix Apache-licensed code with GPLv2 code.

> **rigao said:**
> Anyhow, I must (I mean, I know nobody will sue me, because it is a very very little project and the author of the GPLv2 piece is unknown (to me at least), but I mean I must morally) then release two pieces of code, the one with the GPL code and the other one with the apache code, and then a help file with instructions in how to unite it, isn't it?

Basically, yes.  Most people deal with it by distributing their software as source code only, with codes covered by different, uncompatible licenses in separate source files, and letting the user compile it for himself.

---

