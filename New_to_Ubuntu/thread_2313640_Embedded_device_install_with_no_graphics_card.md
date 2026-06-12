---
title: "Embedded device install with no graphics card"
date: 2016-02-14
forum: New to Ubuntu
---

### Post by ashley17 on 2016-02-14
HI guys.
Newbie here lol.
Im looking to install ubuntu (preferably server) to an embedded device with only 512MB flash ( I can add a CF card or usb stick to improve storage).
I would like to add a web based gui to add later if possible.
It has 2 nic's and is running ssh server to connect to it and ftp server to upload files.
It has kernel 2.6 and drivers but nothing else.
Other peripherals are wireless, gps, usb and RS232.

Would like to be pointed in the right direction.
Any help would be great and being a newbie to linux in general I want to learn.

Thanks all.

---

### Post by ian-weisser on 2016-02-14
My advice: Separate learning-about-linux from the embedded device project.

1) Learn about Linux using a Virtual Machine (VM). Install Ubuntu Server 14.04 in a VM and play with it. Learn how package management works. Learn good security habits. Learn how to maintain it. Learn how to set up a web server. Break it and fix it.

2) Build a test server in a VM using the Minimal Install image, which creates a much slimmer install...but is easier to break and harder to fix. This is your rehearsal for installing onto an embedded device. Measure your size and ensure your prototype system will fit on your device.

3) Based on your experience, installing onto the embedded device will be much easier.

---

