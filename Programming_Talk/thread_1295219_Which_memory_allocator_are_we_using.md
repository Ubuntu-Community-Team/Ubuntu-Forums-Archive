---
title: "Which memory allocator are we using?"
date: 2009-10-19
forum: Programming Talk
---

### Post by froggyswamp on 2009-10-19
Folks, is there any simple way to detect whether I'm running slub or slab?
/proc/slabinfo doesn't seem to mention that.

---

### Post by renkinjutsu on 2009-10-19
try this ```
cat /proc/meminfo | grep -o -i -e slab -e slub
```

---

### Post by froggyswamp on 2009-10-19
It yields "Slab", but my gut feeling tells me "Slab" in this case doesn't really mean the real name of the allocator, i.e. slub provides info under /proc/slabinfo for compatibility/ABI reasons, could be same story with meminfo.
I mean, ru sure?

---

### Post by renkinjutsu on 2009-10-19
hmm.. you can always open up /boot/config-$(uname -r) in gedit and search for slub/slab

that's the config for compiling the kernel (tis what i think)

---

### Post by froggyswamp on 2009-10-19
Thanks! Since slab is commented out and slub is not, looks like the latter is on.

---

