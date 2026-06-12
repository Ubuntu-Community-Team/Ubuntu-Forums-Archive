---
title: "[SOLVED] Keyboard Doesn't Work In Install"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by ModdTaco on 2008-09-30
I'm trying to install Ubuntu Studio. However I can't install it because my USB keyboard wont respond in the setup. (Cant even get passed the Language selection). I have NO PS/2 connector on my PC. Any workaround?

---

### Post by Crafty Kisses on 2008-09-30
If there's anyway you can get this command in Terminal:
```
lsusb
```
Post it back here, and let comes out of it.

---

### Post by ModdTaco on 2008-09-30
How the heck do I get into the terminal?

---

### Post by Crafty Kisses on 2008-09-30
You can try copy and pasting it in the Terminal.

---

### Post by bpalone on 2008-09-30
You might check your computer's BIOS settings.  There may be a setting for USB there and it is turned off.

Just a thought, for what it is worth.

---

### Post by Terl on 2008-09-30
Might want to check your bios to make sure you have the usb turned on at boot.

---

### Post by ModdTaco on 2008-09-30
USB is turned on... Works fine for 98,XP,Vista,OSX. Just not the Ubuntu install screen. I dont think I can access terminal because I thought you had to have Ubuntu installed to use it..

---

### Post by bpalone on 2008-09-30
> **ModdTaco said:**
> USB is turned on... Works fine for 98,XP,Vista,OSX. J.

Those are Operating Systems and they have their own drivers for the USB.  The BIOS provides the first software for the hardware to communicate with each other.  If it is turned off in the BIOS the hardware is not aware of any USB devices.

The hardware and the OS haven't reached the point to hand off the USB devices yet.  The OS is only barely there, just enough to get itself installed.  So, check the BIOS setting.

---

### Post by ModdTaco on 2008-09-30
I know those are OS's. I'm saying the hand off is NOT the Bios problem. It's worked for ever other Linux distro just not the Ubuntu setups. I found a work around for now.

---

### Post by Crafty Kisses on 2008-09-30
Were you able to test your keyboard layout in the beginning?

---

### Post by ModdTaco on 2008-09-30
No... It would not even let me select my language. It seems I can't use the graphical installer with my USB keyboard. The workaround is to NOT load the GFX installer and go old school... Worked and now im running Ubuntu Studio... Sweeeet...

---

