---
title: "Cross compile for armv5 problem"
date: 2015-02-21
forum: Packaging and Compiling Programs
---

### Post by Frank_Natoli on 2015-02-21
Using ubuntu 14.04 LTS. Cross compiling for Cirrus Logic EP9301 which is ARM v5 ARM9 CPU. "man gcc" on Ubuntu says "armv5" is valid option for "-march=" but is rejected by gcc with message "bad value (armv5) for -march= switch". For that matter, all architecture options that "man gcc" says are valid are rejected by gcc. How to convince gcc under Ubuntu to honor "-march=armv5"?

Was using a much older gcc [different path to compiler] that I inherited from former project engineer. Older gcc was generating good code for EP9301 except the compiler disregards "#pragma pack(1)" since the EP9301 needs aligned data and the older gcc is apparently incapable of generating byte referencing instructions for multi-byte integers to avoid mis-aligned data traps.

I was hoping that the much newer gcc that comes with Ubuntu would generate byte referencing instructions but can't get it to accept the "-march=armv5" switch.

---

