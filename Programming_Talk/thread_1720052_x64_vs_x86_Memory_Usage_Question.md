---
title: "x64 vs x86 Memory Usage Question"
date: 2011-04-02
forum: Programming Talk
---

### Post by nova47 on 2011-04-02
So I've been working through the book Hacking the Art of Exploitation 2nd edition (excellent book for the record) and I got to the example displayed here [http://forum.intern0t.net/offensive-guides-information/2902-basic-buffer-overflow-attacks.html](http://forum.intern0t.net/offensive-guides-information/2902-basic-buffer-overflow-attacks.html). I originally attempted to recreate the buffer overflow on my x64 machine and via gdb noticed that the auth_flag was loaded in memory space lower than password_buffer. However when I recreated the overflow on an x86 machine auth_flag was properly loaded after password_buffer. Why is that?

---

### Post by johnl on 2011-04-02
Just a hunch -- try adding '-fno-stack-protector' to the flags you pass to gcc.

---

### Post by dazman19 on 2011-04-04
2 to the power of 32 is what? 
0 or 1 (2 bits),

x64 well EM64T is 2 to the power of 40.

---

