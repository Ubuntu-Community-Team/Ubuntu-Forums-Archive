---
title: "flex doesn't work"
date: 2008-04-14
forum: Programming Talk
---

### Post by mbazs on 2008-04-14
Hi,

I wanted to start using flex (2.5.33 amd64) , but it tells me a bunch of idiot messages

c.l:4: bad character: %
c.l:4: unknown error processing section 1
c.l:4: unknown error processing section 1
c.l:4: unknown error processing section 1
c.l:5: unrecognized '%' directive
c.l:8: bad character: %
c.l:8: bad character: }

this is nonsense, it's a really simple example I wanted to compile to C++.

Any ideas?

---

### Post by Tuna-Fish on 2008-04-14
umm.. huh? the fault is in your input. Fix it.

... Specifically, flex works just fine. Something else failed.

---

### Post by mbazs on 2008-04-15
I don't think so, it fails on the very first % character:
%name Scanner

in addition, it fails on EVERY character, I don't think that it's my fault

---

### Post by mbazs on 2008-04-15
It might be the example is bad. URRRGHHH!
Thanx!

---

### Post by Tuna-Fish on 2008-04-15
np. Sorry if I was a little harsh, we get "Tool X that tens of thousands of people use worldwide is broken, please help me. My input is flawless."-style here at least a few times a week, and a lot more from a few other programming forums I visit. Simple math says I have read hundreds of such messages in my lifetime. Not one has turned out to be correct. In the rare cases that weren't straight PEBKAC, there usually was somehow malformed input or test data.

For humor, search "gcc broken" in the programming forums.

---

### Post by Zwack on 2008-04-15
> **Tuna-Fish said:**
> For humor, search "gcc broken" in the programming forums.

Hey, I've reported GCC broken before...

And it was.  I can't remember the exact problem but it was something to do with the 64 bit HP-UX compilation failing but the 32 bit version working.  But, yes, most "This tool is broken" errors are input problems and not tool errors.

Z.

---

