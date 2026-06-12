---
title: "Magically expanding hard drive??"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by staf0048 on 2008-07-19
I have an odd problem (if you can call it that).  I installed a 500GB HD a few months ago as a replacement for my very old 20 GB one.  Installation went fine and I haven't had any issues whatsoever since the upgrade, however I just checked the Disk Usage Analyzer to see how much space I'd used up and for some reason it's now telling me that my 500GB HD is 920GB!!!  I"m not complaining by any means, but can anyone offer an explanation as to how this could happen?

---

### Post by kool_kat_os on 2008-07-19
maybe they messed up when packaging the HD? :confused:

Thats strange....

---

### Post by Shippou on 2008-07-19
> **kool_kat_os said:**
> maybe they messed up when packaging the HD? :confused:

Thats strange....

Cool! I wish that happens to me... :)

---

### Post by kool_kat_os on 2008-07-19
> **Shippou said:**
> Cool! I wish that happens to me... :)

me too! :)

---

### Post by Shazaam on 2008-07-19
Uncheck "gvfs-fuse-daemon" in Preferences (Disk Usage Analyzer). What happens is this doubles the output on files and usage. I don't know if it is a bug or default but it is annoying.

---

### Post by staf0048 on 2008-07-19
> **kool_kat_os said:**
> maybe they messed up when packaging the HD? :confused:

Thats strange....

I'm pretty certain it was around 500GB when I originally installed it, because otherwise I would have noticed this much earlier than now.  I installed it in April.

---

### Post by staf0048 on 2008-07-19
> **Shazaam said:**
> Uncheck "gvfs-fuse-daemon" in Preferences (Disk Usage Analyzer). What happens is this doubles the output on files and usage. I don't know if it is a bug or default but it is annoying.

Thanks that fixed my problem.  Though I must say I'm not nearly as excited as I was 5 minutes ago . .

---

### Post by Shazaam on 2008-07-19
Sorry to burst your bubble.....
:)

---

