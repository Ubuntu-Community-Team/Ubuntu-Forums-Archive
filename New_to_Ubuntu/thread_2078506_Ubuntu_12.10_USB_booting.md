---
title: "Ubuntu 12.10 USB booting"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by Ububtuser44 on 2012-10-31
Currently booting Ubuntu 12.10 from a usb drive. Installed through LiLi USB Creator. Has 3gb persistence. But everytime I boot the OS form my pd it starts with setting as if it were a fresh installation every time. Starting from keyboard setting selection to "Try Ubuntu" or "Install Ubuntu on drive" everything shows up. And all this takes a lot of time to load. What can I do to stop this?

Installed Ubuntu from - ubuntu-12.10-desktop-i386.iso

---

### Post by newb85 on 2012-10-31
What you're describing is normal behavior for a Live USB.  Ubuntu isn't really "installed" on that USB in the traditional sense, and that's the main reason it loads so slowly.  The keyboard selector and "Try Ubuntu", etc. are the Ubiquity installer.  That's included because one of the main reasons people use Live USBs is as installation media.

I think I remember reading somewhere that Ubiquity could be uninstalled from a Live USB, but I can't find that thread at the moment.

If you want things to load more quickly, it is possible to install to a USB in the more traditional sense.  It will require at least an 8GB USB drive.  Also, you will have to have other installation media (i.e., either a Live DVD or a Live USB that's different from USB you're installing to).

---

