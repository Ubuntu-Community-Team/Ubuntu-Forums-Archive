---
title: "Grub display size on start up"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by Nosphky on 2014-04-20
I have a dual boot setup for Windows7 and Ubuntustudio 13.10 with Grub2.    On startup and on reboot, about 90% of the time, the grub choices are displayed in six lines of very small text on the top left on the screen.  About 1 in 10 times, these options are displayed in a much larger text roughly centred vertically and horizontally on the screen.

Why wouldn't the boot choices be displayed 100% of the time in the same fashion?    It is as though some sort of race condition exists between at least 2 processes and usually 1 wins but sometimes the other gets there first.

I prefer the larger, centred, display.   Is there a way to make sure that this always occurs?

---

### Post by hamishmb on 2014-04-20
There is a way found here: [http://askubuntu.com/questions/127851/change-boot-screen-resolution](http://askubuntu.com/questions/127851/change-boot-screen-resolution)

I've done this before, so I'm pretty sure it'll work :)

Hamish

---

### Post by Nosphky on 2014-04-21
Thank you Hamish for the response.  I followed your link and carried out the changes it suggested but this didn't provide the outcome I was hoping for.  At the first reboot, the grub menu options were still in small size at top left of screen.

I selected Windows and got a screen full of giant sized stuff but subsequent reboots were back to normal - small grub menu in top left of screen and boots into Ubuntu or Windows proceeded normally.

---

