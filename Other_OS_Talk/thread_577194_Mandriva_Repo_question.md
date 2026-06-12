---
title: "Mandriva Repo question"
date: 2007-10-15
forum: Other OS Talk
---

### Post by 67GTA on 2007-10-15
I have added the official, distrobution, and PLF repos to 2008. I see that most of the apps have two entries. One from Mandriva, and one from PLF. If I only used PLF repos, will I miss anything by not having the Mandriva repos such as official updates? Do they get sent to the PLF mirrors? I have always liked the PLF repos for restricted multimedia purposes.

---

### Post by AdamWill on 2007-10-16
Usually when an app exists in both PLF and the official repos it's the same package built with different options - for instance, the freetype2 packages in Mandriva and PLF are identical (and built from the same SRPM) except that in PLF the bytecode interpreter is enabled. Usually in this case the PLF package will be updated whenever the official package is updated.

---

### Post by igknighted on 2007-10-16
> **67GTA said:**
> I have added the official, distrobution, and PLF repos to 2008. I see that most of the apps have two entries. One from Mandriva, and one from PLF. If I only used PLF repos, will I miss anything by not having the Mandriva repos such as official updates? Do they get sent to the PLF mirrors? I have always liked the PLF repos for restricted multimedia purposes.

PLF doesn't have everything though.  So say OO.o has a security flaw, and an update is released... then you need the official repo to get it.  Repo updating in urpmi is fast enough that there really isn't any reason not to leave the official sources... all the packages are labled "mdv" or "plf" so you wont run into conflicts if that is what you are worried about.

---

### Post by AdamWill on 2007-10-16
Obviously. I think the OP just wanted to know whether the actual PLF packages he installed would get updates.

---

### Post by igknighted on 2007-10-16
> **AdamWill said:**
> Obviously. I think the OP just wanted to know whether the actual PLF packages he installed would get updates.

I figured, just thought I would add it to be on the safe side

---

