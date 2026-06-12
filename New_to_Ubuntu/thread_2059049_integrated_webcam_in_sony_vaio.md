---
title: "integrated webcam in sony vaio"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by dougmoffatt on 2012-09-17
I am running XP in Virtual box on Ubuntu 12.04. Ubuntu recognises the integrated webcam but XP in vbox doesn't. Are there some settings in vbox I should be aware of? or is it something else? I am wanting the webcam to run Skype.

---

### Post by dougmoffatt on 2012-09-17
I am running XP in Vbox on Ubuntu 12.04 and it doesn't recognise USB devices, although they are recognised in Ubuntu.  Is there some setting(s) I should know about in Vbox?

---

### Post by overdrank on 2012-09-17
Hi and please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by Cheesemill on 2012-09-17
You need to install the VirtualBox extension pack on the host and the VirtualBox guest additions on the guest for full USB functionality.

[Extension Pack]("https://www.virtualbox.org/wiki/Downloads")

[Installing Guest Additions]("https://www.virtualbox.org/manual/ch04.html#additions-windows")

---

### Post by newb85 on 2012-09-17
I've got 12.04 running on VB inside 12.04 (for testing purposes) on my Toshiba, and it doesn't look like the virtual machine is recognizing my built-in webcam, either.  I'm guessing it's either a setting or a limitation in VB.

---

### Post by newb85 on 2012-09-17
There's a setting in VB to enable the USB 2.0 controller, and it's turned off by default.  That might be the culprit.

---

