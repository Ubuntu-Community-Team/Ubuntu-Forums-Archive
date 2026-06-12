---
title: "Installing Ubuntu ..."
date: 2012-10-19
forum: New to Ubuntu
---

### Post by Abhilash Goyal on 2012-10-19
hello everyone ... I have SONY Vaio VPCEH series Laptop with original window7(HB), would it cause problem if i install Ubuntu in my Laptop ... Pls Help ...

---

### Post by Cheesemill on 2012-10-19
It shouldn't be a problem, I should think that most people here on the forums dual-boot.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by newb85 on 2012-10-19
Hi, welcome to the forums and (if you proceed) to Ubuntu!

Adding Ubuntu shouldn't be a problem.

The way you install should depend on how you envision yourself using Ubuntu.

Dual-Boot: When you turn your computer on, you choose either Windows or Ubuntu.

VM Client (like VirtualBox): Running Ubuntu like a program inside Windows.  This means sharing resources with Windows, but it does give you the flexibility of switching back and forth without restarting the machine.

Windows Installer (Wubi): Kind of like dual-boot, but a little easier to install (sometimes).  However, it leaves Ubuntu as a slave to Windows in two respects: it uses Windows' sub-optimal filesystem, which will hurt performance (speed and fragmentation), and it uses Windows' bootloader, which will hurt stability (if you uninstall or upgrade Windows or Windows dies, you will likely lose Ubuntu).  Technically, it is a VM client, but it loads instead of the Windows environment, so it doesn't give you the flexibility of easily switching back and forth.  Wubi was designed for "trying out" Ubuntu.  Some use it for long-term installs (many with success), but I wouldn't recommend it.

---

