---
title: "Mobile phone Android emulator"
date: 2020-10-12
forum: New to Ubuntu
---

### Post by nginmu on 2020-10-12
It would be handy to be able to install Android mobile phone apps from the Google Play store, on my nice big desktop machine. Is there an easily installable emulator out there that will run on Lubuntu 20.04? 

The simpler the better, just to appraise / play about with, the odd app.. no need for full feature developer options. I read suggestions in old threads about installing Android as a VM but not sure what the latest advice would be.

I find the phone itself a bit fiddly, only ever use it when I have to really, guess that just comes from age!

Am I opening a nasty can of worms here..

---

### Post by tea for one on 2020-10-12
Not really answering your question but here is something to consider:-

[https://www.android-x86.org/](https://www.android-x86.org/)

---

### Post by nginmu on 2020-10-12
From android-x86.org

> You can easily test the iso file by a virtual machine like [virtual box]("https://www.android-x86.org/documentation/virtualbox.html") or [qemu]("https://www.android-x86.org/documentation/qemu.html"). Alternatively, on a Linux host you can use the qemu-android script (available since nougat-x86) to run android-x86 in qemu directly

That sounds interesting, thanks for the link

edit.. found this page useful [https://www.instructables.com/Creating-an-Android-Emulator-Using-Qemu/](https://www.instructables.com/Creating-an-Android-Emulator-Using-Qemu/)

---

### Post by TheFu on 2020-10-12
Another option is to use a direct connection to your android devices over usb.
```
sudo snap install  scrcpy
```
Audio plays on he phone, but video and your mouse on the Linux system. No emulation.  Screen recording possible.

I did android development for a few months.  The hardware requirements were pretty steep and running was 100x slower than native.

---

