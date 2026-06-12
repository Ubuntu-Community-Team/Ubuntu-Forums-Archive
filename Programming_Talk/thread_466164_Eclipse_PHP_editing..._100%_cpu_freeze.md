---
title: "Eclipse PHP editing... 100% cpu freeze"
date: 2007-06-06
forum: Programming Talk
---

### Post by zackiv31 on 2007-06-06
So I just installed eclipse on 7.04, and installed the necessary PHP plugins...

On certain documents, when I type certain words, or try to close tags, my cpu jumps to 100% and eclipse freezes... I wait a couple minutes, but nothing happens... and I'm forced to kill it...

Any suggestions???

---

### Post by zackiv31 on 2007-06-06
I can't type the following tag: <script>

Once I try to type the last '>', it shoots to 100% and freezes.

---

### Post by ditsch on 2007-06-06
Be sure you are running Eclipse with a SUN VM, the GCJ runtime (which is the default) obviously has problems with PHPEclipse (and Eclipse in general btw).

---

