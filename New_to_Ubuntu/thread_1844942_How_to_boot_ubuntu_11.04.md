---
title: "How to boot ubuntu 11.04"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by Kracer on 2011-09-16
I have set up a boot loader to include ubuntu but where should I point the bootloader to start ubuntu.
In the windows it's going to an exe file, but for ubuntu it's trying to find a file that doesn't exist I can see be ause I mounted the linux partition in windows.
Thanks in advance

---

### Post by pytheas22 on 2011-09-16
How did you install Ubuntu?  Normally the installer takes care of setting up your bootloader for you and you should not have to do anything else.  If it detects that Windows is installed on the computer it will make an entry for you to boot that as well.

As far as I know, the Windows bootloader can't boot Linux; instead, you need to make your computer boot to the grub (or LiLo) bootloader first, which can then either boot Linux or chainload the Windows bootloader so you can boot Windows.  This is how the Ubuntu installer will configure things by default.

---

