---
title: "Memory usage by a process."
date: 2009-12-07
forum: Programming Talk
---

### Post by K-Z on 2009-12-07
Hi all. I am working inside kernel 2.6. In that, for every process, I am calculating its memory usage or requirement from vm_area_struct (vm_end-vm_start) in its mm_struct structure. Is my approach correct. 

Also, can you please tell me whether it is possible to send a string from shell level to kernel level through system call??

---

### Post by Arndt on 2009-12-08
> **K-Z said:**
> Hi all. I am working inside kernel 2.6. 

[...]

Also, can you please tell me whether it is possible to send a string from shell level to kernel level through system call??

Isn't that what for example 'open' and 'write' do?

(What's shell level? Is it user level?)

---

### Post by K-Z on 2009-12-09
> **Arndt said:**
> Isn't that what for example 'open' and 'write' do?

(What's shell level? Is it user level?)

I really don't have idea about that, but shell is same as user level. Can u please tell me whether I am correct or not for this.....

I am working inside kernel 2.6. In that, for every process, I am calculating its memory usage or requirement from vm_area_struct (vm_end-vm_start) in its mm_struct structure. Is my approach correct. 

Also, can you please tell me whether it is possible to send a string from shell level to kernel level through system call??

---

