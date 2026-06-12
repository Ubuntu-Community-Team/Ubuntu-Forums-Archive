---
title: "everything has an unmet dependency"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by suvam8694 on 2012-07-17
i tried installing the device driver for ZTE MF190 usb 3g dongle to access the internet. the error i received was that it requires qt3 runtime library. i got it from packages.ubuntu.com but while installing that i got another error that qt3 requires libc6 >=2.4. i got that too but then libc6 required libgcc1 which in turn required something else. what should i do. i have no access to internet on ubuntu as i was installing the 3g dongle device driver for accessing the internet. :confused: 
Please help me. wifi is not working on my laptop so please don't ask me to use wifi instead.
thanks in advance.

Ubuntu 12.04 
HP 630 Notebook PC

Also the wifi is not working. the hardware switch is on. when i turn the wifi on using the network menu nothing happens it automatically goes back to off.

---

### Post by madjr on 2012-07-17
what version of ubuntu are you using ?

---

### Post by anewguy on 2012-07-17
You could try:

sudo apt-get build-dep <package name>

where you put the actual package name for qt3 in place of the <package name> string.  Apt will then try to install everything to meet the dependencies.  Doesn't always work, but it can help you get out of a nested dependencies problem.

---

