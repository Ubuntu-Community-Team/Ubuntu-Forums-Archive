---
title: "Intel 82810e graphics- stuck at 640x480"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by joshjani on 2008-05-07
I thought I was doing pretty good with Ubuntu using Feisty, but since I had few problems after initial setup, I've really forgotten how to do things!

I recently upgraded to 8.04, on the exact same machine and configuration that I had using Feisty, but now my screen resolution is stuck at 640x480 at 61hz That's not useful to me! 

I know I need to configure properly for the Intel onboard graphics, but I don't know/remember how. I tried searches here, but found people with problems much deeper than mine, using compiz and beryl and such. I don't need anything 3-D or super snazzy, just smooth performance at a finer resolution.

And please refresh my memory- is there something akin to the "My Computer" right-click in Windows, where I can get a snapshot of hardware in the PC? I wanted to check and see if Ubuntu knew what card I was using, that it said something about Intel driver, etc, and couldn't find it.

Thanks in advance for helping out a repeat noob.

JC

---

### Post by Bigtime_Scrub on 2008-05-07
YOu can go to System->Administration->Hardware Drivers/Hardware Testing

or if that isnt enough



Ubuntu comes with several command line tools which might help you detect more hardware than the Hardware Manager.

    *

      lshw lists all hardware.
    *

      lshw -short provides a short hardware summary.
    *

      Use cat /proc/cpuinfo for a crude, but quick way to display your processor information.
    *

      lspci lists connected PCI cards.
    *

      lsusb lists connected USB devices.
    *

      cat /proc/net/dev lists all the network interfaces. Alternatively, try lshw -class network.

---

### Post by joshjani on 2008-05-08
Thanks for that list- I'm starting a file to print with a bunch of commands I'll need.

Any tips on editing xorg conf to help me with intel i8210e graphics?

Anybody can chime in! Thanks

---

