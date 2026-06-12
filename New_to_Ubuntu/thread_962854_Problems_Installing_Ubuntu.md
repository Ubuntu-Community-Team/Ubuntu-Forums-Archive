---
title: "Problems Installing Ubuntu"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by willowford on 2008-10-29
Hello there,
I have recently bought a [transtec senyo 610]("http://www.transtec.co.uk/GB/E/products/personal_computer/pc/mini_pc.html?mod=prod&name=SY610TA65-A") and would like to use ubuntu. I downloaded the desktop version (ubuntu-8.04.1-desktop-amd64) and have tried to run the cd on the new blank machine. It gets to the welcome screen and I have tested the cd and the memory, but when I try to install ubuntu it thinks about it for a while and then just freezes.
Any suggestions?
Many thanks for any help.
Liam

---

### Post by Coreigh on 2008-10-29
On some of the older versions there was an option for "safe-mode" graphics or VGA mode. I have experienced installs where even though the graphics chipset is supported it did not work well during installation.

Is this an option you can try?

---

### Post by spiderbatdad on 2008-10-29
try some of the boot options, accessible by pressing F6 (more options), at the startup screen. Some versions offer a dialog with choice, other versions simply prompt the user with a boot line. In the latter case, delete the end of the line, where it says "quiet splash --" and replace with "noapic nolapic." There are other options as well...It may be a hard drive configuration issue...in which case, you can try "all_generic_ide." Sometime it is necessary to specify the graphics capabilities with "vga=791" (as an example) a search on vga would reveal more about what those numbers mean.

See here for more on this:[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Be sure to delete the quiet splash.

---

### Post by OldTimeTech on 2008-10-29
Suggestion would be to use the Alternative CD, it loads the same thing as what you downloaded but does it with a text setup instead of a gui...seems to work better with the intel graphics.

---

### Post by willowford on 2008-10-29
I've put it in safe mode and it seems to be working...
Many thanks for your prompt response.
Liam

---

