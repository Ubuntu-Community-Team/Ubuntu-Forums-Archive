---
title: "question about grub and EFI?"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by santiagorf on 2013-06-28
Hi all,
Today I first installed Ubuntu 12.4 in the first partition of my computer and then Scientific Linux in the second one. After installing SL, I rebooted the computer, to go back to Ubuntu, but the only OS available on the GRUB was SL.
SL uses GRUB 0.96, so I thought that since Ubuntu uses GRUB2, reinstalling Ubuntu in the first partition will solve the issue, and let me boot both OS. However, after reinstalling Ubuntu in the first partition, I continued having SL as the only available OS.
Finally, using Boot-Repair I was able to reinstall GRUB in a way I can boot up from either Ubuntu or SL. I remember that in the installation process Boot-Repair mentioned something about EFI (honestly just used the recommended repair without really knowing what was going on).

I remember having similar problems in the past that were solved by reinstalling Ubuntu, which recovered all the lost OS. But, today in this new computer things were different. Is this related to EFI, or there is something am I missing?

Any help to clarify my confusion is much appreciated

---

### Post by Kopkins on 2013-06-28
It's likely that SL didn't use OS_Prober to detect other OSes. Ubuntu DOES do this by default, but maybe when you installed it, it didn't overwrite the SL Grub correctly. If you had chrooted into your Ubuntu system you could have done grub-install /dev/sdX (for your disk) and everything probably would have been fine. 

I don't think it is a problem with EFI. Perhaps it interfered with Ubuntu replacing SL's grub, but so far EFI has only provided me with more booting options. 

Kopkins

---

### Post by oldfred on 2013-06-28
If you have new hardware it will have both UEFI and BIOS. Ubuntu will boot in either mode, but drive needs to be gpt partitioned to use efi. Drive will be MBR(msdos) partitioned to boot with BIOS mode.

If your SL uses grub 0.96 (not 1.96?) that is grub legacy. Grub legacy only had a limited way to find other installs and we usually had to add them manually. Better to use grub2 from Ubuntu to boot. You may have to chain load to SL's grub to have all the correct boot parameters. 

You can post the link to the BootInfo report that Boot-Repair creates.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by android4682 on 2013-06-28
> **santiagorf said:**
> Hi all,
Today I first installed Ubuntu 12.4 in the first partition of my computer and then Scientific Linux in the second one. After installing SL, I rebooted the computer, to go back to Ubuntu, but the only OS available on the GRUB was SL.
SL uses GRUB 0.96, so I thought that since Ubuntu uses GRUB2, reinstalling Ubuntu in the first partition will solve the issue, and let me boot both OS. However, after reinstalling Ubuntu in the first partition, I continued having SL as the only available OS.
Finally, using Boot-Repair I was able to reinstall GRUB in a way I can boot up from either Ubuntu or SL. I remember that in the installation process Boot-Repair mentioned something about EFI (honestly just used the recommended repair without really knowing what was going on).

I remember having similar problems in the past that were solved by reinstalling Ubuntu, which recovered all the lost OS. But, today in this new computer things were different. Is this related to EFI, or there is something am I missing?

Any help to clarify my confusion is much appreciated

I had the same problem as you.
I posted my question on this forum and the answer was to install boot-repair and do a automatic fix.
That fixed my problem.

If I had the choose between a UEFI laptop or a Legacy. I defiantly choose a Legacy.

---

