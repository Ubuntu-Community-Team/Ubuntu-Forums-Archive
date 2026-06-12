---
title: "[SOLVED] Resolution problem upon login"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Farmer of Bricks on 2008-10-29
I'm running Kubuntu 8.04 with KDE3.5 and KDE4 on an AMD Athlon x64, 1.25 gigs of ram, and an Nvidia GeForce4 MX 4000, running the proprietary driver. I've stopped using KDE3.

When I turn the computer on, it shows a screen with the energy-star logo and a ticker that tests the memory, along with a lot of other data. I usually skip the memtest with the [esc] key. The computer then checks for a boot floppy and a boot CD, and, finding neither, proceeds to run GRUB.  A small prompt shows beneath all the scrolled text asaying, 'Press ESC to enter the GRUB menu,' followed by a number that counts down from 5, and then GRUB loads the kernel. 
A little message appears to tell me that the kernel is loaded, and then more text flashes upon the screen. The screen switches from the 1204x768 that the above stuff has been displayed in to 1440x900, which is the highest resolution that my acer AL1916W can display. That's a good thing. The login screen appears, in the correct resolution. I type in my password and hit [enter].

The moment I hit [enter], the screen drops back into 1024x768, and stays that way while KDE4 loads. It will stay that way until I open System Settings and click on Display.

The moment I hit Display, the screen instantly pops back into 1440x900, and it stays that way until I log out.

Please help. It's not urgent, but it is rather annoying. I'd rather not mess with text files, but I will if necessary and well-explained. 

Thank you.

---

### Post by Farmer of Bricks on 2008-11-05
In other news, I've figured out how to get a program to auto-run upon KDE4 start (Create a link to the application in $/.kde4/Autostart/). 

It logically follows taht I could put in a link to System Settings, thereby obviating the necessity to open System Settings manually, *BUT*

Could I put an option on the end of the systemsettings command to get it to open the "Display" section automatically?

---

### Post by Farmer of Bricks on 2008-11-21
This problem was solved today when I logged into KDE 3.5 on my Hardy Machine. The KDE 3.5 desktop loaded, in glorious 1024 x 768, so I opened System Settings and went to Display. Nothing happened, so I changed the resolution to 1440 x 900, and exited. I restarted the computer, and when I logged into KDE 4.1, it loaded in 1440 x 900. 

Why does KDE 4.1 depend upon KDE 3.5 resolution config files? 
Would this be fixed by upgrading to Intrepid?

---

