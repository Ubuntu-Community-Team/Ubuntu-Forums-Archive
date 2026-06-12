---
title: "nvidea &amp; Supertux etc problems"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by chaplanger on 2008-07-28
Now that I have moved form 7.10 to 8.04 -- I find that I cannot run any of the Supertux games (Supertuxcart, Supertux 2, or Planet Penguin Racer).  All of these worked fine before the update.

My Nvidea card is Geforce 6600 GT -- I am using the 'nv' driver (this has given me the best screen resolution so far -- allowing for 1024 x 768 ).

The games won't even start -- the screen momentarily flashes and then returns to the current screen without so much as an error message.  Any ideas on what is causing this and how to address it?  Thanks for any illumination on this.

---

### Post by ozbolt on 2008-07-28
Do you have compiz on or off?

---

### Post by PmDematagoda on 2008-07-28
Perhaps Supertux requires OpenGL acceleration, which in the case of the nv driver(which you are using) does not work. Did you try activating the Nvidia restricted driver by going to Hardware Drivers in System>Administration>Hardware Drivers?

---

### Post by chaplanger on 2008-07-28
> **ozbolt said:**
> Do you have compiz on or off?

How do I check this?

---

### Post by chaplanger on 2008-07-28
> **PmDematagoda said:**
> Perhaps Supertux requires OpenGL acceleration, which in the case of the nv driver(which you are using) does not work. Did you try activating the Nvidia restricted driver by going to Hardware Drivers in System>Administration>Hardware Drivers?

When I tried using the "nvidea' driver in 8.04 I was limited to 800x600 screen resolution.  This was unacceptable.

---

