---
title: "Pixel smudges on new Ubuntu"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by kakibula on 2013-03-21
Hello. I am very new to linux. just installed Ubuntu 12.10 and Mate 1.4.2.
I noticed pixel smudges when i m working on it and it really is annoying.
See attached screenshot (you ll see the text smudges next to the mouse cursor).
How can i fix this ? thanks.

---

### Post by ManamiVixen on 2013-03-21
This is a bug with the open source Nvidia driver. It possibly affects the ATI one, not sure on that one. You'll have to install the proprietary driver for your graphics. If you have intergrated Intel, I'm not sure whats up with it if thst is the case. There should be no issues with Intel.

---

### Post by kakibula on 2013-03-21
I have Nvidia Geforce GTX 460.
Is there a non-open-souce driver for this for linux ?

---

### Post by ManamiVixen on 2013-03-21
"sudo apt-get install nvidia-current" SHOULD work. It's not uncommon for the driver to screw over an Ubuntu install. Just hope and cross your fingers that it will work with no issues. But that is the Proprietary driver provided Nvidia.

---

### Post by howefield on 2013-03-21
Make sure that you also have the kernel headers installed before installing the nvidia driver.

---

### Post by kakibula on 2013-03-22
Thanks a lot.
it solved my problem !

---

