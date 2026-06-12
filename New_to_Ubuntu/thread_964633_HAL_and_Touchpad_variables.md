---
title: "HAL and Touchpad variables???"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Agrajag27 on 2008-10-31
Okay, I have a Dell m1530 with a "Synaptics Touchpad" and learned a bit about xorg.conf to make changes to it in 8.04.

I've now upgraded to 8.10 (so far so good). Now the touchpad is terribly slow. When I go into xorg.conf there are comments throughout it saying that upgrade manager commented out various sections including the touchpad as it's now handled by "HAL". 

I believe HAL is Hardware Abstraction Layer and that sounds good but how do I now get all my settings set given this change and, at the least, speed up my touchpad?

---

### Post by talsemgeest on 2008-10-31
You could try uncommenting what had been commented out, but make sure you make a backup first. Hopefully it trys to use the xorg.conf first, so it might use the settings.

Worth a try, hope it helps :)

---

### Post by PierreDeKat on 2008-10-31
My understanding is that xorg is no longer the preferred method of configuring your hardware. 

Instead, you will want to create or copy-and-paste an fdi file into your /etc/hal/fdi/policy directory.

But [they give you an example here]("https://wiki.ubuntu.com/X/Config#Input%20Configuration%20with%20HAL") that may be of use.

Otherwise, you might have to wait until Jaunty Jackalope, when they will hopefully have a GUI for configuring hardware.

---

### Post by wgrant on 2008-10-31
Also see [the documentation specific to touchpads](https://help.ubuntu.com/community/SynapticsTouchpad).

---

