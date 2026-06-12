---
title: "Setup to compile for mips"
date: 2005-10-18
forum: Programming Talk
---

### Post by kalias on 2005-10-18
Has anyone in ubuntu land done C development for the mips processor?  I would like to know how to setup my toolchain for the mips processor.  From what I have read it requires some work.  Drop me a note if you have some info.

thanks :)

kalias

---

### Post by toojays on 2005-10-18
I have done MIPS development before, but that was on a native MIPS/Gentoo system. If you want to build MIPS binaries on an x86 box, you will need to build yourself a cross-compiler toolchain. It does require some work. I found [these instructions]("http://foobazco.org/~wesolows/mips-cross.html"); the "Phase 1" section is relevant to your situation.

---

### Post by ratdude747 on 2009-12-28
thanks to the loongson becoming a reality, i suggested that ubuntu be ported to MIPS on ubuntu brainstorm.

---

