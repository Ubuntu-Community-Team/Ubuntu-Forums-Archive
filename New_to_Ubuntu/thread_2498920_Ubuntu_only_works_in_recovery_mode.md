---
title: "Ubuntu only works in recovery mode"
date: 2024-07-03
forum: New to Ubuntu
---

### Post by sebbarros on 2024-07-03
Hi,
My first post here, sorry for any mistake. I am using Ubuntu 20.04 on a Dell Vostro 3405 AMD Ryzen 5 3450u with Radeon Vega Mobile gfx x 8. I tried to USB boot from a SD card with a different distro (it did not work) and now Ubuntu only boots in recovery mode. In the starting (GRUB?) screen if I choose "Ubuntu" I get a black screen. If I go into "Advanced options", recovery mode and then "resume", everything works fine. I tried the options in the recovery menu, but it did not solve the problem. Any help appreciated. Thanks a lot.

---

### Post by grahammechanical on 2024-07-03
This is something you may not know. When we select Advanced Options>Recovery mode>Resume the Ubuntu desktop will load with a open source video driver.

It may be that you originally installed 20.04 to use a proprietary video driver. And so when Ubuntu loads it looks for a proprietary driver and does not find one.

My advice would to use Resume and open Software & Updates>Additional Drivers tab. If you are connected to the internet the utility will find a proprietary video driver. The option may already be ticked. If you untick it and then reboot Ubuntu will load with the open source video driver without the need to use Advance Options.

To connect to the internet when using Recovery mode, first select Network at the recovery menu and when the check is finished select Resume.

Regards

P.S. Welcome to Ubuntu forums.

---

### Post by sebbarros on 2024-07-03
Thanks a lot for your welcoming reply!! I can't find a video driver in the Additional Drivers tab. 
I can see (I do not send a screen capture because it is in Spanish)
1. Realtek Semiconductor Wireless adapter (ticked in  the option "do not use device"), 
2. "Unknown" (tick in "Using Customize puleaudio default sample rate for Cirrus codec...")
3. "Advanced Micro Devices SMBus Controller, (tick in "Using hardware support for Dell Vostro 3504 from oem-somerville-beric-amd-meta (open code/source?)"
4. "Unkown" (underneath it says "This device is using an alternative controller", tick in "Using hardware support for Somerville plataform from oem-somerville-meta (open code/source?)".
Thanks again!!

---

