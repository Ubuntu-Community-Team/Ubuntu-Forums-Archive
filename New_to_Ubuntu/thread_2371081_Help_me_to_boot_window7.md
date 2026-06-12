---
title: "Help me to boot window7"
date: 2017-09-10
forum: New to Ubuntu
---

### Post by iankitgupta on 2017-09-10
First i install win7 64 bit.
Than i try to install ubuntu 14 lte version . 
It was not installing so i create another partition of 15GB . 
Now I'm not able to boot window 7 ,  it directly boots ubuntu .
I tries installing grub but window 7 was not listed there . I'm new here .
Please anyone help me ,im stuck here .
Detailed report is here .

[http://paste.ubuntu.com/25507397/](http://paste.ubuntu.com/25507397/)

---

### Post by deadflowr on 2017-09-10
Well, not much to say except you wiped the Windows 7 install when you installed Ubuntu.
You might try again,
here's some light reading:
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by oldfred on 2017-09-10
Did you install Windows in BIOS mode to MBR partitioned drive and then install Ubuntu in UEFI boot mode converting drive to gpt and in effect erasing Windows?

The Windows 7 DVD installer is BIOS only. You have to copy to flash drive and move/rename a couple of boot files to make them work for UEFI.
The BIOS/MBR configuration is now 35 years old, so probably better to install in UEFI mode if you have new UEFI hardware.

How you boot install media UEFI or BIOS, for both Windows & Ubuntu is how it installs.
 Only 64 bit supported for UEFI boot, Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
rem === Copy boot files to the System partition =========
W:\Windows\System32\bcdboot W:\Windows /s S:\Windows\Boot\EFI 

For Ubuntu UEFI install info see link in my signature.

---

