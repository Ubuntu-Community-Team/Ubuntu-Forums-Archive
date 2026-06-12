---
title: "Broadcom STA driver not installing on LiveUSB"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by Aftrumpet on 2012-09-09
Since I do not have a computer of my own at the moment (using my family's computer) I do not have the ability to install Ubuntu on a hard disk so I'm planning on just running it from a USB for now. However, I cannot get wireless working on this USB (12.04.1). When I open the "Additional Drivers" window and install the Broadcom wireless driver, I am prompted to restart my computer to activate it, but when I restart, the driver is not activated. Does anyone know how to fix this?

---

### Post by yeats on 2012-09-09
This depends on how you created the USB.  If you created it to be a "live" USB, it will not store any changes you make.  You'll need to create the USB to be "persisent".  A google search of "ubuntu persistent usb" should put you on the trail of some tutorials.

---

### Post by Aftrumpet on 2012-09-09
I created it with pendrivelinux and selected a persistent file size of about 800mb, does that make it persistent or do I have to do something different?

---

### Post by MARP1961 on 2012-09-09
There are numerous posts on Broadcom drivers! Since early in the 10.04 Lucid Lynx cycle, I have never managed to get success with the STA driver and invariably have to install the B43 Firmware Installer via Synaptic. 'Additional Drivers' just makes things worse because if you install STA as it suggests it will then unhelpfully blacklist B43.

---

