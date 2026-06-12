---
title: "Boot into terminal without grub"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by llakais on 2011-10-30
Hello everyone,

I'm running Oneiric Ocelot and my Xorg.conf is messed up to the point where the screens are useless and so I need to boot into a terminal to copy over to my backup configuration. However, I do not have grub and so there appears to be no option to do that. Am I completely screwed or does anyone have any ideas?

Thanks so much for your help!

-llakais

---

### Post by wojox on 2011-10-30
Use a live cd or usb, just something live. Why do you have no grub?

---

### Post by llakais on 2011-10-30
I have the live cd that I installed from, will that help? I don't know why I don't have grub, it just doesn't come up during boot - just goes straight to the splash screen with no option for anything else.

---

### Post by wojox on 2011-10-30
Reboot and hold down the left shift key should work. Yes your install CD will work.

---

### Post by antoinethewiz on 2011-10-30
CTRL + ALT + F2 should get you to console. If you have no keyboard control (I don't think the keyboard is dependant on Xorg.conf but I may be wrong), press ALT + SYSRQ + R to regain control. You can also kill the graphic session (and consequently all graphics apps) with CTRL + ALT + Backspace. This should also take you to a console.

---

### Post by konsolelover on 2011-10-30
I think you have grub but it doesn't show up because Ubuntu is the only installed OS in your system.To boot in text mode you need to edit your /etc/default/grub file.

---

### Post by antoinethewiz on 2011-10-30
> **konsolelover said:**
> I think you have grub but it doesn't show up because Ubuntu is the only installed OS in your system.To boot in text mode you need to edit your menu.lst file.

Oops... I didn't read that he didn't have GRUB. Yeah, do what this guy says. **feels ignorant**

---

### Post by llakais on 2011-10-30
Holding down left shift got me into grub - you guys were right that I had it but it wasn't showing up because Ubuntu is my only OS.  Everything is fixed now, thanks so much for all the help!

---

