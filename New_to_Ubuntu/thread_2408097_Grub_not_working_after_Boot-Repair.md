---
title: "Grub not working after Boot-Repair"
date: 2018-12-13
forum: New to Ubuntu
---

### Post by twumm on 2018-12-13
I had grub perfectly working until I updated Ubuntu-18 when I got a prompt.
Now grub never shows up and I have tried all possible solutions I've come across online.

I generated [this from the last boot-repair]("http://paste.ubuntu.com/p/b3MMdShb9F").

Hopefully I can get some awesome feedback in resolving this.

Thanks

---

### Post by oldfred on 2018-12-13
If you go into your UEFI boot menu, you have multiple boot options. Have you tried all of them.
Sometimes with HP, the only option that works is the hard drive entry.  That uses /EFI/Boot/bootx64.efi. Boot-Repair backed up old copy which was a copy of Windows boot file & made it a copy of shimx64.efi to boot Ubuntu.

---

### Post by twumm on 2018-12-14
Thanks for the feedback.
To clarify further, by the boot menu, you mean from the bios, right? Or the boot menu I can get with efibootmgr?

---

### Post by oldfred on 2018-12-14
Yes, you only see short description in UEFI boot menu, but this shows details and you can see differences. 
boot-Repair report also shows this:
sudo efibootmgr -v

        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    Some vendors still call UEFI as BIOS, but since Windows 8 was released in 2012, vendors are required to use UEFI with gpt partitioning if Windows is pre-installed.

---

### Post by twumm on 2018-12-14
I chose F9 from this option - [https://drive.google.com/file/d/1ZLaKIply8jKUCNBiY1u857tHWCbPmqLN/view?usp=sharing](https://drive.google.com/file/d/1ZLaKIply8jKUCNBiY1u857tHWCbPmqLN/view?usp=sharing)
And then selected the second ubuntu option. It loaded perfectly. How can I automate this like it used to be, please? - [https://drive.google.com/file/d/1QBJxhWEn7ec9kF5Zqd_aYC62q92LYWi6/view?usp=sharing](https://drive.google.com/file/d/1QBJxhWEn7ec9kF5Zqd_aYC62q92LYWi6/view?usp=sharing)

---

### Post by oldfred on 2018-12-14
Some have to go into UEFI and set the correct choice as first in UEFI boot order.

Most can use efibootmgr to set boot order, but that was what grub used when it installed. so if that did keep Ubuntu entry or hard drive entry as first, then only choice is via UEFI. That screen is in UEFI settings on boot options, not the boot menu.

If efibootmgr works. This shows boot order and boot options:
       Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1
see also 
man efibootmgr

---

### Post by twumm on 2018-12-14
I went through the option of  setting the boot options with efibootmanager - [https://drive.google.com/file/d/1Z4YLQJ8kC1iVMr20GAcaL3EaSegrohKw/view?usp=sharing](https://drive.google.com/file/d/1Z4YLQJ8kC1iVMr20GAcaL3EaSegrohKw/view?usp=sharing)

And changed them to - [https://drive.google.com/file/d/1mQOTcYUFPBr3pGpeXBL-34BGOSSF3vi6/view?usp=sharing](https://drive.google.com/file/d/1mQOTcYUFPBr3pGpeXBL-34BGOSSF3vi6/view?usp=sharing)

However, it still boots straight to windows.

---

### Post by oldfred on 2018-12-14
Did you try settings in HP's UEFI?

Some with HP also said they had to update UEFI from HP for their system.

---

### Post by twumm on 2018-12-14
This is what I currently have in HP's UEFI, which should be fine, I think - [https://drive.google.com/file/d/1bTrkv0Boc0FRukc48u2pLGx2e1zazsxa/view?usp=sharing](https://drive.google.com/file/d/1bTrkv0Boc0FRukc48u2pLGx2e1zazsxa/view?usp=sharing) .
I will look at the possible option of updating the UEFI. I will keep you posted.
Thanks for the support.

---

### Post by twumm on 2018-12-16
I took re-inserted the RAM and everything seems fine now. Thanks a lot for your help.

---

