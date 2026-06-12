---
title: "Boot option not included USB after fully installed in USB"
date: 2019-03-18
forum: New to Ubuntu
---

### Post by lauchokyip on 2019-03-18
I have followed the steps from [https://www.youtube.com/watch?v=YIhYitXwJfE&t=1s](https://www.youtube.com/watch?v=YIhYitXwJfE&t=1s). But the USB is not showing on my boot option.

  *Here is what I have done:*
  1) I downloaded Ubuntu desktop  and installed it on my **4GB USB drive** using **Rufus**
  2) I then installed the ubuntu OS into my **64GB USB drive** from the **4GB USB drive**

  3) Then I tried to access the boot option menu after I finished installing it only showed me the windows boot manager
  PS: **I have tried to plug in the 4GB USB drive and it was  shown on the boot option mene. I also tried doing this on debian 9 but  no luck. It will only showed the 64 USB drive if I used rufus to burn  the Ubuntu desktop into**

---

### Post by yancek on 2019-03-18
Can you access the BIOS on boot and change boot priority to the 64GB drive?  You should see a message on screen when you boot telling you which key to use as this varies with manufacturer.
Which version of windows was/is installed?  Is it UEFI?
Did you do an EFI install of Ubuntu?  Did you create an EFI partition on the USB first?  Or did you do a Legacy install?  Might be best to post more information from boot repair.  See the link below.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by lauchokyip on 2019-03-19
I have done UEFI install. This is the discussion I have started [https://askubuntu.com/questions/1126674/boot-option-not-included-usb-after-fully-installed-in-usb-with-uefi](https://askubuntu.com/questions/1126674/boot-option-not-included-usb-after-fully-installed-in-usb-with-uefi)

---

### Post by QIII on 2019-03-19
yancek's first question in their response is important.  Answering that would be helpful in diagnosis.

---

