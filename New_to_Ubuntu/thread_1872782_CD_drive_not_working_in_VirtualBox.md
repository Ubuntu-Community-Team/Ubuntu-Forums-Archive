---
title: "CD drive not working in VirtualBox"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by Ymurti on 2011-10-31
I have Ubuntu 11.10 and I have installed Oracle VM VirtualBox.
I installed windows 7 in VirtualBox but the CD drive is not working in windows 7 only with Ubuntu. Someone please can help me?
:(

---

### Post by Yayestechlab on 2011-10-31
Try this. In the settings for your VM under storage click on the little CD and a menu will pop up, from the menu choose either the cd drive or an iso file.

---

### Post by veggis on 2011-10-31
in Oracle virtual box

Settings --> Storage in the next windows press Virtualboxguest...... (the little cd-rom in the with window)

and the the CD-ROM to the right with an green arrow on and choose host drive and check passthorugh

---

### Post by Ymurti on 2011-10-31
Dear Yayestechlab and Veggi, Thank You a lot, the CD drive is now working :)
Can I ask you one more thing I have the same problem with USB. When I attach a pen drive I can not see it in Windows 7 in the VirtualBox. Can you help me?

---

### Post by jmszr on 2011-10-31
Ymurti,

         Have you installed the "Extension Pack"? You can download it from here: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads), if you haven't yet. That is needed for USB devices.

Hope that helps.

---

### Post by Yayestechlab on 2011-10-31
In the settings click on Ports then USB then the picture of a usb cord and a plus sign, then from the menu that appears choose the usb device that you want to use in the VM.

---

### Post by Ymurti on 2011-10-31
Dear jmszr,  I do have the "Extension Pack" installed.

---

### Post by Ymurti on 2011-10-31
> **Yayestechlab said:**
> In the settings click on Ports then USB then the picture of a usb cord and a plus sign, then from the menu that appears choose the usb device that you want to use in the VM.

Dear Yayestechlab,  There is no choice in the usb with a plus sign. Here it is a screenshot of the settings.

---

