---
title: "[SOLVED] Booting GRUB Menu - Taking Too Long!!!"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by UnknownFear on 2008-05-10
I am having a problem with my GRUB menu. Actually... its before GRUB boots up. I recently just got VMware Server installed and I got it configured so I can boot into my Windows XP Pro partition. Now, after I did that for a bit, I had to restart my computer, so I rebooted. Normally, booting into GRUB would take less than 10 seconds. It has taken more than 10 minutes just to boot into GRUB!! Can anyone here tell me why it is doing this?

---

### Post by UnknownFear on 2008-05-10
Does anyone know of anything I can do to try and fix this? I really hate having to wait 10 minutes for GRUB to boot up.

---

### Post by spiderbatdad on 2008-05-10
Edit the file /boot/grub/menu.lst

remove '--queit splash' from the end of the line beginning with the word 'kernel' in the section that begins ####END DEFAULT OPTIONS####.

That way you will get some feedback. Perhaps you can see where the process is hanging, and then we can fix it.

---

### Post by UnknownFear on 2008-05-10
> **spiderbatdad said:**
> Edit the file /boot/grub/menu.lst

remove '--queit splash' from the end of the line beginning with the word 'kernel' in the section that begins ####END DEFAULT OPTIONS####.

That way you will get some feedback. Perhaps you can see where the process is hanging, and then we can fix it.

That did it. Booting into GRUB is now faster. Thanks for the help!!

---

