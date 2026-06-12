---
title: "Installing windows along ubuntu on a GPT HDD"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by Nabeel Abbas on 2014-02-07
I am running 13.10(x64) on my latitude E4310. Now I tried installing windows from a DVD to achieve dualboot but nearly every disk I tried gave me this*"Windows cannot be installed to this disk. The selected disk is not of the GPT partition style"* error. Now I suspect my optical drive don't support uefi boot. Is there any way to install windows now???

---

### Post by oldfred on 2014-02-07
Windows only installs to gpt partitioned drives with UEFI boot. And how you boot install media is how it installs.

Is your system UEFI capable? 
Windows 7 DVD is BIOS only but you can convert it to UEFI by copying to flash drive and doing some updates.
Or you have to convert drive to MBR(msdos) and install in BIOS mode.

       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

    
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

