---
title: "memory addresses for bash screen"
date: 2009-10-17
forum: Programming Talk
---

### Post by wirate on 2009-10-17
I have a very old book (Let Us C by Yashavant Kanetkar) which tells me that the first letter on-screen is stored in the memory address 0xB8000000 with its color in 0xB8000001. I can not figure out how I can apply this to bash????

---

### Post by NathanB on 2009-10-17
Hi Waqar,

Due to the way modern operating systems re-map all the memory addresses via a Virtual Memory scheme, there is no way of knowing what the true address will be at any given time.  Also, due to the protective measures imposed by modern OSs, you do not have direct access to hardware resources from a user-mode application.

[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

I suggest that you install a FrameBuffer driver - it is very similar to what you want to achieve.

[http://en.wikipedia.org/wiki/Framebuffer](http://en.wikipedia.org/wiki/Framebuffer)

Nathan.

---

### Post by wirate on 2009-10-17
^^ many thanks :)

---

