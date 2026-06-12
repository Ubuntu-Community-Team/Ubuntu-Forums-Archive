---
title: "Ubuntu screwed something..."
date: 2014-04-23
forum: New to Ubuntu
---

### Post by protoss96 on 2014-04-23
Hi,

I was using Ubuntu 12.04 LTS about two weeks ago, and then when 14.04 showed up i upgraded immediately. Now i found out that Ubuntu 14.04 is not avaible for EFI PCs and then i just go to update manager and upgraded operating system. After the installation when PC needs to show motherboard logo (in my case ACER) the whole screen gets ubuntu theme and the corners of screen have smooth ping-orange color.

Here is the picture, i really don't know what kind of problem is this, but i personally believe that this UEFI software on EFI PC trigered some conflicts. Now booted Fedora 20 LXDE to test screen again and the problem is still there...

- Thank you so much for every helpful reply. Cheers!

---

### Post by suprleg on 2014-04-23
Not using EFI or UEFI on this old clunker, but have you entered your firmware setup utility and looked around for a solution?

---

### Post by ajgreeny on 2014-04-23
14.04 works on EFI / UEFI without a problem; you just need to make sure that you have the correct version and have booted the install medium in the manner in which you want to install the OS.  If you upgraded online this should all have been taken care of in the upgrade.

How did you manage this updating; as a clean install over the previous version, or as an online upgrade?
Are you using a 64 bit OS?
If a clean install, did you boot the DVD/USB in UEFI or legacy BIOS/CSM mode?

See [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for all UEFI information.

---

### Post by protoss96 on 2014-04-23
I installed Ubuntu 12.04 with DVD and then i upgraded to 14.04 via Update Manager so i can say i used online upgrade without any medium, and i am on 64-bit.

---

### Post by ajgreeny on 2014-04-23
I haven't a clue what is going on here so can you boot to a live system and try installing and using boot-repair.
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

---

### Post by suprleg on 2014-04-23
> **ajgreeny said:**
> 

See [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for all UEFI information.

Thanks for this. :popcorn:

---

