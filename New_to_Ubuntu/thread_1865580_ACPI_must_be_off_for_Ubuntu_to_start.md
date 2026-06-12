---
title: "ACPI must be off for Ubuntu to start"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by shico90 on 2011-10-20
Hello, My Ubuntu doesn't start until I turn off the ACPI in the grub.
During the installation it kept hangs at
Kernel_thread_helper so I installed with the ACPI off, and now after installation. I have to turn it off.
so what is my problem, please help.

---

### Post by thatguruguy on 2011-10-20
ACPI has been disabled by default in the Linux kernel because it makes certain hardware unbootable.

My guess is, you have that hardware.

---

### Post by shico90 on 2011-10-20
> **thatguruguy said:**
> ACPI has been disabled by default in the Linux kernel because it makes certain hardware unbootable.

My guess is, you have that hardware.
But that happened only since yesterday, last week i was using Ubuntu as usual without making this ACPI off

---

### Post by LinuxFan999 on 2011-10-20
> **thatguruguy said:**
> **ACPI has been disabled by default in the Linux kernel because it makes certain hardware unbootable.**

My guess is, you have that hardware.
I never knew that. I guess my computer will be unable to shut down if I install Ubuntu, and it will halt instead of powering off normally.

---

### Post by thatguruguy on 2011-10-20
Sorry, it is ASPM that is turned off by default by the Linux kernel.  I mixed my acronyms.

---

### Post by /bin/sh on 2011-10-20
If you have windows on another partition then you can try to install linux/ubuntu from wubi: [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

