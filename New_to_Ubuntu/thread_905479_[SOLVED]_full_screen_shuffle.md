---
title: "[SOLVED] full screen shuffle"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by yamatteo on 2008-08-30
I have Xubuntu 8.04. I can't change screen resolution, and I don't know exactly what is my resolution, even if it is more than 800x600.
Everything works well but when I start a full screen application monitor shuffle. I mean: each pixel line is at his right height, but they are randomly shifted horizontaly. So it is not possible to see nothing but colors.
When I shut down this program everything come normal.


Is there some way to solve it?

---

### Post by Piera88 on 2008-09-02
I have the same problem. I thought it was my computer's fault.
Is there any solution?  :(

---

### Post by aimpau on 2008-09-02
1. Check if your videocard is propriety:
   Applications>>System>>Hardware Drivers

2. Change your Video and refresh settings:
   open a terminal:
   ```

gksu displayconfig-gtk

```

---

### Post by yamatteo on 2008-09-03
In System>>Hardware Drivers there are nothing, so I think I need no proprietary driver.
In the graphic setting I see it's using (ATI Radeon (fglrx)) drivers. When I try to change settings (ie resolution or refresh rate,) and test each time the screen come black for half a second and then come back to previous settings, raising an error : "Configuration test failed: Plese verify the selected devices and configuration".
So, by now, I can't try any other resolution.

---

### Post by yamatteo on 2008-09-03
Even worse. As I told, I tried changing some settings, but it was not possible to test, so (to be safe) I reset to previous resolution and refresh rate. After rebooting, xubuntu started in safe-graphics mode, 800x600, and there is no available setting with higher resolution that works.
Any idea?

---

### Post by yamatteo on 2008-09-04
I solved the problem : moved to Debian.

---

