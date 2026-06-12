---
title: "I installed Ubuntu 18.04 alongside Win10 but my laptop boots directly into Win10"
date: 2018-08-09
forum: New to Ubuntu
---

### Post by mohilkhare on 2018-08-09
Yesterday, I installed Ubuntu 18.04 alongside Win10 and I realized, on booting I was not provided with a choice to choose my OS on booting and it normally booted right into Win10. The only way for me to boot in Ubuntu is to repeatedly tap 'esc' key and then press F9 from boot options, which obviously isn't the right way. I need the community's support so that I get to choose between Win and Ubuntu every time I boot my laptop.

---
Hardware Configs:
Laptop Model: HP Pavilion CC120TX
BIOS Version: F.30
Legacy mode off (Tried by turning on too, doesn't work)
Secured boot off (Tried by turning on too, doesn't work)
Fast boot off (Tried by turning on too, doesn't work)
I'm attaching the screenshot of the full configuration of my system.
[IMG]https://imgur.com/wnAHsaf[/IMG][IMG]https://imgur.com/jz7Dc8W[/IMG]
---
Things I've tried:
1. Used EasyBCD and EasyUEFI to change the boot priority (Putting Ubuntu over Windows): Doesn't work, the old priority gets restored on reboot.
2. On Terminal, I've tried ```
efibootmgr
``` and ```
boot-repair
``` reintsalled the grub, again, the boot order changes on a reboot.
3. On cmd, I've tried ```
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
``` again, doesn't work.
---

I request the experienced and engineers to please help me out with this. It will be a great help.

Thank you

---

### Post by yancek on 2018-08-09
A pre-installed windows 10 version is almost certainly using UEFI.  The official Ubuntu documentation on the subject is at the link below.  Review that and compare it to what you did.  Did you install Ubuntu UEFI?  How to tell if you boot UEFI to insall UEFI is explained at the link below also.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Some basics, if one system is UEFI, both (or all) must be UEFI or you will only be able to boot using the method you currently are using.

You make a reference to boot repair but don't give any explanation.  Did you download it and run it?  If so, what you should run it again but select the option to Create BootInfo Summary which will give you a link when it finishes.  Also, if you are able to boot Ubuntu using the method you describe, download boot repair using the 2nd option descdibed on their site then post the link here and it will contain enough info for someone to suggest a possible solution.

Not sure which install option you chose.  It should be the Manual option, referred to as 'Something Else' in Ubuntu and NOT use the install alongside method.

You may have installed Ubuntu in Legacy/CSM mode while windows is UEFI.  That would explain why you have to boot the way you do.  Don't expect you will get much help with windows software here (EasyUEFI) but you might get lucky.

---

