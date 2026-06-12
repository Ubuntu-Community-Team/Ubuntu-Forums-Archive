---
title: "Dell XPS 13 9350 Graphics Issue"
date: 2016-02-05
forum: New to Ubuntu
---

### Post by mattlonis on 2016-02-05
Hello this is my first time using Ubuntu and utilizing the Ubuntu forums. I don't know any rules regarding how to operate here within the forums but I'll preface my issue with a quick story. I am a prospective computer science undergrade and am entering this field with little knowledge. I recently decided to try Ubuntu and installed 15.10, liked it so much i wiped my drive and made it my sole OS.  I experienced issues with my network driver for my laptop posted in the title so i upgraded to the xenial development build to utilize the 4.4 kernel. This went well and i had no issues.

I had one issue with my laptop not shitting down and sitting at an Ubuntu logo with the dots and tried a fix using gedit /etc/default/grub. Eventually i decided not to change the file because i probably would mess something up and low and behold when i force shut off my computer, i was sent to the grub bootloader (which i had never seen before). With a lot of frustration i eventually figured out i needed to boot into recovery mode and use failsafeX in order to see anything (because ubuntu would boot into a black screen otherwise).

Now that i am on my working Ubuntu it seems i have to always use failsafeX and when i run the command [COLOR=#111111][FONT=Consolas]lshw -c video[/FONT][/COLOR] i get:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: Sky Lake Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:db000000-dbffffff memory:90000000-9fffffff ioport:f000(size=64)

which leads me to believe i have no graphics driver installed which is weird to me because it worked before, and apparently Ubuntu comes with these drivers...

I tried to get the xorg-edgers ppa but this didn't work either. I'm kinda stuck.... :/

---

### Post by Geoffrey_Arndt on 2016-02-06
Xenial is still beta, and all the loose ends aren't tied up yet.    Maybe better to run 15.10 and sort the network issues out.   Remember, for a minor cost (from $10.00 to $25.00 usd), you can get several plug & play usb wireless adaptors.   Here is one brand I've had great success with, as they also target the Linux market and pretest the devices: (avail on Amazon, NewEgg, etc.).   I own the nano size 150 ultra dongle.

[URL="http://www.pandawireless.com/"]http://www.pandawireless.com/

[/URL]

---

### Post by svast on 2016-03-17
The onboard broadcom Wifi card is not supported by ubuntu 15.10, but you can buy a $20~ Intel 7265 wifi board for replacement.
It won't fail, and will not break the warranty.

I did it, and very pleased with that. I did the trick with the help of a youtube tutorial

---

