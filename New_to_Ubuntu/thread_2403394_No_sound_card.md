---
title: "No sound card"
date: 2018-10-10
forum: New to Ubuntu
---

### Post by santiagoandreu on 2018-10-10
Hi, I'm new to Ubuntu, installed it yesterday. I installed lastest version (LTS18.04).
The problem is that no sound card is detected and I dont get any sound in my speakers, headphones or HDMI output (image is ok).
Help please, Thanks.
Santiago

---

### Post by oldrocker99 on 2018-10-11
Post the results of```
lspci
```

---

### Post by santiagoandreu on 2018-10-11
> **oldrocker99 said:**
> Post the results of```
lspci
```

00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 36)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers (rev 36)
00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 36)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 36)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 36)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 36)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 36)

That's what i got.

---

