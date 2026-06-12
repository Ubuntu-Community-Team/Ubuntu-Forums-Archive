---
title: "Ubuntu 13.04 does not boot on amd 64 bit Lenovo machine."
date: 2013-08-18
forum: New to Ubuntu
---

### Post by amityadav9314 on 2013-08-18
I have bought this laptop [http://www.flipkart.com/lenovo-essential-g505s-59-379862-laptop-apu-quad-core-a8-8gb-1tb-dos-2-5gb-graph/p/itmdm5ukxfqvwkqf?pid=COMDM5UGX9QFNWAM&otracker=ch_vn_laptop_main_Best%20priced%20Laptops%20in%20Great%20Configurations](http://www.flipkart.com/lenovo-essential-g505s-59-379862-laptop-apu-quad-core-a8-8gb-1tb-dos-2-5gb-graph/p/itmdm5ukxfqvwkqf?pid=COMDM5UGX9QFNWAM&otracker=ch_vn_laptop_main_Best%20priced%20Laptops%20in%20Great%20Configurations) and installed Ubuntu 13.04 on it. But the issue is that I can not boot. It just shows a simple and only plain purpule screen, that's it. 

I searched on internet and found this.. [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it).
My problem is in the first answer's first point. So I set nomodeset in the /etc/default/grub entry. But it did not help. And I don't see grub options on holding shift key while it boots so I could not use the recovery options or could not edit the grub on go by pressing 'e' and adding 'nomodeset'

I also installed amd catalyst driver by booting vai live cd and using chroot.

Any suggestion what to do

---

### Post by jeffroaltiere1 on 2013-08-18
It seems like your boot files are corrupted or partially missing. In this case, I'd try Boot Repair. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

 I too had the same issue once (the lingering purple screen), and I downloaded this and ran it. It will wipe and re-install the boot files for Ubuntu. This may be what your in need of.

---

### Post by amityadav9314 on 2013-08-19
No, I still can not fix it. I tried boot-repair. 
Here is my paste bin: [http://paste.ubuntu.com/6001782/](http://paste.ubuntu.com/6001782/)

---

### Post by oldfred on 2013-08-19
While shift should work some with UEFI have used escape to get grub menu.

You seem to have an UEFI system, but drive is MBR which will only boot in BIOS/CSM mode. You show a few left over Microsoft efi files in sda1, which is now shown as FreeDos. It may have been efi partition or was system purchased without an operating system and only had FreeDos?

Changing settings for grub config do not work without running sudo update-grub and you only can do that from inside your install. If you know how to chroot, you can chroot into your install and run update-grub which will add the changes to your menu.

---

