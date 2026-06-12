---
title: "[SOLVED] eeepc &amp;quot;live cd&amp;quot; booting to busy box prompt"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by t0p on 2008-09-25
I've followed the instructions at [www.pendrivelinux.com]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/") to install a live cd image of ubuntu 8.04.1 to a usb flash stick.  Then I've stuck the usb stick into my eeepc, and booted it.  But, after a very long boot, it's booting to a busy box prompt instead of the gnome desktop I expected.

---

### Post by Vakman on 2008-09-25
When it offers you a choice at the start of like "Start Ubuntu With No CHanges To Your Computer" etc.
Press F6 for "More Options" and then it will let you edit the boot after it says "quiet splash" or something similar add "--all_generic_ide" without the quotes. Try it out. I know it worked for my laptop.

---

### Post by t0p on 2008-09-25
> **Thisislaw said:**
> When it offers you a choice at the start of like "Start Ubuntu With No CHanges To Your Computer" etc.
Press F6 for "More Options" and then it will let you edit the boot after it says "quiet splash" or something similar add "--all_generic_ide" without the quotes. Try it out. I know it worked for my laptop.

Thanks for the tip... but it didn't work. :(  Anyone else got any ideas?

---

### Post by t0p on 2008-09-26
Well, I managed to resolve my problem.  The live cd .iso image that I transferred to the usb stick was faulty.  I followed alternative instructions, at [this link]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/") - it involved downloading an .iso from ubuntu.com, which I'd hoped to avoid - and this resulted in a working live usb stick.  Cool! :)

So, I've got a live session of hardy working on my eepc now.  And later I'll install it to the eeepc's ssd.  Ubuntu on my eeepc!! Heh heh!! Now I just gotta get the wireless and the webcam working...

---

