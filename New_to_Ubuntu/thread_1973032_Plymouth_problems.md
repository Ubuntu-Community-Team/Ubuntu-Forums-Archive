---
title: "Plymouth problems"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by kryten2k35 on 2012-05-04
Ok, so I installed Super Boot Manager and started playing with Plymouth.

I also installed the NVidia resolution fix which actually restored my Plymouth back to what it was prior to the properiatory drivers.

I then used SBM to create a theme of my own, inserting a background image and logo to use. This failed.  So, I opened up /lib/plymouth/themes/ and found the default Plymouth theme for my distro and replaced the background image with one I wanted to use. This caused problems, not sure what, but I was back to text only plymouth.

So, using SBM I downloaded and installed another theme. I clicked the "show splash" or whatever it is and the preview windows opened up showing the correct splash screen I'd picked. So I rebooted to test this and sure enough when shutting down the screen I'd chosen shows. Then when it was rebooting, it loaded GRUB (Loading GRUB...) and displayed an error message too quick for me to see what it was I jsut caught "Fatal Error" and it shows the text plymouth splash :(

If I reset the splash using SBM, sure enough on shutdown it's thtere but on reboot it's dead.

What can I do to restore this?

---

### Post by kryten2k35 on 2012-05-04
Such an idiot!

I had put vga=1680x1050 into the grub commands after installing the fix. I JUST managed to catch a glimpse of the error saying something about vga (or vesa... was going out on a wing). Removed that line and got it working ok =D

---

