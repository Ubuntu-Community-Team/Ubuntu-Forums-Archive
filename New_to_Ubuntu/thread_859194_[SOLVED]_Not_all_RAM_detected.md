---
title: "[SOLVED] Not all RAM detected"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by LRT on 2008-07-14
here are my specs:

[http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=580&formid=3404&website=AcerPanAm.com&siteid=7117&words=all&keywords=&areaid=2]("http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=580&formid=3404&website=AcerPanAm.com&siteid=7117&words=all&keywords=&areaid=2")

i wanted to upgrade to 1GB of RAM but the BIOS and Ubuntu is only detecting part of it. The BIOS shows 786432 KB and /proc/meminfo MemTotal shows 775028 KB. the new RAM is DDR2 PC2-5300 667Mhz. if you read the specs on the link above this RAM should be compatible. 

anyone know how i can fix this?

---

### Post by hyper_ch on 2008-07-14
does your video card use shared ram?

---

### Post by PmDematagoda on 2008-07-14
Did you also check your BIOS to see if there is such an option like Physical Address Extensions(or something like that), and if it is on?

---

### Post by LRT on 2008-07-14
> does your video card use shared ram? 
not sure, but i can tell you that the post screen shows the following:

```
Memory testing: 786368K OK+ 256M shared memory
```

so does this mean that it IS detecting all the memory?? i don't have a video card, it is onboard video. is the onbard video supposed to use this "shared ram"??

> Did you also check your BIOS to see if there is such an option like Physical Address Extensions(or something like that), and if it is on?

i don't see anything the says "Physical Address Extension" in the BIOS.

---

### Post by overdrank on 2008-07-14
> **hyper_ch said:**
> does Your Video Card Use Shared Ram?

+1 :)

---

### Post by mcduck on 2008-07-14
Yes, the integrated graphics card takes it's share of your RAM.

PAE isn't important here, it's only relevant if you want to use more memory than waht a 32-bit system would otherwise understand 4GB and more).

"cat /proc/meminfo" reports even less memory as the kernel is loaded to RAM at boot and that part of the memory doesn't count as available memory.

---

### Post by LRT on 2008-07-14
thank you for explaining that so well!

---

