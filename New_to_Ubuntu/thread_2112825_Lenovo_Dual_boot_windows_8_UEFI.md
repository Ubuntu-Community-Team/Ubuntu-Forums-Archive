---
title: "Lenovo Dual boot windows 8 UEFI"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by helikart on 2013-02-05
Hi,
I have the same issue of not being able to boot into Windows 8 after installing Ubuntu 12.10.

I followed the instructions on running boot-repair, but it didn't seem to work. My boo-info URL is [http://paste.ubuntu.com/1612892](http://paste.ubuntu.com/1612892).

After I ran boot repair, additional boot options appeared: "Windows UEFI bkpbootmgfw.efi", "Windows Boot UEFI loader", and "EFI/Lenovo/Boot/bootmgfw.efi". I tried them just in case after trying my Windows 8 loader, but now luck.

Any suggestions?

Thank you,

Tom

---

### Post by oldfred on 2013-02-05
Moved to your own thread. Thread you were in was not Lenovo and had multiple drives, so is different.

Have you turned secure boot off?
Have you turned fast boot off?

Another Lenovo thread that also shows Ubuntu installed.
[http://ubuntuforums.org/showthread.php?t=2112406](http://ubuntuforums.org/showthread.php?t=2112406)

And same question. That I do not understand why script is showing two lists of bootable devices. And one shows ubuntu.

Line 965 shows one set with 0018 as default or Windows.
And Line 003 shows 0019 as default or ubuntu

When you go into UEFI from keyboard not Windows menu, do you not see ubuntu as a boot option? And then get grub menu with Windows options that should also boot Windows?

Another Lenovo that worked.
       Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

    But some Lenovo will not work.
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

