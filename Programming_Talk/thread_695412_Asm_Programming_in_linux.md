---
title: "Asm Programming in linux"
date: 2008-02-13
forum: Programming Talk
---

### Post by karthikbalaji on 2008-02-13
Hi All,

I m a newbie trying to learn the linux kernel. I started going through the linux kernel. But I m unable to comprehend the functionality and implementation of asm blocks.

for example,
__asm__ __volatile__(
		"bis %1,%1,$30\n\t"
		"bis %0,%0,$26\n\t"
		"ret ($26)"
		: /* no outputs: it doesn't even return */
		: "r" (START_ADDR),
		  "r" (PAGE_SIZE + INIT_STACK))

Is there any good tutorial to learn this kind of asm programming?

Thanks

---

### Post by LaRoza on 2008-02-13
[http://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html](http://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html)

You should know C and Assembly before doing this.

---

### Post by karthikbalaji on 2008-02-13
Thanks .. Will go through that link. Seems to be a good introduction.
I have some experience with 8085 assembly. Hope that will help.

---

### Post by karthikbalaji on 2008-02-28
I would like to *** the following link also to the list .. Its pretty good ..

[http://www.delorie.com/djgpp/doc/brennan/brennan_att_inline_djgpp.html](http://www.delorie.com/djgpp/doc/brennan/brennan_att_inline_djgpp.html)

---

### Post by Wybiral on 2008-02-28
I would learn GAS assembly before learning inline GCC assembly. It will make more sense that way.

---

