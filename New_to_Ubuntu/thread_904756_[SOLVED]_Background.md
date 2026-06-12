---
title: "[SOLVED] Background"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by bj218 on 2008-08-29
I have tried 3 times to change the background and each time when I reboot 
the default background is back. How can I make my background be there when I reboot?

---

### Post by Crafty Kisses on 2008-08-29
Try this: run ```
gconf-editor
``` and edit ```
apps/nautilus/preferences
``` and tick or clear **show_desktop**. Try also toggling **show_desktop** and see if that does anything.

---

### Post by rogeriopvl on 2008-08-29
that's weird. It shouldn't behave like that. Are you changing it from  firefox? or from the background option of ubuntu?

---

### Post by Crafty Kisses on 2008-08-29
Yeah, I'd also like to know, do you have desktop effects on?

I'd also like to see this output:
```
glxinfo
```

---

### Post by bj218 on 2008-08-31
> **rogeriopvl said:**
> that's weird. It shouldn't behave like that. Are you changing it from  firefox? or from the background option of ubuntu?

In Ubuntu I go to Preferences then to Appearance then clk on the Background
tab then clk "+Add" then in the "Add Wallpaper" window I drag and drop a 
picture from my floppy drive. The main Ubuntu window then shows my picture it also appears in the Background Window along with all the other background selections.

---

### Post by billgoldberg on 2008-08-31
> **bj218 said:**
> In Ubuntu I go to Preferences then to Appearance then clk on the Background
tab then clk "+Add" then in the "Add Wallpaper" window I drag and drop a 
picture from my floppy drive. The main Ubuntu window then shows my picture it also appears in the Background Window along with all the other background selections.

That is because Ubuntu can't access the picture when you boot up.

The floppy isn't mounted, so Ubuntu changes to the default one.

Just copy the picture somewhere on your harddrive (places -> pictures).

---

### Post by OutOfReach on 2008-08-31
Yeah, Ubuntu will look for the picture in the location that it came from, you should try to move your picture into a directory like Pictures and set it as the background from there.

---

### Post by bj218 on 2008-09-02
> **billgoldberg said:**
> That is because Ubuntu can't access the picture when you boot up.

The floppy isn't mounted, so Ubuntu changes to the default one.

Just copy the picture somewhere on your harddrive (places -> pictures).

Thank you, I did as you suggested and I now have the picture I wanted each time I bootup.

---

