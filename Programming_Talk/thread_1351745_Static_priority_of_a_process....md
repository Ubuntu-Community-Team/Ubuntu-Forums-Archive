---
title: "Static priority of a process..."
date: 2009-12-10
forum: Programming Talk
---

### Post by K-Z on 2009-12-10
Can you please tell me where in kernel the static priority of any process is determined???? I am implementing a scheduler inside kernel. So, I want to go to that section and allot static priority to each process as per my algorithm. I do not want to make use of any system calls like nice() or set_scheduler().

---

### Post by CptPicard on 2009-12-11
Well, I would think that examining the source of the priority-setting syscalls would reveal quite a bit of the internal structures of the kernel that get altered by them?

---

