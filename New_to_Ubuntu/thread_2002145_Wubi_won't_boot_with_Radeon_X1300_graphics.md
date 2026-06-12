---
title: "Wubi won't boot with Radeon X1300 graphics"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by tjfs on 2012-06-12
I upgraded my graphics card from X300 to X1300. Before, I could install Ubuntu with Wubi just fine. Now, after the initial reboot the screen goes black and never comes back on, which I assume is because there is an incompatibility between Ubuntu and the X1300 GPU. I have tried booting with Safe graphics mode and that doesn't work either.

---

### Post by mastablasta on 2012-06-12
boot and then select nomodeset on boot options in grub menu (i think F6).
 
more here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
not a really good upgrade on the card but let's see if support is better for x1300 :-)

---

### Post by tjfs on 2012-06-12
I'll try that but I'm not sure it's even getting as far as the grub menu. It just goes black.

---

### Post by Mark Phelps on 2012-06-12
IF you upgraded in hopes of getting better graphics support, then you wasted your time.

The X... series of ATI adapters were dropped from restricted driver support years ago.  The last Ubuntu release that supported that was 8.10.

These days, the only driver that supports them is the open-source Radeon driver -- the same driver that you were using to support the X300.

---

