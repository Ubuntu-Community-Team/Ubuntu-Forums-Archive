---
title: "Can't boot LiveUSB: low graphics mode"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by ronb2552 on 2014-01-27
[FONT=arial][COLOR=#333333]I am trying to install Ubuntu 13.10 alongside Windows 8.1 that was installed with MBR. Created a bootable usb with UNetbootin but when I try to load ubuntu from usb I am stuck at "low graphics mode".
[/COLOR]
[COLOR=#333333]My system:[/COLOR]
Gigabye z87-ud3h
i5 4570
AMD radeon 7790[/FONT]

---

### Post by Bucky Ball on 2014-01-27
Welcome. Do you get to a screen with the options 'Try Ubuntu' 'Install Ubuntu' before this screen? If so, hit F6 and try some of the options there then attempt 'Try Ubuntu'.

---

### Post by ronb2552 on 2014-01-27
> **Bucky Ball said:**
> Welcome. Do you get to a screen with the options 'Try Ubuntu' 'Install Ubuntu' before this screen?
Yes I do. I selected 'try Ubuntu'.

---

### Post by Bucky Ball on 2014-01-27
Hit F6 and try some of the options there then attempt 'Try Ubuntu'. 'nomodeset' works for nvidia cards but not sure about AMD.

---

### Post by ronb2552 on 2014-01-27
> **Bucky Ball said:**
> Hit F6 and try some of the options there then attempt 'Try Ubuntu'. 'nomodeset' works for nvidia cards but not sure about AMD.
I think I am not getting the screen you are talking about. I get a black GRUB screen with option "Try ubuntu...", "Install ubuntu"... F6 doesn't do anything.

---

### Post by Bucky Ball on 2014-01-27
Ah. Your drive is set to boot EFI? Could you boot into the BIOS and give it a check? Easier still, when you get to that screen, does it say 'grub-efi' at the top?

---

### Post by ronb2552 on 2014-01-27
> **Bucky Ball said:**
> Ah. Your drive is set to boot EFI? Could you boot into the BIOS and give it a check? Easier still, when you get to that screen, does it say 'grub-efi' at the top?
It didn't say 'grub-efi'. It was something like 'gnu grub 2'. However, I did have 'UEFI and legacy' in bios which I changed to 'Legacy only'. Now instead of grub it boots into some sort of UNetbootin boot with similar options. Selecting 'Try Ubuntu' results in the same 'low graphics mode'.
Thanks for your help.

---

### Post by Bucky Ball on 2014-01-27
If you are booting Windows 8 you MUST leave EFI on, so if you have it off, switch back on, that is not the issue or Win8 will fail to boot. Have you got fastboot and secureboot off in the BIOS?

---

### Post by ronb2552 on 2014-01-27
> **Bucky Ball said:**
> If you are booting Windows 8 you MUST leave EFI on, so if you have it off, switch back on, that is not the issue or Win8 will fail to boot. Have you got fastboot and secureboot off in the BIOS?
Windows 8 boots fine even after setting the boot to 'Legacy only'. As far as I understand my win8 is installed in legacy format( MBR partition table) so that all the UEFI features do not work. However, I did turn off everything I could find that relates to uefi (including fastboot and secureboot) just in case.

---

### Post by Bucky Ball on 2014-01-27
Rules out anything to do with EFi then. When you boot into low-graphics mode is everything working okay, just a stretched screen? If so, when you install you should be able to install drivers for the AMD radeon 7790 fairly easily. They just don't exist on the disk perhaps. This is sometimes the case with proprietary or very new hardware. You need to agree to install the specific driver as part of the third-parties ToS. 

There appears to be a driver for it here which you could try installing when you've installed to hard disk:

[http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64](http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64)

---

### Post by ronb2552 on 2014-01-27
> **Bucky Ball said:**
> Rules out anything to do with EFi then. When you boot into low-graphics mode is everything working okay, just a stretched screen? If so, when you install you should be able to install drivers for the AMD radeon 7790 fairly easily. They just don't exist on the disk perhaps. This is sometimes the case with proprietary or very new hardware. You need to agree to install the specific driver as part of the third-parties ToS. 

There appears to be a driver for it here which you could try installing when you've installed to hard disk:

[http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64](http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64)

Thanks again.
It doesnt actually boot into low-graphics mode. I just get a black screen.

Edit1: I also tried disabling my AMD Radeon 7790 card and using the on-board Intel one but it makes no difference.

Edit2: I tried using a LiveCD instead of usb. I managed to get to the advanced install screen and select 'nomodeset'. This gets me to a black screen(no message about "low graphic mode"). Otherwise, I get the same thing as before.

---

### Post by ronb2552 on 2014-01-28
Is there anything else I can try? 
I found an old Ubuntu 10.10 32Bit CD I had lying around and surprisingly it worked! I managed to boot to LiveCD from the first try.
Surely we can make it work with the newer version?

Can anyone help?
Thanks

---

### Post by butters stotch on 2014-01-28
> **ronb2552 said:**
> Is there anything else I can try? 
I found an old Ubuntu 10.10 32Bit CD I had lying around and surprisingly it worked! I managed to boot to LiveCD from the first try.
Surely we can make it work with the newer version?

Can anyone help?
Thanks

Maybe you have tried that, but I have to ask: Did you try to select "Install Ubuntu" in the grub menu?
I just got a new laptop with AMD APU and graphic card. I have the same issue as you do. I tried the "Install Ubuntu" instead of booting live session and it worked (13.10 64bit).
Of course with UEFI on and secure boot off.

---

