---
title: "Multiple browser support in linux?"
date: 2008-09-15
forum: Programming Talk
---

### Post by extruct on 2008-09-15
Hello, since many of you know IE6 has poor css support, IE7 has a better one but still not perfect. In WinXP I was able to have all of them: IE6, IE7, FF and test my site in all of them. Someone know a way to run IE6/7 in Linux without the need to install Virtual machine?

Thanks.

---

### Post by forger on 2008-09-15
Internet explorer is not open source, I'm afraid you'll have to use a windows machine to test how it looks on it. You can always use virtual machine software, like virtualbox or vmware to create a virtual machine withinin ubuntu

edit: Also, the best test is within the original operating system, so neither wine or any internet explorer in linux will do :\

---

### Post by pp. on 2008-09-15
Have you looked at Wine? IE4 seems to run there, so perhaps more recent versions do that as well.

As far as IE can be said to run, of course.

---

### Post by extruct on 2008-09-15
Thanks for the replay, I think Ill have to use my sister's pc to test it :(

---

### Post by DrMega on 2008-09-15
If you do most of your testing in FireFox, you won't be far wrong. There are a few well known quirks and workarounds for making IE6 behave (can't remember them all, but most are to do with the box model). If you implement those workarounds (there are property names that FF ignores that IE doesn't, and vice versa), then you should need only minimal testing on IE.

---

### Post by perlluver on 2008-09-15
Also, there is IEs4Linux, maybe you could give this a try: [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux).

---

### Post by mssever on 2008-09-15
> **perlluver said:**
> Also, there is IEs4Linux, maybe you could give this a try: [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux).
But some sites look different in IEs4Linux than in real IE. Your best bet is a VM.

---

### Post by Reiger on 2008-09-15
But suppose you really don't want a vm; there is always: [http://browsershots.org](http://browsershots.org)

---

### Post by extruct on 2008-09-15
Yea I know about IEs4Linux, but as mssever said its probably not good as real IE6.
Reiger Thanks! Seems very hand!

---

