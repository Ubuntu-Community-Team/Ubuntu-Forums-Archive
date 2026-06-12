---
title: "help for ubuntu installation"
date: 2024-09-16
forum: New to Ubuntu
---

### Post by aureta on 2024-09-16
Hi, I am trying to install ubuntu in an hp envy intel core i3 windows laptop. I watn to erase windows from it and install ubuntu instead. I followed instructions from the web on how to proceed 
making a bootable usb drive using rufus. When going through the steps setting the bios and start the installation of ubuntu, I get two errors messages upon clicking "Try or Install Ubuntu" in the pc system window. The messages are: 
error: file "/casper/val inuz" not found
error: you need to load the kernel first

I would appreciate help to install Ubuntu, thanks...

Alejandro.

---

### Post by TheFu on 2024-09-16
"/casper/val inuz" is a typo - either by you or in the distro/download you have.  Download it again and please validate the ISO using the **sha256sum** program to ensure it isn't corrupted.

Using the "Try Ubuntu" method is always recommended so you can see that everything works (audio, video, mouse, keyboard, networking, touchpad) - those are the big items.

I'd strongly recommend using a 22.04 flavor, not 24.04, at this point.  There seem to be some things in 24.04 that are impacting more people than normal.  22.04 support for the flavors will go to at least next April, but probably June/July. In those extra months from today, 24.04 will become better and better.

And if that doesn't work, there are other beginner friendly Linux distros that are very much like Ubuntu which are worth considering.

---

### Post by ActionParsnip on 2024-09-17
You can use torrents to add extra error checks to the ISO. Could also try a different USB stick / SDCard etc

---

