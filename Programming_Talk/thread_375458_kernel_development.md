---
title: "kernel development"
date: 2007-03-03
forum: Programming Talk
---

### Post by polosataja on 2007-03-03
Studing linux kernel development I need some linux box to run test modules. I'm not writing anything for some special devices, so virtual box will be ok (without xorg, only console). 

What to choose? "9 steps to install vmware" is to complicated for this and I don't want to mess up the system installing all this "9 steps" stuff. May be there is some "one command sudo aptitude"?

I've heared such words like "qemu", "virtualbox", "kvm", but have not tried them. Or may be I even don't need them at all?

---

### Post by pmasiar on 2007-03-03
> **polosataja said:**
> Studing linux kernel development I need some linux box to run test modules. (...) "9 steps to install vmware" is to complicated for this and I don't want to mess up the system installing all this "9 steps" stuff. May be there is some "one command sudo aptitude"?

I have little clue about kernel development etc. But I have this gut feeling that if you are looking for 1-command aptitude and 9 steps is too complicated, you might be not ready yet to solve real kernel problems when they strike. Maybe you need to learn more, become expert is less esoteric areas first? Ie compile your own kernel, try to build gentoo, or linux from scratch?

I readily admit I have no clue and hope experts will give you better advice. Good luck.

---

### Post by Mr. C. on 2007-03-04
I agree with the previous poster's comment.  If you don't have the diapers for installation, or dual boot, you're not going to make it as a kernel jock!

Ok, with that said, you might be able to get by with one of the live CDs which allows loadable driver modules.  This won't be difficult for a kernel-g(uy|al) like yourself!

MrC

---

### Post by polosataja on 2007-03-04
No, installing vmware is not difficult for me! The only i want is to not mess up the system installing third-party debs and tar.gz's manually. May be there is some open source virtual machine emulator that will be enough to run console mode linux. Or may be there is some other way to test modules.

---

### Post by winch on 2007-03-04
[User-mode Linux]("http://user-mode-linux.sourceforge.net/") might be of some use.

---

### Post by lloyd mcclendon on 2007-03-04
+1 for user mode linux, you definately need that for kernel dev

---

### Post by polosataja on 2007-03-04
Aha, thank u!

---

