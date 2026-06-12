---
title: "Ubuntu not seeing Windows 7 64 bit home"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by Cody_Tellor on 2014-04-18
Hello,

I got this laptop that was a windows 8.1 now I downgrade (and delete windows 8.1) install windows 7 64 bit home and it's up to date and I want to dual boot it so when I put the ubuntu 14.04 (64 bit) disk and reboot the computer and go it install ubuntu here what I see.

Install type

This computer currently has no detected os. What would like to do?

&#9679;Erase disk and install Ubuntu
Warning: This will delete and files on disk

&#9633;Encrypt the new Ubuntu installation for security
You will choose security key in the next step

&#9633;Use LIM with new Ubuntu installation
This will set up Logical Volume Management. It allows taking snapshot partition resizing.

------------------------------------------------------------------------------------
&#9675;Something else
You can create or resize partition yourself, or choose partition for Ubuntu

                                                          |Quit| |Back| |Install Now|


What should I do I want to keep windows 7 I want to dual boot ubuntu. Than You!

---

### Post by oldfred on 2014-04-18
All those choices totally erase drive.

If system was Windows 8 pre-installed it had gpt partitioning. Windows only boots from gpt drives with UEFI.
But if you used a Windows 7 DVD, it does not have UEFI, so it converted drive to MBR(msdos). But it does not correctly convert.
You can copy Windows DVD to flash drive and convert it to a UEFI install.
Or fix the error that Windows did in not totally house cleaning the gpt data.

Best to confirm that extra gpt data is the issue.
Post this from terminal in live installer.
       sudo parted /dev/sda unit s print

If it shows MBR, but extra gpt data, we can use fixparts to remove backup gpt data. But if drive is gpt and Windows in UEFI boot mode, then fixparts may create more issues than it solves.

---

