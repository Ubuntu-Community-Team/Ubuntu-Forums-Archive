---
title: "Install ubuntu"
date: 2018-08-08
forum: New to Ubuntu
---

### Post by superepic on 2018-08-08
Hello everyone, I have a netbook LENOVO YOGA 330 (came with windows) and I was trying to install ubuntu, but when booting the first thing that appears is the following message:

COULD NOT OPEN "EFI / BOOT / fallback.efi": 14

enter the bios and the only option that has is the UEFI, I tried with SECURE BOOT enable and disable and nothing, I keep appearing the same message.

Does anyone know how to solve it?

Greetings.

---

### Post by wildmanne39 on 2018-08-08
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by oldfred on 2018-08-08
Is that booting live installer, or after install?

You probably want UEFI Secure boot off, but UEFI on or first boot option.

If after install post this:
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)  
    
If not able to boot live installer, check that download was correct  and flash drive properly configured, not a copy of ISO.

---

### Post by superepic on 2018-08-09
Hello, oldfred .... is a livecd with installation option, but the error appears at the beginning, it is the first thing that the screen shows. it does not show the grup, it does not show the desktop, the first screen is the error.

i try with Secure boot off and on and nothing.

PD: the netbook has win10

---

### Post by oldfred on 2018-08-09
Could be bad download or incorrect configuration on flash drive.
Did you check md5sum on ISO you downloaded?
And what tool did you use to extract & copy ISO files to flash drive?

Is this an older UEFI system? If so see if Lenovo has an UEFI update.

Once installed you may have this issue.
[https://forums.lenovo.com/t5/Linux-Discussion/No-trackpad-in-Ubuntu-on-330-15IGM-81d1/td-p/4128611](https://forums.lenovo.com/t5/Linux-Discussion/No-trackpad-in-Ubuntu-on-330-15IGM-81d1/td-p/4128611)
[https://askubuntu.com/questions/1049787/lenovo-ideapad-330-touchpad-not-working/](https://askubuntu.com/questions/1049787/lenovo-ideapad-330-touchpad-not-working/)

---

