---
title: "Dual Boot Windows and Ubuntu issue"
date: 2019-04-05
forum: New to Ubuntu
---

### Post by grauweiss on 2019-04-05
Hi,

I tried dual booting Ubuntu and Windows 10 and then ran Boot Repair since booting up Windows didn't work.

Boot Repair didn't work either so I tried several approaches including rebuilding the BCD from windows but everytime I try that, I get the errror 0xc0000225 or that 0 windows installations were found.
In windows I could not find the BCD file, so here I am starting this new thread. Any help is welcome.

Boot Repair pastebin: [http://paste.ubuntu.com/p/nvvWt956RD/](http://paste.ubuntu.com/p/nvvWt956RD/)

---

### Post by oldfred on 2019-04-05
The BCD would be in the ESP - efi system partition.
But the first part of Boot-Repair has not been updated to include all the details inside the NVMe drive.

But grub only boots working Windows.
Can you directly boot Windows from UEFI boot menu, often f10 or f12, same key you used to boot flash drive installer?

---

### Post by yancek on 2019-04-05
Does booting Ubuntu ( the installed Ubuntu) work?  I ask because I don't see any grub.cfg file in your boot repair output.  It does show Ubuntu and windows detected.  Do you see a Grub boot menu?  Your output also shows entries for both Ubuntu and windows with the efibootmgr output.  Do you have Boot Options on boot which allow you to select booting from an EFI file?  The boot files for both windows/Ubuntu are present.

---

### Post by grauweiss on 2019-04-09
Yes, I can see grub and I can click on Windows but the system would not load the OS, because of the 0xc0000225 error.
I could not boot Windows from the UEFI boot menu and trying to repair the "startup" said 0 Windows installations were found. I tried to recreate the BSD but I did not succeed.

I had to reinstall Windows, but now they finally managed to get along ;)

Thank you for your replies!

---

