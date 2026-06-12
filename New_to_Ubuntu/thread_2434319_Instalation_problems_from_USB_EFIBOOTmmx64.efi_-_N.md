---
title: "Instalation problems from USB \EFI\BOOT\mmx64.efi - Not Found"
date: 2020-01-03
forum: New to Ubuntu
---

### Post by natastar on 2020-01-03
Hi, I'm trying to install 18.04.3 on a new desktop. I started the installation from a USB, got to the part where you choose Logical Volume Management or something else and then looked for more information. I hadn't partitioned first in Windows so I aborted that installation and partitioned. USB will now not load again. Message is
Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\mmx64.efi: Not Found
Failed to start WokManager: Not Found
Something has gone seriously wrong: import_mok_state() failed
: Not Found

I created a new USB start up on a different stick and got the same message.

I tried to burn iso to a DVD and got errors at all speeds so burned Kubuntu 18.04.1 to DVD which worked, but then would not boot and windows just boots.

Very grateful for any help please

---

### Post by oldfred on 2020-01-03
The mmx.efi is to manage UEFI Secure boot keys. That normally is only required if you have UEFI Secure boot on and have proprietary drivers like nVidia. With proprietary drivers Ubuntu cannot provide a Secure boot key, but a user can, if he trusts the software or compiles his own driver.

Quick fix is to just copy grubx64.efi and rename to mmx64.efi. You will get a correct mmx64.efi in your system once installed.

It may be that some software to create live installer does not also copy mmx64.efi? What did you use to create live installer?
       Rufus Create bootable USB drives the easy way  From Windows create Linux installer may have mmx64.efi error
rufus  select gpt (uefi non csm) 
    
       System fails to boot with \EFI\BOOT\mmx64.efi - Not Found
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171) 
    
What brand/model system or motherboard?
What video card/chip?
Some need extra boot parameters.

General UEFI install info in link below in my signature.

---

### Post by georgesoto1 on 2020-04-05
This error appeared for me when I restarted my PC, I’ve changed my USB but not sure how I can change it on the PC as it turns on displays the message and turns off. Any help would be much appreciated

---

### Post by oldfred on 2020-04-05
Is it then not booting the USB?
Do you have Ubuntu already installed?
If not the message can only be from USB.

Try turning UEFI Secure Boot off in UEFI setting.

More details on UEFI install in link in my signature.

---

