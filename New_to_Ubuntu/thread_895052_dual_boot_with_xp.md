---
title: "dual boot with xp"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-08-19
if i have xp installed first and i install xubuntu after will the grub menu automatically add xp to the boot menu ? :confused:

---

### Post by talsemgeest on 2008-08-19
Yeah, it should. But even if it doesn't, it is pretty easy to add it manually.

---

### Post by smooth3006 on 2008-08-19
> **talsemgeest said:**
> Yeah, it should. But even if it doesn't, it is pretty easy to add it manually.

well if it doesn't, can you help me out by giving me instructions on how to do it ? i know when i installed ubuntu after vista it added it automatically to grub.

---

### Post by kk0sse54 on 2008-08-19
I see no reason why it shouldn't and if it doesn't just edit /boot/grub/menu.lst and point grub to where xp resides on your hard drive with chainloader set at +1.

---

### Post by talsemgeest on 2008-08-20
If it doesn't I will be more than happy to walk you through adding it manually. But by all counts it should add it automatically.

---

