---
title: "Cannot boot from flash drive"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by Nmaster400 on 2013-06-28
So I got a computer with Windows 8 preinstalled, so I have UEFI on it. I don't like Windows 8 so I decided to try Ubuntu, because it seems like I might like it. I used the Universal USB Installer to burn the ISO to a flash drive, and I used Ubuntu 13.04. I'm not that tech-savvy so please excuse my stupidity and possible ignorance. So I went into my BIOS settings and disabled Security Boot and Fast Startup, and I can't get it to boot from the flash drive. I tried using advanced startup, changed the startup priority, and even tried Wubi, although I knew it wouldn't work. So if I'm doing something totally ignorant please tell me and excuse my stupidity. Thank You.

---

### Post by C.S.Cameron on 2013-06-28
You need to install Ubuntu 64 to use a flash drive with UEFI.
If you need persistence let me know.

---

### Post by Nmaster400 on 2013-06-28
I used the 64-bit download.

---

### Post by oldfred on 2013-06-29
Some computers only boot in CSM/BIOS/Legacy mode, although all should boot with UEFI or with UEFI and secure boot if USB flash drive is configured correctly.

Did you check that download was correct? YOu can verify with md5sum.
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


Are you sure you downloaded the 64bit version. It likes to default to the 32 bit.
 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Some have had to just do it a second time. Some flash drives also have issues. 
Also some USB ports with certain hardware work better than others. Try a USB2 port or just another port.

      
 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)

---

### Post by JDorfler on 2013-06-29
I made the mistake of buying a small laptop, used to be called a netbook, with Win 8 on it.  Since it was just a netbook I went ahead and just deleted it and installed LinuxMint 15 Mate.  However, apparently with that particular system I needed to have a smaller thumbdrive than I was orginally using when I tried originally.  I have also built a newer PC with UEFI.  After installing Win8 I had to go into Win8 reboot menu and tell it to boot into the thumbdrive to install Ubuntu.  

I'm starting to think this whole UEFI business has yet to mature.  Too many differences between systems on how to boot into Linux or other OSes.

---

