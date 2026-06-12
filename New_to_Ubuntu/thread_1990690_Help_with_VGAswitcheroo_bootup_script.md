---
title: "Help with VGAswitcheroo bootup script?"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by Aldo93 on 2012-05-29
I tried making a startup script that would disable my discrete graphics card upon bootup by following the instructions found here: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics) under the 'script for use during bootup' section, but it doesn't seem to have worked. I am sure I have done everything correctly and there were no error messages reported by the terminal. 

I have double checked that the file is executable, double checked my GRUB file and the added command line within it, and have definitely ran the 'update-grub' command before rebooting, yet when I reboot and do the 'cat /sys/kernel/debug/vgaswitcheroo/switch' command, it is showing that both graphics cards are still powered on.

Anyone have any idea what the problem could be, or if there's an easier way? I'm running 12.04 LTS if that makes any difference.

---

