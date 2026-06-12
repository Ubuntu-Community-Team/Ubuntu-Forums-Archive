---
title: "Logging in twice"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by pete_zahuat on 2008-05-12
When I log in (the first time), the screen changes and shows some boot sequences (which lasts for about 2 seconds), then goes back to the log in screen again.

Also, I went into grub to see if I could find the problem, and I noticed that when I pressed 'esc' that I had about 10 choices to choose from. Weird thing is, I am not doing a dual boot and the choices just seem to repeat themselves. I did not know if the multiple boot options affected the login screen or not, but just thought it might help.

---

### Post by pete_zahuat on 2008-05-12
Oh I forgot to mention I am using 8.04

---

### Post by Inxsible on 2008-05-12
> **pete_zahuat said:**
> When I log in (the first time), the screen changes and shows some boot sequences (which lasts for about 2 seconds), then goes back to the log in screen again.

Also, I went into grub to see if I could find the problem, and I noticed that when I pressed 'esc' that I had about 10 choices to choose from. Weird thing is, I am not doing a dual boot and the choices just seem to repeat themselves. I did not know if the multiple boot options affected the login screen or not, but just thought it might help.The multiple choices could simply be because you may have installed multiple kernels. This also happens if you haven't cleaned up your grub menu since newer OS updates will most likely also update the kernel. The old entries are not removed during this update.

---

