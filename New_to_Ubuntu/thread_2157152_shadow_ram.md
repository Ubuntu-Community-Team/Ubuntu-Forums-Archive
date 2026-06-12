---
title: "shadow ram"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by prs3e8 on 2013-06-24
Should shadow ram on x86 machines be disabled when installing Linux?  I saw a several of mentions about that , but they were both old.   Is it still valid advice?

---

### Post by vipulkumar7 on 2013-06-24
I think you are right by disabling a shadow RAM.you can  accelerate access to the ROMs on your motherboard and on some of the controller cards. Linux does not use these ROMs once it has booted because it provides its own faster 32-bit software in place of the 16-bit programs in the ROMs. Disabling the shadow RAM may make some of it available for programs to use as normal memory.  Leaving the shadow RAM enabled may interfere with Linux access to hardware devices. :)

---

