---
title: "missing files needed by configure scripts"
date: 2007-02-28
forum: Programming Talk
---

### Post by nickoli_02 on 2007-02-28
I'm attempting to compile the latest f-spot 0.3.4 and I'm getting stuck with this error when running ./configure:

```
checking for mono... /usr/bin/mono
checking for gmcs... /usr/bin/gmcs
checking pkg-config is at least version 0.9.0... yes
checking for GDU_MODULE_VERSION_CHECK... yes
checking for mono.pc... configure: error: missing the mono.pc file, usually found in the mono-devel package

```

I ran locate and whereis after updatedb to try and find the missing file... it doesn't seem to be on my computer. This isn't the first time I've ran into this type of problem, so, I'm hoping someone can fill me in on a solution :)

---

### Post by po0f on 2007-02-28
nickoli_02,

> **nickoli_02 said:**
> I'm attempting to compile the latest f-spot 0.3.4 and I'm getting stuck with this error when running ./configure:

```
checking for mono... /usr/bin/mono
checking for gmcs... /usr/bin/gmcs
checking pkg-config is at least version 0.9.0... yes
checking for GDU_MODULE_VERSION_CHECK... yes
checking for mono.pc... configure: error: missing the mono.pc file, **usually found in the mono-devel package**

```

I ran locate and whereis after updatedb to try and find the missing file... it doesn't seem to be on my computer. This isn't the first time I've ran into this type of problem, so, I'm hoping someone can fill me in on a solution :)

```
[FONT="Courier New"]$ sudo apt-get install mono-devel[/FONT]
```

:)

---

### Post by nickoli_02 on 2007-03-01
haha....... thanks :)

Well I installed mono-devel, but I get the same error. Locate mono.pc doesn't find the file...

---

### Post by po0f on 2007-03-01
nickoli_02,

Ok, try installing libmono-dev instead.

---

### Post by nickoli_02 on 2007-03-01
alright... glad all those dependencies got sorted out, haha. Make and checkinstall finished with no errors :) thanks!

---

### Post by tanemahuta on 2007-05-22
Thx! Helped for me too!

---

### Post by Raineer on 2007-06-01
> **po0f said:**
> nickoli_02,

Ok, try installing libmono-dev instead.

Thank you for this! I needed that one as well.

---

### Post by pavolzetor on 2008-04-26
and me too thx

---

