---
title: "Running AMD ISO(Kubuntu) on Intel Platform -(finding the right ISO)"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by saponempotenti on 2012-04-16
I did not know that the ISO versions of Intel 64 and AMD 64 were so different they needed the exact processor?  I guess this would make sense.  So when decididng on the ISO information, you need 32(AMD or Intel) vs 64 (AMD or Intel) and then the correct distro.  This can make it challenging when trying to find the exact ISO for your needs.  Some distributions do not have the 64 our yet alone 64 for intel :/  Any good places to find a list?  I do not like searching around in Pirate bay and such.

---

### Post by jwbrase on 2012-04-16
> **saponempotenti said:**
> I did not know that the ISO versions of Intel 64 and AMD 64 were so different they needed the exact processor?  I guess this would make sense.  So when decididng on the ISO information, you need 32(AMD or Intel) vs 64 (AMD or Intel) and then the correct distro.  This can make it challenging when trying to find the exact ISO for your needs.  Some distributions do not have the 64 our yet alone 64 for intel :/  Any good places to find a list?  I do not like searching around in Pirate bay and such.

AMD-64 ISO's will work on Intel 64-bit processors. The 64-bit version of the x86 architecture is called AMD-64 because AMD made the first x86-64 processors (whereas Intel had made the first 16 and 32-bit x86's). But Intel 64-bit processors use the same architecture as AMD 64-bit processors.

---

### Post by saponempotenti on 2012-04-16
Thanks for the response.  After more research I have discovered that the problem was virtual machine.  VM does not allow 64bit.  It was not my processor that was confused, but the virtualization.  Read something about editing the BIOS of VM to allow it to recognize 64 bit, but my actual processor does not allow that.  Ironic. -thanks again!

---

