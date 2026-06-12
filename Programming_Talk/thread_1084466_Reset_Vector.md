---
title: "Reset Vector"
date: 2009-03-02
forum: Programming Talk
---

### Post by Lekshmi on 2009-03-02
While kernel boot up ,operating mode will be real mode .this ia 16 bit adressing mode. only 1MB can be accessible.So the content of EIP ie 0xFFFF0 is added with some hidden register content which inturn points to the location 0xFFFFFFF0. Why this particular address (0xFFFFFFF0) is choosen? This is 4GB - 16 bytes. Is any speciality for this address?

---

### Post by veda87 on 2009-03-02
that is because When the computer is turned on, its BIOS instructions are executed. That is, when you turn on ANY PC it jumps to 0xFFFFFFF0 (BIOS). By the way, the BIOS is usually located on read-only memory (ROM) so it is also known as firmware.

for more help, do refer the following link....

[http://www.cs.ucla.edu/~kohler/class/05f-osp/notes/lec03.html](http://www.cs.ucla.edu/~kohler/class/05f-osp/notes/lec03.html)

---

### Post by jespdj on 2009-03-02
Here's an interesting article for you: [http://duartes.org/gustavo/blog/post/how-computers-boot-up](http://duartes.org/gustavo/blog/post/how-computers-boot-up)

There are more interesting posts on how the computer works on a low level on that blog.

---

