---
title: "Setting Swap Size"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by EDLIU on 2013-05-18
Hi,

My laptop uses 8 GB RAM.

What's the size I should set for my "Ubuntu(64-bits) Swap partition"?

And, my laptop runs Intel Chip. But the downloaded Ubuntu(13.04) shows "AMD 64-bit"

Thanks.

Ed

---

### Post by Hekabe on 2013-05-18
You should probably just set it to 4GB. As for the processor problem, where does it say AMD 64-bit?

---

### Post by cortman on 2013-05-18
AMD64 is what the architecture is often referred to. I don't think it's incorrectly saying you have an AMD processor.

---

### Post by HermanAB on 2013-05-19
Hmm, it is a laptop, so you probably want to use Suspend when you snap the lid shut.  Therefore you should set the swap size to at least 2x RAM size.  The suspend process scribbles the machine state into the swap partition and if it is too small, then suspend will fail.

---

### Post by Irihapeti on 2013-05-19
> **HermanAB said:**
> Hmm, it is a laptop, so you probably want to use Suspend when you snap the lid shut.  Therefore you should set the swap size to at least 2x RAM size.  The suspend process scribbles the machine state into the swap partition and if it is too small, then suspend will fail.

I think that applies to hibernate, not suspend. Hibernate writes to swap; suspend writes to RAM.

My EeePC 900 has never had a swap partition, and I've suspended it on many occasions with no problems.

---

### Post by mcduck on 2013-05-19
Yep, the swap is needed for hibernate, not suspend, and it doesn't require twice as much swap as there is RAM, only *as much as RAM currently used on the system*. So if you want to know you will be able to hibernate in any situation you need as much swap as you have RAM.

The rule about swap=2xRAM is an old one, and doesn't relate to hibernating or make any sense with the amounts of RAM PC's have these days.

(There is a bit of confusion in the naming, though, as suspend/hibernate are sometimes referred as "suspend-to-RAM" and "suspend-to-disk")

---

### Post by Impavidus on 2013-05-19
> **EDLIU said:**
> Hi,

My laptop uses 8 GB RAM.

What's the size I should set for my "Ubuntu(64-bits) Swap partition"?

And, my laptop runs Intel Chip. But the downloaded Ubuntu(13.04) shows "AMD 64-bit"

Thanks.

Ed

If you want to hibernate, set swap to slightly more than RAM. Mind the difference between gigabinarybytes and decimal gigabytes: 8GiB RAM=8192MiB RAM, necessiating 8590MB disk space, so make it 9000MB=9GB to be sure. If you don't hibernate, or if you accept that you won't be able to hibernate on the rare occasions that you actually use most of your RAM, you don't need that much. With 8GB RAM it's unlikely your computer will ever run out of RAM. Well, unless you like video editing, want a bunch of virtual machines or some other very memory-hungry things.

It is labeled AMD 64-bit because AMD first introduced 64-bit processors. Intel followed quickly, but the name AMD 64-bit stuck.

---

### Post by CatKiller on 2013-05-19
Strictly, Intel had their own 64-bit instruction set - IA-64 or Itanium. Nobody liked it. AMD's 64-bit instruction set (AMD64 or x64) was backwards-compatible with x86 in hardware and everybody liked that. Intel went with the market and used AMD's instruction set.

---

### Post by richierich1986 on 2013-05-19
On a default Ubuntu install, the installer sets the amount of swap to the same amount as the RAM. I've checked this on numerous installs,
and it's always the same. So if you have 8Gb of RAM, set 8Gb of swap. If Ubuntu does so by default, it must be a good guideline.

---

### Post by EDLIU on 2013-05-20
Thanks.

Ed

---

