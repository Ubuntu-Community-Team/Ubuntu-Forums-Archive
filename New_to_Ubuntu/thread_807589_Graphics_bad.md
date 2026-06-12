---
title: "Graphics bad"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by fsixteen on 2008-05-25
I just installed ubuntu on my old computer that has an old optiquest v115 21" monitor and using the built in graphics chip (Unichrome VIA P4M800 Northbridge) on a pc chips p25G motherboard.  On bootup it said it didn't recognize my monitor so I picked the optiquest v115 from the list and set the resolution to 1024x768, but when it booted it was set at 800x600 and only two resolutions were available, 640x480 and 800x600.  I tried rebooting again and this time the screen is so messed up I can't read anything on the screen- its just orange and takes up 2/3 of the screen with a bunch of lines in it.  How can I get it readable again and be able to use a higher resolution.

---

### Post by iaculallad on 2008-05-25
> **fsixteen said:**
> I just installed ubuntu on my old computer that has an old optiquest v115 21" monitor and using the built in graphics chip (Unichrome VIA P4M800 Northbridge) on a pc chips p25G motherboard.  On bootup it said it didn't recognize my monitor so I picked the optiquest v115 from the list and set the resolution to 1024x768, but when it booted it was set at 800x600 and only two resolutions were available, 640x480 and 800x600.  I tried rebooting again and this time the screen is so messed up I can't read anything on the screen- its just orange and takes up 2/3 of the screen with a bunch of lines in it.  How can I get it readable again and be able to use a higher resolution.

Had you tried reconfiguring the Xserver? (You could enter the Recovery Mode - Press ESC key when you see the GRUB on boot time)

Code:
> sudo dpkg-reconfigure -phigh xserver-xorg

---

