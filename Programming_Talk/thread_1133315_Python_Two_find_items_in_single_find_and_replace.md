---
title: "Python: Two find items in single find and replace?"
date: 2009-04-22
forum: Programming Talk
---

### Post by blairm on 2009-04-22
Hi,

I can do a normal find and replace in python using re.sub, but is it possible to have two items in the find part of a find and replace?
The context is I have a file and want to remove all lines that don't start with # or "http
Doing the # find and replace first won't work, because that will remove all the lines starting with "http, which I want to keep.
Same problem would arise if I did the "http find and replace first.

Any ideas gratefully received,

Blair

---

### Post by ghostdog74 on 2009-04-22
use the alternation operator "|"

---

### Post by blairm on 2009-04-22
Thanks Ghostdog... that seems to do the trick.
If you don't mind me asking, how long does it take to get to a point where you know all these commands?
I've only been playing with Python - in fact, any kind of programming - for a few weeks. Can I expect to have a reasonable idea of what I'm doing within a year or is that unrealistic?
I'm putting in about 20 hours a week, if that makes a difference.

Blair

---

### Post by ghostdog74 on 2009-04-22
> **blairm said:**
> Thanks Ghostdog... that seems to do the trick.
If you don't mind me asking, how long does it take to get to a point where you know all these commands?

I have been using Python since 1997/98. your question really has no direct answer so i am really not sure. it depends on a lot of factors. what i can say is that if you are really into learning python, plan your time well, read, understand, practice and ask when in doubt. For your case, how long does it take for you to read [this](http://www.amk.ca/python/howto/regex/)?

---

### Post by blairm on 2009-04-22
Thanks for your reply.

It's becoming obvious that I can't just throw myself in the deep end with this and rely on picking things up along the way as I've done with everything else in life; I will have to study the basics first. 

As for how serious I am about learning - looking for a hobby which is completely different to work, where intuition and people skills are the key requirements; my logic skills are lacking, so I'm hoping that programming will improve them.

Cheers,

Blair

---

