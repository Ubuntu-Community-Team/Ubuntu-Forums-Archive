---
title: "Is logging USB communication possible?"
date: 2008-09-05
forum: Programming Talk
---

### Post by xolot1 on 2008-09-05
Im looking to extract the data off of a Nike Sportband (pedometer watch), which connects via USB.  As far as I know, it has yet to be reverse engineered, yet I'd really like access to the data.  There is a proprietary Nike application that extracts the data and uploads it to their website.

Id like to start by watching the communication between the device and the original application, if possible.  

Is there a way to create a pipe or middle layer between two USB sources?  Is it feasible to write a program that logs this communication?

I know, for example, that VMWare can pass USB devices to the client OS.  Can I emulate this? Im open to any sort of creative ideas or suggestions. Its mostly just an experiement...

---

### Post by rnodal on 2008-09-05
My best guess would be that you have to code something in the kernel.

-r

---

### Post by Mister.Vash on 2008-09-05
Check the tools section here for USB Sniffers:
[http://www.linux-usb.org/](http://www.linux-usb.org/)

---

