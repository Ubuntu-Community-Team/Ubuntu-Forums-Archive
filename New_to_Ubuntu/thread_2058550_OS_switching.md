---
title: "OS switching"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by ericsonlouis on 2012-09-15
Hey I have a question i have constantly been changing my laptops os and i want to know if it in anyway will affect my computer if i continue to change it . Can my computer crash or anything?

---

### Post by critin on 2012-09-16
> **ericsonlouis said:**
> Hey I have a question i have constantly been changing my laptops os and i want to know if it in anyway will affect my computer if i continue to change it . Can my computer crash or anything?

Can't speak for a laptop, but as for my two desktops, an emachine and a Dell, I'll let you know when or if they finally crash.  They are both older with low specs and I'm constantly changing os's, running as many as possible on the disks, replacing them one at a time, and doing it all over again.

They haven't been harmed by a 'buntu yet.  Laptops may be more fragile.

---

### Post by varunendra on 2012-09-16
[*Disclaimer*: The info below may be incorrect as most of it is my personal understanding based on random readings on the net]

Although given the fact how robust HDDs are these days you shouldn't be worried about this, but it is worth noting that everytime you install a new OS, the MBR is overwritten. MBR (Master Boot Record) is located on the 'first sector' on any hard disk and contains the partition table, boot-flag info, and initial boot-program (optional). If this one sector gets corrupt, the HDD is trash, no matter how clean or healthy the rest of the disk is. AFAIK, this 'first' sector can not be relocated externally (at user level) and I believe even the internal mechanism or logic of the HDD does not have any provisions to relocate it if it gets corrupt.

Having said above, I think any sector on a modern HDD is capable of surviving thousands, maybe a few million, rewrites, so you can't wear it out just by installing-reinstalling OSes :).

(oh, any corruption/scratch etc. made 'EXACTLY' during the writing of MBR at this 512 Byte sector due to shock or power surge would count as "accident", not a normal wear & tear ;))

Hope it helps.

---

### Post by ericsonlouis on 2012-09-17
Thanks now I can continue with my testings :)

---

