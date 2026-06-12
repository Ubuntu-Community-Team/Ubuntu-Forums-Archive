---
title: "Ubuntu crashes after installation restart"
date: 2018-11-08
forum: New to Ubuntu
---

### Post by deano.linux on 2018-11-08
Hi, so I am new to Ubuntu. I recently installed it on my laptop and when I was told to restart, it restarted and crashed. I don’t know why it crashes whenever I restart my computer but I have the crash information.
[    0.000000] ACPI Error: [_UPC] Namespace lookup failure, AE_ALREADY_EXISTS (20170831/dswlosd-378)
[    0.000000] ACPI Exception: AE_ALREADY_EXISTS, (SSDT:  MIDERN) while loading table (20170831/tbxfload-228)
[    0.000000] ACPI Error: 1 table load failures, 9 successful (20170831/tbxfload-246)
[    0.927686] tpm_crb MSFT0101:00: [Firmware Bug] : ACPI region does not cover t
[    0.927730] tpm_crb MSFT0101:00: [Firmware Bug] : ACPI region does not cover t
[    1.010234] Couldn’t get size: 0x800000000000000e
[    1.010248] MODSIGN: Couldn’t get UEFI db list
[    1.010518] Couldn’t get size: 0x800000000000000e
/dev/sda6: recovering journal
/dev/sda6: clean, 177454/2564096, 1933782/10240000

---

### Post by TheFu on 2018-11-08
I searched with google using  "tpm_crb MSFT0101:00: [Firmware Bug]"  and found this: [https://ubuntuforums.org/showthread.php?t=2381494](https://ubuntuforums.org/showthread.php?t=2381494)  Post #8 seems to have a solution, assuming your machine has an nVidia GPU.

---

### Post by deano.linux on 2018-11-09
How do I do this? I see setparams  &#8216;System setup&#8217; and lower down it says fwsetup.
and that&#8217;s when I press e

---

### Post by TheFu on 2018-11-09
I have no idea where you are.  You have to see the grub screen (youtube will find what that looks like easily), move the highlight over the line using up/down arrows, press 'e', then follow the instructions.  This is all before any OS boots.

Then, to make the change permanent, after you get booted into Ubuntu, follow the 2nd half of the instructions.

The instructions seem correct from here, except don't forget to run **update-grub** as the very last step after everything else, then reboot.
The comments for the solution say that, but it isn't part of the list of steps, so it is easy to miss.

I'm not good at explaining these things to beginners. Sorry.   Hopefully someone else will try or you'll search youtube for *grub edit boot* and find enough there to explain.

---

### Post by deano.linux on 2018-11-09
Okay I will try that then

---

