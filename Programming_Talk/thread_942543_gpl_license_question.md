---
title: "gpl license question"
date: 2008-10-09
forum: Programming Talk
---

### Post by monkeyking on 2008-10-09
If I release my own program with source as gpl.

Will I be able to change future versions to non gpl?

I couldn't find any answers to this question.



thanks in advance

---

### Post by Tomosaur on 2008-10-09
> **monkeyking said:**
> If I release my own program with source as gpl.

Will I be able to change future versions to non gpl?

I couldn't find any answers to this question.



thanks in advance

If your project contains or is linked to GPLd code / libraries that you didn't write, then no.

If your project is built entirely from scratch, or uses code / libraries which are under some other licence which allows you to do so, then yes.

Basically speaking you can change your licence any time you feel like provided you're not depending on code which falls under the GPL.

---

### Post by pmasiar on 2008-10-09
Yes, you can change license terms of your own code anytime, or even use multiple licenses.

---

### Post by Zugzwang on 2008-10-09
> **monkeyking said:**
> If I release my own program with source as gpl.

Will I be able to change future versions to non gpl?

I couldn't find any answers to this question.


You can always dual-licence your work, for example like it is done in MySQL or QT. This means that apart from the GPL licence, you can also distribute your stuff under a different licence.

However, if someone has contributed to the project, you must either ask him/her for permission or remove that part from the project when switching/adding licences. Also you cannot withdraw your project once you released it under the GPL, i.e. you cannot prevent anyone else from distributing it or modifying it afterwards.

---

### Post by monkeyking on 2008-10-09
Ok, so what you are saying is.

If I release a version 0.5 as gpl.

Then I can make 0.6 non-gpl, or whatever license I want.
and I don't have to give out the source code in this release?

thanks

---

### Post by maximinus_uk on 2008-10-09
Correct.

However, I think that GPL is often *the answer*, not the question :)

---

### Post by rnodal on 2008-10-09
> **monkeyking said:**
> Ok, so what you are saying is.

If I release a version 0.5 as gpl.

Then I can make 0.6 non-gpl, or whatever license I want.
and I don't have to give out the source code in this release?

thanks

I am not an expert on this but as long as your code uses GPL licensed code then it must also be released under GPL. Sometimes GPL is not really the way to go.

-r

---

### Post by nvteighen on 2008-10-09
It's rather simple: if it's **your** code, you can do whatever you want with it.

But, if you use code from others, you have to respect their licensing terms. And GPL obliges you to make your code GPL.

The problem is that what constitutes "usage of others' code" depends on each country's legislation.

---

### Post by forger on 2008-10-09
Ah just give the source, the worst thing that can happen is you being advertised on child projects heh

---

