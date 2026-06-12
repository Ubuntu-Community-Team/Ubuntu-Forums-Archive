---
title: "Ubuntu won't ever start.."
date: 2015-10-25
forum: New to Ubuntu
---

### Post by Andrea_Rufini on 2015-10-25
[COLOR=#111111][FONT=Ubuntu]Hi guys, I downloaded and installed Ubuntu 14.04, disabling either Secure Boot and Fast Boot from my Bios. It worked fine until i rebooted the computer using Windows and than GRUB disappeared. I followed a guide and tried to solve the problem with a Boot Repair Live Disk, but I could only get a white screen when trying to start the OS. Now the Grub disappeared again. Could anyone please help me find a solution? [/FONT][/COLOR]

---

### Post by yancek on 2015-10-25
Run the boot repair Live Disk again and this time select the option to "Create BootInfo Summary" rather than trying to repair.  Post a link to the uploaded output here and someone should be able to advise you.

---

### Post by Geoffrey_Arndt on 2015-10-25
Andrea, it's also very helpful if in your answer, you include your computer specs:
>   cpu
>   ram
>   graphics system (nvidia xxx, ati xxx, intel integrated xxx . . )
>   storage system (1 drive, 2 drives, internal or external, ssd, etc.)
>   whether you also disabled Windows "Hibernation" - - - very important
>   if Laptop, what wireless system (broadcom, intel, atheros, realtek, marvel, etc.)
>   last but not least, what is the brand and model of the actual PC?   Some models of HP and Toshiba for example, are designed to only run windows (unless you hack the bootloader files via renaming schemes, etc.)

---

### Post by Mike_Walsh on 2015-10-25
TBH, if you created a Puppy Linux flash drive, booted with that, then ran the Grub4DOS config tool, you'd be sorted... :D


Regards,

Mike. ;)

---

