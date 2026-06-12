---
title: "Applying grub theme prevents boot"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by Danja91 on 2013-05-20
Hello,

Sorry for posting twice in one day; I'm having a separate issue that wouldn't be appropriate under my other thread. I am trying to apply a nice looking skin to grub, but doing so prevents me from booting properly. Before I lay out the problem, here is my hardware and installation info:

Hardware: Microsoft Surface Pro
Installation steps:
[COLOR=#333333]1: Disabled Secureboot in the BIOS[/COLOR]

[COLOR=#333333]2: Shrank the system partition on the SSD by 10 GB.[/COLOR]

[COLOR=#333333]3: Burned a bootable 64 bit Ubuntu 13.04 ISO onto a flash drive[/COLOR]

[COLOR=#333333]4: Rebooted into the flash drive, went through the initial Ubuntu configuration options.[/COLOR]

[COLOR=#333333]5: In the 10 GB empty space, added a 600 MB logical partition as swap.[/COLOR]

[COLOR=#333333]6: In the remaining 9.4 GB of empty space, added a primary ext4 partition mounted as /[/COLOR]

[COLOR=#333333]7: Installed the MBR to the SSD (dev/sda).[/COLOR]

[COLOR=#333333]8: Finished the installation

9: Rebooted into a bootable version of grub Boot Repair (64 bit), applied recommended settings (but made Windows my default OS selection)

10: Booted into Ubuntu


At this point everything worked and I was able to boot into both Windows 8 and Ubuntu, so I attempted to apply the theme from:
[/COLOR][https://github.com/webbrandon/Surface-Boot-Themes](https://github.com/webbrandon/Surface-Boot-Themes)

I believe I followed all steps faithfully (except for deleting one of the Windows 8 installations). However, after running sudo-update grub and rebooting, I have very strange results. If I select one of the two Windows installations, a purple square fills the screen and the computer hangs. If I select Ubuntu, I still get the purple square but 50% of the time it continues to boot Ubuntu after a few seconds; the remaining 50% of the time it also hangs.

Is there anything I could have done wrong that would cause this behavior? Does anyone have any recommendations to make the theme work? I really like the appearance, especially compared to the default grub.

As a side note, the installation steps I posted above skipped a step: I had bitlocker enabled and when I ran Boot Repair, it didn't recognize the installation. The subsequent grub configuration could not load into Windows. I reran boot repair, checked the "restore EFI" box in the advanced settings, restarted the computer, and booted into Windows 8 (there was no boot menu after restoring the EFI settings). After disabling bitlocker, Boot Repair was able to recognize my Windows installation and create a functional grub configuration. Two questions about this: 1 - is bitlocker support something that could perhaps be implemented in a future Boot Repair release? 2 - is it safe to reenable bitlocker now that I have a working boot configuration?

Thanks for your time.

---

### Post by tusharsingal on 2013-09-15
Same problem here. I don't use Bitlocker though - how do I go back to Windows? :confused:

---

