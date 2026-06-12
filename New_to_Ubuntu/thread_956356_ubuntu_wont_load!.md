---
title: "ubuntu wont load!"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by nilsolaris on 2008-10-23
I'm having quite a problem at the moment with ubuntu, on the loading screen if im am not able to press esc at the GRUB loading screen and go down to the past version ubuntu kernel 2.6.21-19 , it loads ubuntu kernel 2.6.21-24 and gets stuck at the 75% mark. This starting happening after an update. How can I fix this problem?

---

### Post by eragon100 on 2008-10-23
> **nilsolaris said:**
> I'm having quite a problem at the moment with ubuntu, on the loading screen if im am not able to press esc at the GRUB loading screen and go down to the past version ubuntu kernel 2.6.21-19 , it loads ubuntu kernel 2.6.21-24 and gets stuck at the 75% mark. This starting happening after an update. How can I fix this problem?

I don't know how to make that kernel version work, but you can install startup manager from add/remove to set 2.6.21-19 as the default.
Then you wouldn't have to select it in Grub.

---

### Post by nilsolaris on 2008-10-23
Thank you for the reply. By chance would you know if there is a way I could possibly remove ubuntu kernel 2.6.21-24 all together and reinstall it?

---

### Post by Liviu-Theodor on 2008-10-23
> **nilsolaris said:**
> Thank you for the reply. By chance would you know if there is a way I could possibly remove ubuntu kernel 2.6.21-24 all together and reinstall it?

Yes you can, but be sure to have at least another working kernel. Do it with [FONT="Courier New"]System-Administration->Synaptic Package manager[/FONT].

---

### Post by nilsolaris on 2008-10-23
Again thanks for the help, but what actually would I be look for in Synaptic Package manager? I am not seeing any similar to kernel 2.6.21-24.

---

### Post by dave.com on 2008-10-23
You mean kernel 2.6.24-21 _not_ 2.6.21-24

---

### Post by Liviu-Theodor on 2008-10-23
> **nilsolaris said:**
> Again thanks for the help, but what actually would I be look for in Synaptic Package manager? I am not seeing any similar to kernel 2.6.21-24.
You should do a search with the [FONT="Courier New"]linux kernel[/FONT] keywords. And search the packages that begin with [FONT="Comic Sans MS"]linux-headers-[/FONT], [FONT="Comic Sans MS"]linux-image-[/FONT] and [FONT="Comic Sans MS"]linux-ubuntu-[/FONT]. There are a lots of them, you must be patient. You will see also some version numbers there.

---

