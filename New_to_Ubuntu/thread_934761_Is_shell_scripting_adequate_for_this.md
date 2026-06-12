---
title: "Is shell scripting adequate for this?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Ephilei on 2008-09-30
Never done shell scripting, but thought this might give me an excuse. I just want to write something to do this:

```

for each file in folder(
   if file(x) contains mystring
      move file(x) to mydirectory
   fi
   x++
)

```

Just want to make sure that's possible before I go put hours into it.

---

### Post by niteshifter on 2008-10-01
Hi,

Yes, bash can do what you want. It can be "pure" shell script even (no greping or (g)awking).

But you may find those two (grep and / or awk) useful :)

---

### Post by ghostdog74 on 2008-10-01
> **Ephilei said:**
> Never done shell scripting, but thought this might give me an excuse. I just want to write something to do this:

```

for each file in folder(
   if file(x) contains mystring
      move file(x) to mydirectory
   fi
   x++
)

```

Just want to make sure that's possible before I go put hours into it.

```

mv *mystring* /destination

```

---

### Post by Ephilei on 2008-10-01
Thanks. That was just pseudo code, btw.

---

