---
title: "error&quot;this kernel requires a x86-64 CPU, but only detected a i686 cpu"
date: 2015-01-30
forum: New to Ubuntu
---

### Post by ninja85a on 2015-01-30
i tried to start ubuntu in a virtual machine and it comes up with that error but i do have a x64 cpu the fx 4130 why would it say this error?

---

### Post by lukeiamyourfather on 2015-01-30
Make sure that AMD-V is enabled in the BIOS/UEFI and that you have a 64-bit host operating system with the 64-bit version of the virtual machine software installed. All of those things are required to host 64-bit guests.

---

### Post by mailfordannym on 2015-02-08
Try to download the **32-bit** version of Ubuntu. It might run in the VM.

[http://www.ubuntu.com/download/desktop/thank-you?country=CA&version=14.04.1&architecture=i386](http://www.ubuntu.com/download/desktop/thank-you?country=CA&version=14.04.1&architecture=i386)

---

