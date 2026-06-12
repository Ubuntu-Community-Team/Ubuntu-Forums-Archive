---
title: "Crosscompiling questions"
date: 2011-10-25
forum: Programming Talk
---

### Post by Jagdeep Bhoria on 2011-10-25
Hi All,
 
Sorry for writing in here. Could not find, how to create a new thread.
 
I am new to LINUX.
I want to set up a cross compiler on Ubuntu machine(v10.10).
I have the native GCC compiler version 4.4.5. Now my requirement is that I have a C file that I need to first cross compile and then have to run on ARM device(probably on ARM7).
 
Can anybody help me out???
 
I also want to know how to cross compile a C/C++ file and how to run the output file obtained after cross compile.
 
Regards,
Jagdeep

---

### Post by thatguruguy on 2011-10-25
--redacted, because the thread has been moved --

---

### Post by CharlesA on 2011-10-25
Post moved to it's own thread in PT.

---

### Post by gsmanners on 2011-10-25
> **Jagdeep Bhoria said:**
> I am new to LINUX.
I want to set up a cross compiler on Ubuntu machine(v10.10).
I have the native GCC compiler version 4.4.5. Now my requirement is that I have a C file that I need to first cross compile and then have to run on ARM device(probably on ARM7).

I think I would try out [QEMU]("http://www.qemu.org/") and see whether I could get a gcc toolchain running on that. That may be your best bet for compiling ARM at this point (unless your device has gcc installed on it). See: [http://www.aurel32.net/info/debian_arm_qemu.php](http://www.aurel32.net/info/debian_arm_qemu.php)

---

### Post by Liiiim on 2011-10-25
Unless I'm totally misunderstanding the question, won't [gcc-arm](http://packages.ubuntu.com/oneiric/gcc-4.4-arm-linux-gnueabi) do what you want?

---

### Post by gsmanners on 2011-10-26
This kind of thing is fairly new, so...

/me looks around a bit

Here's the Ubuntu QEMU method: [https://wiki.ubuntu.com/ARM/BuildArmPackages](https://wiki.ubuntu.com/ARM/BuildArmPackages)

This is probably closer to what you're looking for.

---

